---
title: 'ACSD-58471: il caricamento del contenuto dinamico non riesce nella pagina dei dettagli del prodotto, quando sono state pianificate le regole del prezzo di catalogo associate'
description: Applica la patch ACSD-58471 per risolvere il problema di Adobe Commerce, in cui il contenuto dinamico non viene caricato sulla pagina dei dettagli del prodotto, quando sono state pianificate le relative regole del prezzo di catalogo.
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471: il caricamento del contenuto dinamico non riesce nella pagina dei dettagli del prodotto, quando sono state pianificate le regole del prezzo di catalogo associate

La patch ACSD-58471 risolve il problema relativo al mancato caricamento del contenuto dinamico nella pagina dei dettagli del prodotto, quando sono state pianificate le regole del prezzo di catalogo associate. Il sistema ora visualizza correttamente il contenuto dinamico associato alle regole del prezzo di catalogo programmato nella pagina dei dettagli del prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-58471. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il contenuto dinamico non viene caricato sulla pagina dei dettagli del prodotto quando sono pianificate le regole del prezzo di catalogo.

<u>Passaggi da riprodurre</u>:

1. Creare un blocco dinamico in Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Creare un blocco statico in [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Utilizza i widget per aggiungere contenuti.
1. Crea un prodotto e aggiungi il blocco CMS alla descrizione.
1. Crea una regola di catalogo con un aggiornamento pianificato e assegna il prodotto e il blocco dinamico creato in **[!UICONTROL Marketing]** > Promozioni > **[!UICONTROL Catalog Products Rules]**.
1. Esegui la cron e verifica che la pagina dei dettagli del prodotto mostri il contenuto dinamico dopo l’ora di inizio pianificata.
1. Crea una regola di catalogo senza un aggiornamento pianificato e assegna il prodotto e il blocco dinamico creato in **[!UICONTROL Marketing]** > Promozioni > **[!UICONTROL Catalog Products Rules]**.
1. Esegui la cron e verifica se nella pagina di dettaglio del prodotto viene visualizzato il contenuto dinamico dopo l’orario pianificato.


<u>Risultati previsti</u>:

Il contenuto dinamico viene caricato dopo l’ora di inizio pianificata.

<u>Risultati effettivi</u>:

Il contenuto dinamico non viene caricato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
