---
title: 'Avvisi gestiti su Adobe Commerce: avviso di memoria critica'
description: In questo articolo vengono descritti i passaggi di risoluzione dei problemi quando si riceve un avviso di memoria critica per Adobe Commerce in [!DNL New Relic]. È necessaria un'azione immediata per risolvere il problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: dedaf4eeb9403945ada1a90a82f4be45ff98ec4e
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avviso di memoria critica

In questo articolo vengono descritti i passaggi di risoluzione dei problemi quando si riceve un avviso di memoria critica per Adobe Commerce in [!DNL New Relic]. È necessaria un&#39;azione immediata per risolvere il problema.

![avviso disco critico](../../assets/managed-alerts/memory-critical-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Tutte le versioni di Adobe Commerce su infrastruttura cloud Architettura del piano Pro.

## Problema

Riceverai un avviso gestito in [!DNL New Relic] se hai firmato fino a [Avvisi gestiti per Adobe Commerce](managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe per fornire ai clienti un set standard utilizzando informazioni provenienti da Supporto e Progettazione.

<u> **Esegui!** </u>

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per i passaggi, vedere [Attivare o disattivare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella Guida all&#39;installazione di Commerce. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per i passaggi, vedere [Gestire l&#39;elenco degli indirizzi IP esenti](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) nella Guida all&#39;installazione di Commerce.

<u>**Non fare!**</u>

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire gli indicizzatori o altri nodi che possono causare ulteriore stress su CPU o disco.
* Esegui le principali attività amministrative (ad esempio, amministrazione di Commerce, importazioni/esportazioni di dati).
* Cancella la cache.

Il sito potrebbe non rispondere (se non si è già verificata un’interruzione) se si esegue una delle azioni &quot;Non rispondere&quot; prima di aver indagato e risolto la causa dell’avviso.

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

>[!WARNING]
>
>Poiché si tratta di un avviso critico, è consigliabile completare il **passaggio 1** prima di provare a risolvere il problema (passaggio 2 in poi).

1. Controlla se è presente un ticket di supporto Adobe Commerce. Per i passaggi, consulta [Tracciare i ticket di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) nella Knowledge Base di supporto di Commerce. Il supporto potrebbe aver già ricevuto un avviso di soglia [!DNL New Relic], creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:
   * Motivo contatto: è stato ricevuto **[!UICONTROL New Relic]** avviso CRITICO selezionato
   * Descrizione della segnalazione
   * [[!DNL New Relic] Collegamento per incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nei tuoi [Avvisi gestiti per Adobe Commerce](managed-alerts-for-magento-commerce.md).

1. Utilizzare la pagina Infrastruttura di [[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) per identificare i principali processi che richiedono molta memoria. Per i passaggi, fare riferimento alla pagina [[!DNL New Relic] Host di monitoraggio dell&#39;infrastruttura: scheda Processi](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Se servizi come [!DNL Redis], MySQL o PHP sono le origini principali del consumo di memoria, provare a eseguire le operazioni seguenti:
1. Verifica di disporre delle versioni più recenti. Le versioni più recenti possono a volte correggere le perdite di memoria. Se non utilizzi la versione più recente, puoi procedere con l’aggiornamento. Per i passaggi, consulta [Change Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) nella Guida di Commerce su Cloud.
1. Se il problema con il servizio non è correlato alla versione, provare a eseguire le operazioni seguenti:
1. **MySQL**: verificare la presenza di problemi quali query con esecuzione prolungata, chiavi primarie non definite e indici duplicati. Per i passaggi, fai riferimento a [Problemi più comuni relativi al database in Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) nel playbook di implementazione di Commerce.
1. **[!DNL Redis]**: se [!DNL Redis] è una delle principali fonti di consumo di memoria, [invia un ticket di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
1. **PHP**: se PHP è una fonte principale di consumo di memoria, controllare i processi in esecuzione eseguendo `ps aufx` in CLI/Terminal. Nell’output del terminale vengono visualizzati i processi e i processi cron attualmente in esecuzione. Controlla l’output per il tempo di esecuzione dei processi. Se c&#39;è un cron con un lungo tempo di esecuzione, il cron può essere appeso. Per informazioni sulla risoluzione dei problemi, vedere [Rallentamento delle prestazioni, tempi di esecuzione lenti e lunghi](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) e [Processo Cron bloccato nello stato &quot;in esecuzione&quot;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) nella Knowledge Base del supporto Commerce.
1. Se non riesci ancora a identificare l&#39;origine del problema, utilizza la pagina Transazioni di [[!DNL New Relic] APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) per identificare le transazioni con problemi di prestazioni:
   * Ordina le transazioni in base a [!DNL Apdex] punteggi crescenti. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fa riferimento alla soddisfazione degli utenti per il tempo di risposta delle applicazioni e dei servizi Web. Un [[!DNL Apdex score]](managed-alerts-for-magento-commerce-apdex-warning-alert.md) può indicare un collo di bottiglia (una transazione con un tempo di risposta più elevato). In genere si tratta del database, [!DNL  Redis] o PHP. Per i passaggi, consulta [[!DNL New Relic] Visualizzare le transazioni con il più alto [!DNL Apdex] insoddisfazione](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordina le transazioni in base alla velocità effettiva più elevata, al tempo medio di risposta più lento, al tempo più lungo e ad altre soglie. Per i passaggi, consultare [[!DNL New Relic] [Trova problemi di prestazioni specifici]](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Se non riesci ancora a identificare il problema, utilizza la pagina Infrastruttura di [[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Se non riesci a identificare la causa dell’aumento del consumo di memoria, controlla le tendenze recenti per identificare i problemi relativi alle recenti distribuzioni del codice o alle modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare gli ultimi 7 giorni di attività per eventuali correlazioni nelle distribuzioni o nelle modifiche del codice.
1. Se i metodi di cui sopra non ti aiutano a trovare la causa e/o la soluzione entro un tempo ragionevole, richiedi un upsize o metti il sito in modalità di manutenzione, se non lo hai già fatto. Per i passaggi, vedere [Come richiedere il ridimensionamento temporaneo](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) nella Knowledge Base del supporto Commerce e [Attivare o disattivare la modalità di manutenzione](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella Guida all&#39;installazione di Commerce.
1. Se l’upsize ripristina le normali operazioni del sito, puoi richiedere un upsize permanente (contatta il tuo account team di Adobe) oppure provare a riprodurre il problema nella gestione temporanea dedicata eseguendo un test di carico e ottimizzando le query o il codice che riduce la pressione sui servizi. Consulta [Test di carico e stress](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) nella Guida di Commerce su Cloud.
