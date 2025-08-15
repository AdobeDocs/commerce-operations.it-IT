---
title: 'Avvisi gestiti su Adobe Commerce: avvisi MariaDB'
description: In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi quando si ricevono gli avvisi MariaDB per Adobe Commerce in [!DNL New Relic]. Gli avvisi MariaDB monitorano il caricamento elevato delle query e le query DML (Data Manipulation Language) eccessive. Entrambe possono comportare una riduzione dell’esperienza utente o addirittura tempi di inattività. È possibile ricevere due tipi di avvisi.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avvisi MariaDB

In questo articolo vengono illustrati i passaggi per la risoluzione dei problemi quando si ricevono gli avvisi MariaDB per Adobe Commerce in [!DNL New Relic]. Gli avvisi MariaDB monitorano il caricamento elevato delle query e le query DML (Data Manipulation Language) eccessive. Entrambe possono comportare una riduzione dell’esperienza utente o addirittura tempi di inattività. Puoi ricevere due tipi di avvisi:

* Avviso query DML
* Query DML critiche

## Prodotti e versioni interessati

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud

## Problema

Riceverai un avviso gestito in [!DNL New Relic] se hai firmato fino a [Avvisi gestiti per Adobe Commerce](managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando informazioni provenienti da Supporto e Progettazione.

**Esegui!**

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per ulteriori informazioni, vedere [Attivare o disattivare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella Guida all&#39;installazione di Commerce. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per ulteriori informazioni, vedere [Gestire l&#39;elenco degli indirizzi IP esenti](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Termina gli script, ad esempio le importazioni, che potrebbero essere la causa dell’avviso se le prestazioni del sito sono interessate.

**Non fare!**

* Eseguire indicizzatori o nodi aggiuntivi che possono causare ulteriore stress su MariaDB.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache.

## Soluzione

**Query DML (query che modificano il database utilizzando UPDATE, INSERT e DELETE)**

Se viene visualizzato un avviso critico sulle query DML, iniziare dal primo passaggio. Se viene visualizzato un avviso di avviso di query DML, iniziare dal passaggio 2.

1. Controlla se è presente un ticket di supporto Adobe Commerce. Per ulteriori informazioni, consulta la nostra knowledge base [Tracciare i ticket di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). Il supporto potrebbe aver ricevuto un avviso di soglia [!DNL New Relic], creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:
   * Motivo contatto: selezionare **[!UICONTROL New Relic MariaDB alert received]**.
   * Descrizione dell&#39;avviso.
   * [[!DNL New Relic] Collegamento per incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nei tuoi [Avvisi gestiti per Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Per identificare l’origine del problema, prova a identificare le query DML:
   1. Esaminare le operazioni del database utilizzando i passaggi della [pagina Database](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time) di New Relic.
   1. Ordina per **[!UICONTROL CALL COUNT]**, quindi per **[!UICONTROL OPERATION]**. Rivedi `INSERT`, `DELETE` e `UPDATE` operazioni.
   1. Cerca AVG alta.
   1. Fare clic per trovare i chiamanti delle operazioni del database. In questo modo verranno identificate le transazioni che utilizzano tale query in base al tempo.
   1. Cerca ottimizzazioni del codice o ottimizzazioni operative:
      * Ottimizzazioni del codice: cerca di ottimizzare le query con inserimenti/aggiornamenti in blocco, riducendo al minimo l’utilizzo dell’indice o limitando il codice.
      * Ottimizzazioni operative: consente di effettuare l’offload delle modifiche dei dati che richiedono un utilizzo intensivo delle risorse per ridurre i tempi di traffico.
      * Ulteriori ottimizzazioni: accertati di aver utilizzato l’ultima versione di ECE-Tools. Per i passaggi, consulta [Aggiornare la versione degli strumenti ece](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) nella Guida di Commerce su Cloud.
