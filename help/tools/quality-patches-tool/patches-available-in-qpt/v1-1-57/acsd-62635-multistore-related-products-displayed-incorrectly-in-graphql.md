---
title: 'ACSD-62635: i prodotti correlati a più store non sono visualizzati correttamente in [!DNL GraphQL]'
description: Applica la patch ACSD-62635 per risolvere il problema di Adobe Commerce, in cui i prodotti correlati a più store non vengono visualizzati correttamente nella query del prodotto  [!DNL GraphQL] .
feature: B2B
role: Admin, Developer
source-git-commit: 8e6f6590dbed43eb8ce75b694a05ee951b538814
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635: i prodotti correlati a più store non sono visualizzati correttamente in [!DNL GraphQL]

La patch ACSD-62635 risolve il problema relativo alla visualizzazione non corretta dei prodotti correlati a più store nella query di prodotto [!DNL GraphQL]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) 1.1.57. L’ID della patch è ACSD-62635. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando B2B è abilitato, la richiesta [!DNL GraphQL] restituisce tutti i prodotti correlati da tutti i siti Web anche se nella richiesta viene utilizzato un ambito di visualizzazione archivio.

<u>Passaggi da riprodurre</u>:

1. Creare due siti Web, store e visualizzazioni dello store.
1. Crea i seguenti prodotti semplici:
   * Un principale con SKU *product1* assegnato a tutti i siti Web
   * Uno assegnato solo a *Sito Web 1*
   * Uno assegnato solo a *Sito Web 2*
   * Uno assegnato a *Sito Web 1* e *Sito Web 2*
1. Aggiungi tutti i prodotti come correlati a *product1*.
1. Abilita [!UICONTROL B2B] e [!UICONTROL Shared Catalog].
1. Aggiungi tutti i prodotti al catalogo condiviso predefinito.
1. Invia la richiesta [!DNL GraphQL] per recuperare *product1* e i prodotti correlati con il codice store di *Website 1* nell&#39;intestazione.

<u>Risultati previsti</u>:

La risposta contiene prodotti correlati solo dai siti web che corrispondono al codice dello store inviato nell’intestazione della richiesta.

<u>Risultati effettivi</u>:

La risposta contiene tutti i prodotti correlati di tutti i siti web, indipendentemente dal codice store specificato nella richiesta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
