---
title: 'ACSD-66865: il salvataggio di [!UICONTROL Catalog Price Rule] invalida gli indicizzatori e fornisce un''alternativa alla reindicizzazione solo dei prodotti interessati'
description: Applicare la patch ACSD-66865 per risolvere il problema Adobe Commerce in cui  il salvataggio di un [!UICONTROL Catalog Price Rules] invalida gli indicizzatori e fornisce un'alternativa alla reindicizzazione solo dei prodotti interessati.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865: il salvataggio di **[!UICONTROL Catalog Price Rule]** invalida gli indicizzatori e fornisce un&#39;alternativa alla reindicizzazione solo dei prodotti interessati

La patch ACSD-66865 risolve il problema per cui il salvataggio di un **[!UICONTROL Catalog Price Rule]** invalida gli indicizzatori e fornisce un&#39;alternativa alla reindicizzazione solo dei prodotti interessati. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66865. Questo problema è stato risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il salvataggio di un **[!UICONTROL Catalog Price Rule]** causa l&#39;invalidazione di tutti gli indicizzatori, attivando le reindicizzazioni complete invece di reindicizzare solo i prodotti interessati.

<u>Passaggi da riprodurre</u>:

1. Assicurarsi che cron non sia in esecuzione e che tutti gli indicizzatori siano impostati per l&#39;aggiornamento in base alla pianificazione (tranne `customer_grid` che può essere aggiornato al salvataggio).
2. Eseguire una reindicizzazione manuale completa utilizzando il comando: `php bin/magento indexer:reindex`.
3. Verificare che tutti gli indici mostrino lo stato *[!UICONTROL Ready]* con *0* elementi nel backlog.
4. Nella barra laterale di amministrazione, vai a **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**. Creare una regola di prezzo di catalogo attiva per un singolo prodotto, ad esempio utilizzando una condizione *SKU*.
5. Eseguire il comando `php bin/magento indexer:status` per verificare lo stato dell&#39;indicizzatore.
6. Osservare che più indici sono contrassegnati come **[!UICONTROL Reindex Required]** anche se è interessato un solo prodotto.

<u>Risultati previsti</u>:

Vengono identificati solo i dati del prodotto interessati e viene attivata una reindicizzazione parziale invece di una reindicizzazione completa in tutti gli indici.

<u>Risultati effettivi</u>:

Viene attivata una reindicizzazione completa per tutti gli indicizzatori, anche quando solo un singolo prodotto è interessato da **[!UICONTROL Catalog Price Rule]**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
