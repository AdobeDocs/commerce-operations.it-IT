---
title: 'ACSD-51819: inserimento di più ordini con un ID preventivo singolo'
description: Applica la patch ACSD-51819 per risolvere il problema di Adobe Commerce, in cui è possibile effettuare più ordini con lo stesso ID preventivo.
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51819: inserimento di più ordini con un ID preventivo singolo

La patch ACSD-51819 risolve il problema che consente di inoltrare più ordini con lo stesso ID preventivo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41. L’ID della patch è ACSD-51819. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È possibile inserire più ordini con lo stesso ID preventivo.

<u>Passaggi da riprodurre</u>:

1. Accedi come utente.
1. Aggiungi gli oggetti al carrello e procedi al pagamento.
1. Scegliere un metodo di pagamento senza fare clic sul pulsante **[!UICONTROL Place Order]**.
1. Accedi allo stesso account in un altro browser.
1. Procedere all&#39;estrazione con gli stessi elementi senza fare clic sul pulsante **[!UICONTROL Place Order]**.
1. Fare clic sul pulsante **[!UICONTROL Place Order]** in entrambi i sistemi contemporaneamente.
1. Convalida gli ordini effettuati in entrambi i browser.

<u>Risultati previsti</u>:

Viene elaborato correttamente solo il primo ordine proveniente da un browser.

<u>Risultati effettivi</u>:

In entrambi i browser sono stati inseriti gli ordini.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
