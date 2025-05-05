---
title: 'ACSD-63574: l''aggiunta dell''inserzione [!UICONTROL Bundle Product] al blocco tramite [!DNL Page Builder] genera un errore'
description: Applica la patch ACSD-63574 per risolvere il problema di Adobe Commerce, dove l’aggiunta di **[!UICONTROL Bundle Product]** con le opzioni "Checkbox" o "Multi Select" a un blocco tramite [!DNL Page Builder] genera un errore.
feature: Page Builder, Page Content
role: Admin, Developer
source-git-commit: b2e6a3a61dbd3cd3b76e968ff8cdad664663fc4b
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: l&#39;aggiunta dell&#39;inserzione [!UICONTROL Bundle Product] al blocco tramite [!DNL Page Builder] genera un errore

La patch ACSD-63574 risolve il problema che causava un errore quando si aggiungeva **[!UICONTROL Bundle Product]** con opzioni `Checkbox` o `Multi Select` a un blocco tramite [!DNL Page Builder]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-63574. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p10

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si aggiunge **[!UICONTROL Bundle Product]** a un blocco utilizzando [!DNL Page Builder], l&#39;anteprima del widget del prodotto si interrompe e viene visualizzato il messaggio di errore *Si è verificato un errore durante la generazione del contenuto*. Questo problema si verifica in modo specifico quando il prodotto bundle include `Checkbox` o `Multi Select` tipi di opzione e `indexer dimension mode` è impostato su `website_and_customer_group`. Nel registro eccezioni viene visualizzato il seguente errore:

    &quot;
    report.CRITICAL: PDOException: SQLSTATE[42S02]: tabella o vista di base non trovata: 1146 La tabella &#39;db_name.catalog_product_index_price_cg0_ws0&#39; non esiste in /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Nel pannello a sinistra, espandi **[!UICONTROL Catalog]** e seleziona **[!UICONTROL Catalog]** tra le opzioni seguenti.
1. Scorri verso il basso fino alla sezione **[!UICONTROL Price]** e imposta **[!UICONTROL Catalog Price Scope]** su **[!UICONTROL Global]**.
1. Imposta `Indexer dimension mode` su `website_and_customer_group` utilizzando il comando seguente:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Creare un **[!UICONTROL Bundle Product]** con un tipo di opzione bundle `Checkbox` o `Multi Select` e assegnare il prodotto a una categoria.
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**.
1. Selezionare la categoria a cui è assegnato il prodotto creato e provare a **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

Prodotto aggiunto senza errori.

<u>Risultati effettivi</u>:

Impossibile aggiungere un prodotto tramite [!DNL Page Builder] quando il tipo di opzione **[!UICONTROL Bundle Product]** è `Checkbox` o `Multi Select` e `indexer dimension mode` è impostato su `website_and_customer_group`. Viene generato l&#39;errore: *Si è verificato un errore durante la generazione del contenuto*.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
