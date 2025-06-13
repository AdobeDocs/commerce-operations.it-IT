---
title: 'ACSD-54887: il carrello acquisti del cliente viene cancellato dopo la scadenza della sessione del cliente'
description: Applica la patch ACSD-54887 per risolvere il problema di Adobe Commerce per cui il carrello acquisti cliente viene cancellato dopo la scadenza della sessione cliente con [!UICONTROL Persistent Shopping Cart] abilitato.
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-54887: il carrello acquisti del cliente viene cancellato dopo la scadenza della sessione del cliente

La patch ACSD-54887 risolve il problema che causa l&#39;eliminazione del carrello del cliente dopo la scadenza della sessione del cliente con [!UICONTROL Persistent Shopping Cart] abilitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. L’ID della patch è ACSD-54887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7 e 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il carrello acquisti cliente viene cancellato dopo la scadenza della sessione del cliente con [!UICONTROL Persistent Shopping Cart] abilitato.

<u>Passaggi da riprodurre</u>:

1. Abilita [!UICONTROL Persistent Shopping Cart]. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *Sì*.

   Accedi con persistenza abilitata (Nota: non è disponibile nell&#39;autorizzazione popup, ma solo nella pagina [!UICONTROL Sign in] diretta).

1. Aggiungi un prodotto al carrello.
1. Procedi al pagamento e seleziona un metodo di pagamento.
1. Scadenza della sessione (eliminare `PHPSESSID`).
1. Aggiorna la pagina. Si noti che il preventivo viene immediatamente convertito in preventivo ospite perché è già selezionato un metodo di pagamento e il cookie [!UICONTROL Persistent Cart] viene rimosso.
1. Scadenza della sessione (eliminare `PHPSESSID`).
1. Aggiorna la pagina. Vedi che il carrello è vuoto.
1. Accedi di nuovo.

<u>Risultati previsti</u>:

Il carrello contiene il prodotto quando accedi di nuovo.

<u>Risultati effettivi</u>:

Il carrello è vuoto al nuovo accesso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
