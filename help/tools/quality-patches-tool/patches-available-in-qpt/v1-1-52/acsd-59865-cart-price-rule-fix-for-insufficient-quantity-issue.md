---
title: 'ACSD-59865: [!UICONTROL Cart Price Rule] non è in grado di annullare le regole precedenti a causa di una quantità di prodotto insufficiente'
description: Applicare la patch ACSD-59865 per risolvere il problema Adobe Commerce in cui il valore *Incremento quantità sconto* in *Sconto importo fisso,* *Percentuale sconto prezzo prodotto,* e *Acquista X ottieni Y* [!UICONTROL Cart Price Rules] non annulla più l'azione delle regole precedenti.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] non è in grado di annullare le regole precedenti a causa di una quantità di prodotto insufficiente

La patch ACSD-59865 risolve il problema per cui il valore *[!UICONTROL Discount quantity step]* in *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* e *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] non annulla più l&#39;azione delle regole precedenti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-59865. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Cart Price Rule] non riesce ad annullare le regole applicate in precedenza a causa di una quantità di prodotto insufficiente nel carrello.

<u>Passaggi da riprodurre</u>:

1. Accedi come amministratore.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** e fai clic su **[!UICONTROL Add New rule]**.
   * Imposta **[!UICONTROL Rule Name]** = *Test - 1*
   * Seleziona tutti i *siti Web* e i *gruppi di clienti*
   * Imposta **[!UICONTROL Priority]** = *0*
   * Vai alla sezione **[!UICONTROL Actions]**:
      * Imposta **[!UICONTROL Apply]** = *Percentuale di sconto sul prezzo del prodotto*
      * Imposta **[!UICONTROL Discount amount]** = *10*
      * Imposta **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Imposta **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Imposta **[!UICONTROL Discard subsequent rules]** su *No*
1. Cancella la cache.
1. Vai alla vetrina, aggiungi un elemento al carrello e procedi a *pagamento/carrello*.
1. Verifica che lo sconto *10%* sia applicato al carrello.
1. Torna a **[!UICONTROL Cart Price Rules]** e crea una nuova regola.
   * Imposta **[!UICONTROL Rule Name]** = *Test - 2*
   * Seleziona tutti **[!UICONTROL Websites]** e **[!UICONTROL Customer Groups]**
   * Imposta **[!UICONTROL Priority]** = *2*
   * Passare alla sezione **[!UICONTROL Actions]**:
      * Imposta **[!UICONTROL Apply]** = *Percentuale di sconto sul prezzo del prodotto*
      * Imposta **[!UICONTROL Discount amount]** = *20*
      * Imposta **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Imposta **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Cancella la cache.
1. Torna di nuovo alla vetrina.
1. Aggiorna il carrello per aggiornare le regole. Verificare che lo sconto *10%* non sia più applicato.
1. Aggiungi articoli al carrello fino a quando la quantità non soddisfa il valore del *Passaggio* richiesto per la seconda regola.

<u>Risultati previsti</u>:

Il primo [!UICONTROL Cart Price Rule] viene applicato quando vengono soddisfatte le condizioni della seconda regola.

<u>Risultati effettivi</u>:

Le regole di prezzo vengono applicate come configurato nel dashboard di amministrazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
