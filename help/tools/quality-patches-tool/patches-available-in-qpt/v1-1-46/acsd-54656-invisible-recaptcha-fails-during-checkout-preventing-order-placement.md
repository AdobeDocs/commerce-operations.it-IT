---
title: Invisible [!DNL reCAPTCHA] non riesce durante l'estrazione, impedendo il posizionamento dell'ordine
description: Applica la patch ACSD-54656 per risolvere il problema Adobe Commerce in cui l'invisibile [!DNL reCAPTCHA] non funziona correttamente durante l'estrazione, impedendo il posizionamento di un ordine.
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656: [!DNL reCAPTCHA] invisibile non funziona correttamente durante l&#39;estrazione. Ciò impedisce il posizionamento di un ordine.

La patch ACSD-54656 risolve il problema che impedisce il corretto funzionamento dell&#39;invisibile [!DNL reCAPTCHA] durante il pagamento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46. L’ID della patch è ACSD-54656. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL reCAPTCHA] invisibile non funziona correttamente durante l&#39;estrazione. Ciò impedisce il posizionamento di un ordine.

<u>Passaggi da riprodurre</u>:

1. Abilitare qualsiasi tipo di [!DNL reCAPTCHA] per gift card nella pagina [!UICONTROL Checkout].
1. Aggiungi il prodotto al carrello e vai alla pagina **[!UICONTROL Checkout]**.
1. Espandi il modulo gift card e compila un buono regalo valido.
1. Fare clic sul pulsante **[!UICONTROL See balance and apply]**.

<u>Risultati previsti</u>:

La gift card è stata applicata correttamente.

<u>Risultati effettivi</u>:

Viene visualizzato un messaggio di errore: convalida *[!DNL reCAPTCHA]non riuscita, riprova*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
