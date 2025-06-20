---
title: 'ACSD-55231: errore SKU non trovato durante l’utilizzo della funzionalità di ordine rapido'
description: Applica la patch ACSD-55231 per risolvere il problema di Adobe Commerce, se viene visualizzato l’errore *"Lo SKU non è stato trovato nel catalogo"* quando si tenta di aggiungere un prodotto al carrello utilizzando la funzionalità di ordine rapido.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-55231: errore SKU non trovato durante l’utilizzo della funzionalità di ordine rapido

La patch ACSD-55231 risolve il problema che causava l&#39;errore *&#39;Impossibile trovare lo SKU nel catalogo&#39;* durante il tentativo di aggiungere un prodotto al carrello utilizzando la funzionalità di ordine rapido. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44. L’ID della patch è ACSD-55231. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Recupero di *&#39;errore SKU non trovato nel catalogo&#39;* durante la ricerca di prodotti da aggiungere al carrello utilizzando la funzionalità di ordine rapido.

<u>Passaggi da riprodurre</u>:

1. Installare Adobe Commerce con moduli B2B.
1. Passa a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** e imposta:
   * **[!UICONTROL Enable company]**: *Sì*
   * **[!UICONTROL Enable Shared Catalog]**: *Sì*
   * **[!UICONTROL Enable Quick Order]**: *Sì*
1. Salva la configurazione precedente.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e crea un nuovo catalogo condiviso.
1. Passa a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e crea un nuovo cliente:
   * Nel campo gruppo scegliere il catalogo condiviso creato di recente e impostare *[!UICONTROL Allow remote shopping assistance]* su *Sì*.
1. Generare un prodotto semplice con SKU *p12*, associarlo alla categoria *c1* e quindi scegliere il catalogo condiviso appena creato nella sezione [!UICONTROL Product in Shared Catalog].
1. Esegui:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Aggiorna la pagina di amministrazione.
1. Passa a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e modifica il cliente creato in precedenza.
1. Fare clic su **[!UICONTROL Login as customer]**.
1. Vai a **[!UICONTROL Quick order]**.
1. Cerca lo SKU di *p12* e fai clic su **[!UICONTROL Product Suggestion]**.
1. Aggiungi questo prodotto al carrello e ordina.
1. Torna a **[!UICONTROL Quick Order]**, cerca nuovamente lo SKU *p12* e fai clic su **[!UICONTROL Product Suggestion]**.

<u>Risultati previsti</u>:

Puoi aggiungere il prodotto al carrello utilizzando la funzionalità di ordine rapido.

<u>Risultati effettivi</u>:

Impossibile aggiungere il prodotto al carrello utilizzando la funzionalità di ordine rapido e ottenere *&#39;Errore SKU non trovato nel catalogo&#39;* durante la ricerca dello SKU del prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
