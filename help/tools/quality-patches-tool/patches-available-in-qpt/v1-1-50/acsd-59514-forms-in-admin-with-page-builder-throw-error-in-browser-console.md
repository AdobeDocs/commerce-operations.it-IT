---
title: 'ACSD-59514: Forms in Admin con  [!DNL Page Builder]  errore generato nella console del browser'
description: Applica la patch ACSD-59514 per risolvere il problema Adobe Commerce relativo al rendering di Forms in Admin con  [!DNL Page Builder]  generato dall'errore "[!DNL Page Builder]" per 5 secondi senza rilasciare blocchi." nella console del browser dopo l’invio del modulo, e le modifiche non possono essere salvate.
feature: Page Builder
role: Admin, Developer
exl-id: 3d1167d2-0a75-48ac-bc31-5bbd3c4a409e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-59514: Forms in Admin con [!DNL Page Builder] genera un errore nella console del browser

La patch ACSD-59514 risolve il problema che causava la generazione dell&#39;errore *[!DNL Page Builder]per 5 secondi senza rilasciare blocchi da parte dei moduli in Admin con [!DNL Page Builder].* nella console del browser dopo l&#39;invio del modulo e le modifiche non possono essere salvate. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. L’ID della patch è ACSD-59514. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Forms in Admin con [!DNL Page Builder] ha generato l&#39;errore *[!DNL Page Builder]di cui è stato eseguito il rendering per 5 secondi senza rilasciare blocchi.* nella console del browser dopo l&#39;invio del modulo e le modifiche non possono essere salvate.

<u>Prerequisiti</u>:

I moduli Adobe Commerce [!DNL Page Builder] sono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Aprire il pannello di amministrazione e fare clic sul pulsante [!UICONTROL Content].
1. Seleziona il blocco e modificalo.
1. Modificare il contenuto e fare clic su [!UICONTROL Save].
1. Apri la console e visualizza il messaggio di errore.

<u>Risultati previsti</u>:

Il blocco è stato salvato correttamente.

<u>Risultati effettivi</u>:

Il caricatore non smette di ruotare e il blocco non viene salvato. Nella console del browser viene visualizzato il seguente errore:
*[!DNL Page Builder]ha eseguito il rendering per 5 secondi senza rilasciare blocchi.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
