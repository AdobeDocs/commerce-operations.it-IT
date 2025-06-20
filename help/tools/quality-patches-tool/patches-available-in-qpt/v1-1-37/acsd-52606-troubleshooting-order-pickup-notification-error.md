---
title: 'ACSD-52606: messaggio di errore visualizzato quando l’utente fa clic su "Notify Order is Ready for Pickup" (Notifica ordine pronto per il prelievo)'
description: Applica la patch ACSD-52606 per risolvere il problema di Adobe Commerce che causa la visualizzazione di un messaggio di errore quando l'utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52606: messaggio di errore visualizzato quando l’utente fa clic su &quot;Notify Order is Ready for Pickup&quot; (Notifica ordine pronto per il prelievo)

La patch di ACSD-52606 risolve il problema relativo alla visualizzazione di un messaggio di errore *L&#39;ordine non è pronto per il ritiro* quando l&#39;utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-52606. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene visualizzato un messaggio di errore *L&#39;ordine non è pronto per il ritiro* quando l&#39;utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Prerequisiti</u>:

I moduli di inventario sono installati.

<u>Passaggi da riprodurre</u>:

1. Installa nuova istanza.
1. Create una nuova origine e un nuovo materiale.
1. Assegna la nuova origine al sito Web predefinito.
1. Abilitare la posizione di prelievo per l&#39;origine appena creata.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** e abilita **[!UICONTROL In-Store Delivery]**.
1. Crea un prodotto semplice *In Stock* con *QTY=0* per tutte le scorte e *[!UICONTROL Manage Stock = No]* e assegnalo a entrambe le origini.
1. Creare un ordine dal front-end con il prodotto creato nel passaggio precedente, scegliendo *[!UICONTROL In-Store Pickup]* come metodo di consegna.
1. In Amministratore, vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Fare clic su **[!UICONTROL Notify order is ready for pickup]**.

<u>Risultati previsti</u>:

La notifica viene inviata senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *L&#39;ordine non è pronto per il ritiro*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
