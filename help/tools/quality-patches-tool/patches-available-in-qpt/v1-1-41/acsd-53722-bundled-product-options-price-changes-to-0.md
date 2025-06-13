---
title: 'ACSD-53722: il prezzo delle opzioni di prodotto in bundle cambia a $0'
description: Applica la patch ACSD-53722 per risolvere il problema di Adobe Commerce, in cui il prezzo delle opzioni del prodotto in bundle cambia a $ 0 quando diventano attivi aggiornamenti pianificati per ambiti diversi.
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722: il prezzo delle opzioni di prodotto in bundle cambia a $0

La patch ACSD-53722 risolve il problema in cui il prezzo delle opzioni del prodotto in bundle cambia a $ 0 quando diventano attivi aggiornamenti pianificati per ambiti diversi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41. L’ID della patch è ACSD-53722. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo delle opzioni di prodotto in bundle cambia a $0 quando diventano attivi aggiornamenti pianificati per ambiti diversi.

<u>Passaggi da riprodurre</u>:

1. Creare due siti Web, A e B.
1. Imposta la configurazione in **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Crea un prodotto in bundle con un prezzo fisso sui siti Web A e B:

   * Prezzo del prodotto nel pacchetto = Fisso = *0*

1. Aggiungi un prodotto semplice come opzione a discesa per il bundle. Imposta i prezzi seguenti:

   * Prezzo di tutte le visualizzazioni dello store del prodotto semplice all&#39;interno dell&#39;opzione in bundle = *120*
   * Sito Web del prodotto semplice Un prezzo all&#39;interno dell&#39;opzione in bundle = *130*
   * Prezzo B nel sito Web del prodotto semplice nell&#39;opzione in bundle = *140*

1. Pianifica un aggiornamento per disabilitare il prodotto in bundle sul sito Web A.

<u>Risultati previsti</u>:

L’aggiornamento pianificato per il sito web A non influisce sul prezzo del sito web B.

<u>Risultati effettivi</u>:

Dopo l&#39;aggiornamento pianificato, il prezzo dell&#39;opzione del prodotto nel sito Web B è cambiato in **$0**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
