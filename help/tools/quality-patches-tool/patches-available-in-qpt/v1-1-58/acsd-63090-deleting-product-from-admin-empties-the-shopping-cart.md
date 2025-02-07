---
title: 'ACSD-63090: l’eliminazione di un prodotto dall’amministratore comporta lo svuotamento del carrello'
description: Applica la patch ACSD-63090 per risolvere il problema Adobe Commerce relativo alla scomparsa degli articoli del carrello di un cliente in seguito all’eliminazione di un prodotto dopo che è stato aggiunto al carrello.
feature: Shopping Cart, Quotes
role: Admin, Developer
source-git-commit: 513993f0c4bd97047ad128a25a4b2a6b3eebd82b
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090: l’eliminazione di un prodotto dall’amministratore comporta lo svuotamento del carrello

La patch ACSD-63090 risolve il problema relativo alla scomparsa degli articoli del carrello di un cliente in seguito all’eliminazione di un prodotto dall’amministratore, dopo che è stato aggiunto al carrello. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63090. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli articoli del carrello scompaiono quando un prodotto viene eliminato dopo essere stato aggiunto al carrello.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con due prodotti secondari.
1. Accedi come cliente registrato.
1. Aggiungi entrambi i prodotti secondari al carrello.
1. Esci dall’account.
1. Elimina uno dei prodotti secondari dal catalogo.
1. Aggiorna il prezzo dell’altro prodotto secondario utilizzando l’API.

<u>Risultati previsti</u>:

Il prodotto rimanente viene visualizzato nel carrello e l&#39;offerta esistente viene aggiornata nella tabella del database `quote`.

<u>Risultati effettivi</u>:

* Il mini carrello è vuoto.
* Nella tabella del database `quote` è stato generato un nuovo record di virgolette.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
