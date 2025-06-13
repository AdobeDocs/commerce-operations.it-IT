---
title: 'ACSD-60673: problema [!UICONTROL Cart Price Rule] risolto per più metodi di pagamento all''atto dell''estrazione'
description: Applicare la patch ACSD-60673 per risolvere il problema di Adobe Commerce in cui gli sconti di un [!UICONTROL Cart Price Rule] che utilizzano una condizione di metodo di pagamento non sono sempre elencati nei totali.
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: problema [!UICONTROL Cart Price Rule] risolto per più metodi di pagamento all&#39;atto dell&#39;estrazione

La patch ACSD-60673 risolve il problema per cui gli sconti di [!UICONTROL Cart Price Rule] che utilizzano una condizione di metodo di pagamento non sono sempre elencati nei totali. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-60673. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Cart Price Rule] per più metodi di pagamento al momento del pagamento non viene applicato correttamente al metodo di pagamento specifico.

<u>Prerequisiti</u>

Assicurarsi che in **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** e **[!UICONTROL Bank Transfer]** sia abilitato.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Multiple Payment Methods]**.
1. Crea un *[!UICONTROL Cart Price Rule]*.
   * Imposta **[!UICONTROL Conditions]**: metodo di pagamento su **[!UICONTROL Money Order]** (o bonifico bancario)
   * Seleziona **[!UICONTROL Actions]** = *25%* sconto su tutti i prodotti
1. Creare un prodotto virtuale.
1. Per copiare un nuovo preventivo e un nuovo cliente ospite *[!UICONTROL Status]*, passare alla vetrina e cancellare i cookie.
1. Aggiungi il prodotto virtuale al carrello.
1. Procedi a *estrazione*.
1. Fare clic sul metodo di pagamento definito in *[!UICONTROL Cart Price Rule]*.
1. Aggiorna *[!UICONTROL Billing Address]*.
1. Assicurati che lo sconto sia visibile nell’importo totale.
1. Fai clic sulla casella di controllo per modificare il metodo di pagamento.
1. Verifica che lo sconto sia visibile.

<u>Risultati previsti</u>:

Lo sconto è visibile in *Totali* dopo aver fatto clic sulla casella di controllo per passare a un metodo di pagamento applicabile.

<u>Risultati effettivi</u>:

Lo sconto non è visibile nei *Totali*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
