---
title: 'ACSD-65848: le categorie in admin si caricano molto lentamente'
description: Applica la patch ACSD-65848 per risolvere il problema di Adobe Commerce, in cui il conteggio totale dei prodotti in una categoria è stato calcolato utilizzando una sottoselezione, che ha ritardato il tempo di caricamento della categoria.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848: le categorie in admin si caricano molto lentamente

La patch ACSD-65848 risolve il problema relativo al calcolo del conteggio totale dei prodotti in una categoria mediante una sottoselezione, che ritarda il tempo di caricamento della categoria. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACSD-65848. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La pagina di visualizzazione/modifica della categoria Amministratore presenta ritardi significativi durante il caricamento. Il ritardo è causato dal metodo utilizzato per calcolare il conteggio totale dei prodotti in una categoria, basato su una query di selezione secondaria. Il refactoring di questa logica per l&#39;utilizzo di un join migliora le prestazioni e riduce il tempo di caricamento.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova istanza di Adobe Commerce Cloud utilizzando la versione 2.4.8.
1. Crea 2.500 categorie e almeno 10.000 prodotti:
   1. Copiare la directory `setup/performance-toolkit` in `./var` per poter modificare i profili.
   1. Aprire il profilo `small.xml` e aggiornarlo in modo da includere 2.500 categorie e 250.000 prodotti (in base alla configurazione del commerciante).
   1. Esegui il comando seguente per generare gli staffaggi:

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. Dopo aver creato i prodotti e le categorie, accertati che tutte le categorie siano impostate come ancoraggi. Esegui questa query SQL:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. Nel pannello Amministratore, crea una struttura di categorie più profonda:
   * Spostare la categoria 2 nella categoria 1 per annidarla più in profondità nell&#39;albero.
1. Prova ad aprire una pagina di categoria nel pannello di amministrazione utilizzando un URL come:
   ```/admin/catalog/category/edit/id/xx/```

<u>Risultati previsti</u>:

Ogni pagina della categoria si apre al primo tentativo entro pochi secondi.

<u>Risultati effettivi</u>:

L&#39;apertura delle pagine delle categorie richiede più di un minuto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
