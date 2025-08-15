---
title: 'ACSD-62671: [!DNL GraphQL] non restituisce l''indirizzo aggiornato al primo tentativo'
description: Applica la patch ACSD-62671 per risolvere il problema di Adobe Commerce per cui una richiesta di  [!DNL GraphQL]  non restituisce informazioni aggiornate sull'indirizzo al primo tentativo.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] non restituisce l&#39;indirizzo aggiornato al primo tentativo

La patch ACSD-62671 risolve il problema per cui una richiesta [!DNL GraphQL] non restituisce informazioni aggiornate sull&#39;indirizzo al primo tentativo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) 1.1.57. L’ID della patch è ACSD-62671. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si utilizza [!DNL GraphQL Application Server], la richiesta dell&#39;indirizzo del cliente non restituisce i dati più recenti.

<u>Passaggi da riprodurre</u>:

1. Installa e avvia [!DNL GraphQL Application Server].
1. Assicurarsi che il tipo di cache `graphQL_query_resolver_result` sia abilitato.
1. Utilizza [!DNL GraphQL] per:

   * Crea un cliente.
   * Genera un token.
   * Utilizza il token per creare più indirizzi per il cliente sopra indicato.

1. Invia la richiesta [!DNL GraphQL] per ottenere gli indirizzi del cliente.
1. Aggiungi un nuovo indirizzo al cliente.
1. Ripeti la richiesta dal passaggio #4 più volte durante il monitoraggio del conteggio degli indirizzi restituito nella risposta.

<u>Risultati previsti</u>:

La risposta [!DNL GraphQL] contiene il numero corretto di indirizzi cliente.

<u>Risultati effettivi</u>:

Talvolta, nella risposta di [!DNL GraphQL] viene restituito un numero errato di indirizzi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
