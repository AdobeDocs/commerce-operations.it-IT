---
title: 'ACSD-55241: gli attributi **Used** e **Times Used** visualizzano valori errati per i coupon generati'
description: Applica la patch ACSD-55241 per risolvere il problema di Adobe Commerce, in cui gli attributi **Used** e **Times Used** visualizzano valori errati per i coupon generati.
feature: Price Rules
role: Admin, Developer
exl-id: a156f03c-c939-4ea7-bd34-03c2234edbff
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241: **Usati** e **Usati** gli attributi mostrano valori errati per i coupon generati

La patch ACSD-55241 risolve il problema per cui gli attributi **Usato** e **Usato** visualizzano valori errati per i coupon generati. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.47. L’ID della patch è ACSD-55241. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli attributi **Usato** e **Usato** visualizzano valori errati per i coupon generati.

<u>Passaggi da riprodurre</u>:

1. Crea **[!UICONTROL Cart Price Rules]** da **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** e aggiungi eventuali condizioni corrispondenti durante l&#39;ordine (esempio: subtotale maggiore di *5$*)

   * Applica uno sconto.
   * Selezionare **[!UICONTROL Auto Coupon]**.
   * Genera alcuni codici coupon da **Gestione codici coupon**.
   * Reindicizza e pulisci la cache.

1. Crea un **[!UICONTROL customer account]** e accedi al front-end.
1. Aggiungi un prodotto con più di *2* quantità nel carrello e applica un coupon.
1. Fai clic su **[!UICONTROL Check Out with Multiple Addresses]**.
1. Selezionare un indirizzo separato per ciascuna quantità, inserire l&#39;ordine e completare il processo di pagamento.
1. Osserva il totale dell’ordine dall’amministratore e osserva lo sconto applicato.
1. Inserisci un altro ordine con un altro coupon.
1. Eseguire il comando `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` per aggiornare l&#39;utilizzo del codice coupon.

<u>Risultati previsti</u>:

Il conteggio corretto deve essere visualizzato nelle colonne **Tempo utilizzato** e **Usato** con valore **Sì** per **[!UICONTROL manage coupon]** in **[!UICONTROL cart price rule]** nell&#39;amministratore.

<u>Risultati effettivi</u>:

Il conteggio dei codici coupon utilizzati non viene aggiornato nella colonna **Tempo utilizzato** della griglia coupon e la colonna **Usato** mostra il valore *No* se si effettua un ordine con più indirizzi di spedizione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
