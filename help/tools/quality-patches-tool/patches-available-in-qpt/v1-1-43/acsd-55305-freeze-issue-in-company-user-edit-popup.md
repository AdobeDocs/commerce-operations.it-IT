---
title: 'ACSD-55305: blocco a comparsa durante la modifica dell''utente della società in [!UICONTROL My Account]'
description: Applica la patch ACSD-55305 per risolvere il problema Adobe Commerce, in cui la finestra a comparsa [!UICONTROL Edit Company User] sulla pagina [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] si blocca con un caricatore sullo schermo.
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305: blocco a comparsa durante la modifica dell&#39;utente della società in [!UICONTROL My Account]

La patch ACSD-55305 risolve il problema che causa il blocco della finestra popup [!UICONTROL Edit Company User] sulla pagina [!UICONTROL My Account]> [!UICONTROL Company Structure] con un caricatore sullo schermo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. L’ID della patch è ACSD-55305. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante il tentativo di utilizzare la finestra a comparsa *[!UICONTROL Edit Company User]* nella pagina *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]*, poiché si blocca con un caricatore visualizzato sullo schermo.

<u>Passaggi da riprodurre</u>:

1. Creare un’azienda B2B.
1. Crea un attributo a selezione multipla per i clienti.
1. Assegna un valore all’attributo appena creato per l’amministratore della società.
1. Accedi come amministratore della società.
1. Vai a [!UICONTROL account dashboard] e passa a **[!UICONTROL Company Structure]**.
1. Seleziona l’utente.
1. Fai clic su **[!UICONTROL Edit Selected]**.

<u>Risultati previsti</u>:

La finestra a comparsa del modulo viene visualizzata con precisione, offrendo la possibilità di modificare le informazioni aziendali.

<u>Risultati effettivi</u>:

Il menu a comparsa del modulo viene visualizzato senza alcuna possibilità di modifica.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
