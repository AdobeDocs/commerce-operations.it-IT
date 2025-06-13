---
title: 'ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] non popolati quando [!UICONTROL asynchronous indexing] è abilitato'
description: Applicare la patch ACSD-46865 per risolvere il problema di Adobe Commerce per cui le griglie [!UICONTROL shipment] e [!UICONTROL credit memo] non vengono compilate quando [!UICONTROL asynchronous indexing] è abilitato.
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 6f84f5b6-6c34-476c-aae5-9a8ba306f8e4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] non popolati quando [!UICONTROL asynchronous indexing] è abilitato

La patch ACSD-46865 risolve il problema per cui le griglie [!UICONTROL shipment] e [!UICONTROL credit memo] non vengono compilate quando [!UICONTROL asynchronous indexing] è abilitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-46865. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Shipment] e [!UICONTROL credit memo] griglie non vengono compilate quando [!UICONTROL asynchronous indexing] è abilitato.

<u>Passaggi da riprodurre</u>:

1. Nell&#39;amministratore [!DNL Commerce], vai a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SÌ*.
2. Vai di nuovo a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Pulizia cache di configurazione.
4. Effettuare un nuovo ordine per un prodotto semplice.
5. Esegui cron.
6. Aprire l&#39;ordine nell&#39;amministratore [!UICONTROL Commerce] scegliendo **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e generare una fattura e una nota di credito.
7. Sposta l&#39;ordine in [!UICONTROL Archive].
8. Crea un altro ordine per un prodotto semplice.
9. Esegui cron.
10. Passare al nuovo ordine e generare una nuova spedizione, una fattura e una nota di accredito.
11. Esegui cron.
12. Controllare le griglie [!UICONTROL shipments], [!UICONTROL invoices] e [!UICONTROL credit memo] nell&#39;amministratore.

<u>Risultati previsti</u>:

Sono visualizzati i nuovi [!UICONTROL shipment], [!UICONTROL invoice] e [!UICONTROL credit memo].

<u>Risultati effettivi</u>:

I nuovi [!UICONTROL shipment], [!UICONTROL invoice] e [!UICONTROL credit memo] non sono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
