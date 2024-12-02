---
title: 'ACSD-59786: GraphQL restituisce un errore durante il recupero di un "quote_id" per un preventivo scaduto'
description: Applica la patch ACSD-59786 per risolvere il problema Adobe Commerce, se una query GraphQL restituisce un errore durante il recupero di un "quote_id" per una virgoletta scaduta.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: GraphQL restituisce un errore durante il recupero di un `quote_id` per un preventivo scaduto

La patch ACSD-59786 risolve il problema che causa una query GraphQL che restituisce un errore durante il recupero di un `quote_id` per un preventivo scaduto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51. L’ID della patch è ACSD-59786. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una query GraphQL restituisce un errore durante il recupero di un `quote_id` per un preventivo scaduto.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Companies]** e **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** e **[!UICONTROL Enable Company]** impostato su *Sì*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** e imposta **[!UICONTROL Enable Purchase Orders]** su *Sì*.
1. Crea una nuova società e imposta **[!UICONTROL Enable Purchase Orders]** su *Sì* per lo stesso.
1. Crea un prodotto semplice e assegnalo a una categoria.
1. Accedere a Storefront utilizzando l&#39;account amministratore della società e creare un nuovo ordine utilizzando **[!UICONTROL Purchase Order]** come metodo di pagamento.
1. Cambia **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Eseguire il comando `bin/magento c:f`.
1. Passare al database `quote_table` e modificare i valori `created_at` e `updated_at` con un giorno nel passato.
1. Eseguire il comando `bin/magento cron:run --group="sales_clean_quotes`.
1. Eseguire la richiesta GraphQL specificata di seguito utilizzando un token autorizzato per l&#39;amministratore che crea **[!UICONTROL Purchase Order]**:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Risultati previsti</u>:

La query GraphQL restituisce `quote_id`.

<u>Risultati effettivi</u>:

La query GraphQL restituisce un errore interno del server.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
