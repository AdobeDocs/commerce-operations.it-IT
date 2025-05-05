---
title: 'ACSD-47704: il pacchetto di prodotti mostra il prezzo dei soli prodotti in magazzino'
description: Applica la patch ACSD-47704 per risolvere il problema Adobe Commerce, in cui un prodotto in bundle mostra il prezzo dei soli prodotti in stock.
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704: il pacchetto di prodotti mostra il prezzo dei soli prodotti in magazzino

La patch ACSD-47704 risolve il problema in cui i prezzi dei segmenti dei clienti vengono memorizzati nella cache in modo errato tra i gruppi di clienti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. L’ID della patch è ACSD-47704. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo di un prodotto in bundle con Dynamic Pricing abilitato non è corretto in quanto sono inclusi solo gli articoli in stock.

<u>Passaggi da riprodurre</u>:

1. Passa al pannello di amministrazione di Commerce.
1. Vai a **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Imposta **[UICONROL Dynamic Price]** su **[!UICONTROL Yes]**.
1. Elementi bundle:
   * Imposta **[!UICONTROL Ship bundle items]** su **[!UICONTROL Together]**
   * Seleziona **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Casella di controllo Contrassegna come obbligatorio
      * Aggiungi qualsiasi prodotto semplice disponibile; ad esempio, Joust Duffle Bag SKU 24-MB01. Prima di aggiungere il prodotto, annota il suo prezzo - $ 34
   * Quantità predefinita: 1
   * Seleziona **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Casella di controllo Contrassegna come obbligatorio
      * Aggiungi qualsiasi prodotto semplice in magazzino, diverso dal prodotto aggiunto nel passaggio precedente; ad esempio - Strive Shoulder Pack 24-MB04. Prima di aggiungere il prodotto, annota il suo prezzo - $ 32
      * Quantità predefinita: 1
1. Salva prodotto.
1. Vai alla vetrina e trova il prodotto creato nei passaggi precedenti. Annota il suo prezzo - $66
(66 = 32 + 34).
Attualmente, il prezzo del prodotto aggregato è pari alla somma dei prezzi delle sue opzioni.
1. Passa al pannello di amministrazione di Commerce. Vai a **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Trova uno dei prodotti semplici assegnati in precedenza come opzione al prodotto bundle:
SKU 24-MB01 e un prezzo di $34.
1. Modificarne la quantità in 0.
1. Salva il prodotto.
1. Vai alla vetrina e trova il prodotto bundle creato nei passaggi precedenti. Annota il suo prezzo - $ 32. In precedenza il prezzo era di 66 dollari, ovvero la somma di 34 dollari da SKU 24-MB01 e 32 dollari da SKU 24-MB04. Ora che il prodotto 24-MB01 è esaurito, il prezzo del bundle è indicato come $32. Si tratta del prezzo dell&#39;altro prodotto, che è un&#39;opzione in stock.

<u>Risultati previsti</u>:

Il prezzo dei prodotti in bundle con Dynamic Pricing abilitato viene calcolato in modo coerente, indipendentemente dal fatto che le opzioni siano disponibili o esaurite.

<u>Risultati effettivi</u>:

Il prezzo del prodotto bundle con Dynamic Pricing abilitato non viene calcolato correttamente. Vengono prese in considerazione solo le opzioni in stock, con un conseguente importo inferiore visualizzato rispetto a quello effettivo quando una delle opzioni è esaurita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
