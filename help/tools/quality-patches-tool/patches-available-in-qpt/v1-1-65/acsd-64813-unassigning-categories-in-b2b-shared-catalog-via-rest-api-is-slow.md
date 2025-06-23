---
title: 'ACSD-64813: la rimozione dell''assegnazione delle categorie nel catalogo condiviso  [!DNL B2B]  tramite REST API è lenta'
description: Applica la patch ACSD-64813 per risolvere il problema di Adobe Commerce, a causa del quale la rimozione dell'assegnazione di categorie in un catalogo condiviso  [!DNL B2B]  tramite l'API REST è lenta.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0ed4bde6d78429da5a375a8c50f6b348db5a5ad5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-64813: la rimozione dell&#39;assegnazione delle categorie nel catalogo condiviso [!DNL B2B] tramite API REST è lenta

La patch ACSD-64813 risolve il problema relativo al rallentamento della rimozione delle categorie da un catalogo condiviso [!DNL B2B] tramite l&#39;API REST. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-64813. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La rimozione dell&#39;assegnazione di categorie in un catalogo condiviso [!DNL B2B] tramite l&#39;API REST è lenta.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL B2B]**, **[!UICONTROL Company]** e **[!UICONTROL Shared Catalog]**.
1. Genera 30.000 prodotti attivi in magazzino.
1. Crea un [catalogo condiviso personalizzato](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) e assegna a esso tutti i prodotti.
1. Crea una nuova categoria nella categoria principale predefinita e assegna ad essa alcuni prodotti.
1. Utilizzare il token di amministrazione per chiamare l&#39;endpoint REST API `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` con il nuovo ID categoria.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

1. Conferma che la risposta sia *true*.
1. Eseguire `bin/magento cron:run` due volte o eseguire una reindicizzazione.
1. Utilizzare il token di amministrazione per chiamare l&#39;endpoint REST API `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` con il nuovo ID categoria.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

<u>Risultati previsti</u>:

L’operazione deve essere completata in un tempo ragionevole (meno di un paio di minuti).

<u>Risultati effettivi</u>:

L’esecuzione richiede circa 30 minuti o restituisce un errore di timeout.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
