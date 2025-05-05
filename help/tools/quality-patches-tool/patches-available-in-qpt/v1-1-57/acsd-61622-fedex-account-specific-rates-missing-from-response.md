---
title: 'ACSD-61622: [!DNL FedEx] le tariffe specifiche dell''account non sono presenti nella risposta REST API'
description: Applica la patch ACSD-61622 per risolvere il problema di Adobe Commerce per cui nella risposta REST API mancano  [!DNL FedEx]  tariffe specifiche per l'account.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 24acc5f369e0001c8aeab3f81a2e1b51bc523333
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622: nella risposta REST API mancano [!DNL FedEx] tariffe specifiche per l&#39;account

La patch ACSD-61622 risolve il problema in cui le tariffe specifiche dell&#39;account [!DNL FedEx's] non sono presenti nella risposta REST API. Aggiunge il tipo di richiesta di frequenza `ACCOUNT` alla richiesta REST API inviata da Adobe Commerce a [!DNL FedEx], che restituisce una risposta simile alla risposta API dell&#39;SOAP. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-61622. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella risposta REST API mancano [!DNL FedEx's] tariffe specifiche per l&#39;account.

<u>Passaggi da riprodurre</u>:

1. Installa un’istanza Adobe Commerce pulita.
1. Crea un prodotto semplice con un peso di 5 libbre.
1. Configura [!DNL FedEx] per API REST.
1. Abilita il metodo di spedizione [!DNL FedEx] e cancella la cache.
1. Inizia a osservare il file di registro: `var/log/shipping.log`
1. Aggiungi un prodotto semplice al carrello e vai alla pagina di spedizione al momento del pagamento. Esempio di dati del cliente:

   * Codice postale: 58601
   * Nomi: John Doe
   * Indirizzo: 196 Eulalia Burg
   * Paese: Stati Uniti
   * Stato: Dakota del Nord
   * Telefono: 187-563-3627

<u>Risultati previsti</u>:

Le percentuali di `PAYOR_ACCOUNT_PACKAGE` sono disponibili nella risposta REST API, in modo simile alle risposte SOAP API.

<u>Risultati effettivi</u>:

Nella risposta sono disponibili solo `PAYOR_LIST_PACKAGE` tariffe, ovvero non sono presenti tariffe negoziate (account) da [!DNL FedEx].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
