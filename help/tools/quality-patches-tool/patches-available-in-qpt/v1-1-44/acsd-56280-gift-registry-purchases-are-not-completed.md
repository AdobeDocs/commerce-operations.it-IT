---
title: 'ACSD-56280: gli acquisti del registro dei regali non sono completati'
description: Applicare la patch ACSD-56280 per risolvere il problema Adobe Commerce in cui gli acquisti del registro regali non sono completati
feature: Checkout
role: Admin
exl-id: a79f789f-999f-4d11-b7ee-2c065b681efb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-56280: gli acquisti del registro dei regali non sono completati

>[!NOTE]
>
>Questa patch è sostituita da [ACSD-63283](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-58/acsd-63283-resolving-gift-registry-email-and-order-placement-issues-in-adobe-commerce.md).

La patch ACSD-56280 risolve il problema che causa il mancato completamento degli acquisti del registro dei regali. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44. L’ID della patch è ACSD-56280. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli acquisti del registro regali non sono stati completati.

<u>Passaggi da riprodurre</u>:

1. Accedere come cliente e aggiungere un **[!UICONTROL product]** al registro regali.
1. Condividere il collegamento del registro regali.
1. Aprire il collegamento del registro regali in un altro browser o finestra in incognito.
1. Aggiungi la quantità e aggiungi gli articoli al carrello.
1. Vai a **[!UICONTROL Checkout Page]**, seleziona **[!UICONTROL shipping method]** (poiché l&#39;indirizzo di spedizione è già selezionato, fornito dal registrante).
1. Selezionare il metodo di pagamento.
1. Fai clic sul pulsante Inserisci ordine.

<u>Risultati previsti</u>:

L’ordine deve essere effettuato.

<u>Risultati effettivi</u>:

L&#39;ordine non è stato effettuato e l&#39;errore visualizzato è `Call to a member function getUpdatedQty() on null`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
