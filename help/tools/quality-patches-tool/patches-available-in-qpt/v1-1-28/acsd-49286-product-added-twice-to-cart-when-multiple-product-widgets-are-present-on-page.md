---
title: 'ACSD-49286: prodotto aggiunto due volte al carrello quando sono presenti più widget di prodotto'
description: Applica la patch ACSD-49286 per risolvere il problema di Adobe Commerce, in cui il prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286: prodotto aggiunto due volte al carrello quando sono presenti più widget di prodotto

La patch ACSD-49286 risolve il problema se il prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. L’ID della patch è ACSD-49286. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto viene aggiunto due volte al carrello quando sulla pagina sono presenti più widget di prodotto.

<u>Passaggi da riprodurre</u>:

1. Accedi all&#39;amministratore e vai a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Nella sezione del contenuto, fare clic su **[!UICONTROL Edit]** utilizzando [!DNL Page Builder].
1. Aggiungere due elementi riga a **[!UICONTROL Content]**.
1. Aggiungi prodotti in entrambi gli elementi riga.
1. Nella prima riga, impostare l&#39;aspetto del prodotto come [!UICONTROL Product Grid] e selezionare una categoria da visualizzare.
1. Nella seconda riga, impostare l&#39;aspetto del prodotto come [!UICONTROL Product Carousel] e selezionare un&#39;altra categoria da visualizzare.
1. Andare alla vetrina **[!UICONTROL Home Page]** e aggiungere un prodotto dalla griglia prodotti.
1. Aggiungi un altro prodotto da [!UICONTROL Product Carousel].

<u>Risultati previsti</u>:

La quantità di prodotto non deve raddoppiare dopo l&#39;aggiunta di un prodotto al carrello da [!UICONTROL Product Grid].

<u>Risultati effettivi</u>:

La quantità di prodotto raddoppia dopo l&#39;aggiunta di un prodotto al carrello da [!UICONTROL Product Grid].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
