---
title: '''MDVA-42806: Nuovo''e-mail di registrazione della società viene inviata ogni volta che viene aggiornata la società esistente'''
description: La patch MDVA-42806 risolve il problema per cui viene inviata una nuova e-mail aziendale registrazione ogni volta che una società esistente viene aggiornata tramite API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. L'ID della patch è MDVA-42806. Si prega di notare che il problema è pianificato per essere risolto in Adobe Systems Commerce 2.4.5.
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42806: Nuovo e-mail di registrazione aziendale viene inviata ogni volta che viene aggiornata una società esistente

La patch MDVA-42806 risolve il problema per cui viene inviata una nuova e-mail aziendale registrazione ogni volta che una società esistente viene aggiornata tramite API REST. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. L&#39;ID della patch è MDVA-42806. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni Adobe Systems Commerce:**

* Adobe Systems Commerce (tutti i metodi di distribuzione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove versioni di Quality Patches Tool. Per verificare se la patch è compatibile con la versione di Adobe Systems Commerce in uso, aggiornare il `magento/quality-patches` pacchetto alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]pagina](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) : Search for patches. Utilizzare l&#39;ID patch come parola chiave di ricerca per individuare la patch.

## Questione

Viene inviato un messaggio e-mail per una nuova società registrazione ogni volta che una società esistente viene aggiornata tramite l&#39;API REST.

<u>Prerequisiti</u>:

Moduli B2B installati.

<u>Passaggi da riprodurre</u>:

1. Crea un account aziendale.
1. Utilizza l&#39;endpoint `/V1&#x200B;/company&#x200B;/<company_id>`. Per aggiornare la società creata, consulta [Aggiorna l&#39;azienda](https://developer.adobe.com/commerce/webapi/rest/b2b/company-object/#update-the-company) nella nostra documentazione per gli sviluppatori. Di seguito è riportato un esempio di payload:

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Risultati attesi</u>:

Non viene inviata alcuna e-mail che dica &quot;Nuovo azienda registrazione richiesta&quot; poiché l&#39;API sta aggiornando una società esistente.

<u>Risultati effettivi</u>:

Viene inviata un&#39;e-mail con il messaggio &quot;Nuovo società registrazione richiesta&quot; ogni volta che viene inviato il richiesta API.

## Applica la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato Quality Patches Tool: una nuova strumento per le patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) di qualità self-service nel knowledge base di supporto.
* [Controlla se la patch è disponibile per il tuo problema di Adobe Systems Commerce utilizzando Quality [!DNL Quality Patches Tool] Patches Tool](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida.

Per informazioni su altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Search per le](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) patch nella [!DNL Quality Patches Tool] guida.
