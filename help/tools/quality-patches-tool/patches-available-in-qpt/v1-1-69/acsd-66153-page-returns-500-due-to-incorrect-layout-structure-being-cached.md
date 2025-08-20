---
title: 'ACSD-66153: La pagina restituisce un errore 500 a causa di una struttura di layout non corretta nella cache'
description: Applica la patch ACSD-66153 per risolvere il problema Adobe Commerce, se una pagina restituisce un codice di errore 500 a causa di una struttura di layout non corretta nella cache.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153: La pagina restituisce un errore 500 a causa di una struttura di layout non corretta nella cache

La patch ACSD-66153 risolve il problema relativo al codice di errore 500 restituito da una pagina a causa di una struttura di layout errata memorizzata nella cache. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-66153. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p10

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una pagina restituisce un errore 500 a causa di una struttura di layout non corretta nella cache.

<u>Passaggi da riprodurre</u>:

1. Installa `2.4-develop`.
1. Creare e installare un modulo personalizzato:
1.1 Aggiungere un blocco personalizzato al layout `catalog_category_view`.
1.1 Inserisce `Magento\Framework\View\Result\Layout` nel blocco personalizzato tramite il relativo costruttore.
1. Creare la categoria **[!UICONTROL shop]**.
1. Apri **[!UICONTROL two terminal windows]**:
   1. **Terminale 1**: pulizia continua della cache di layout:

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminale 2**: simula richieste simultanee alla pagina della categoria:

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Alcune richieste non riescono in modo casuale con un codice di stato 500 e `var/log/support_report.log` mostra il seguente errore:

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>Risultati previsti</u>:

Tutte le richieste restituiscono 200 OK.

<u>Risultati effettivi</u>:

Alcune richieste restituiscono in modo intermittente l’errore 500 del server interno.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
