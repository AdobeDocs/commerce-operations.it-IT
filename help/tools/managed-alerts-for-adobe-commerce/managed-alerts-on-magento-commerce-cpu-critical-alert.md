---
title: 'Avvisi gestiti su Adobe Commerce: avviso critico CPU'
description: In questo articolo vengono descritti i passaggi di risoluzione dei problemi quando si riceve un avviso critico di CPU per Adobe Commerce in [!DNL New Relic]. È necessaria un'azione immediata per risolvere il problema.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 8629ab18-5eef-4d76-9cf8-88fe2d3439df
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---

# Avvisi gestiti su Adobe Commerce: avviso critico CPU

In questo articolo vengono descritti i passaggi di risoluzione dei problemi quando si riceve un avviso critico di CPU per Adobe Commerce in [!DNL New Relic]. È necessaria un&#39;azione immediata per risolvere il problema. L’avviso avrà un aspetto simile al seguente, a seconda del canale di notifica dell’avviso selezionato.

![avviso disco critico](../../assets/managed-alerts/cpu-critical-magento-managed.png){width="500"}

## Prodotti e versioni interessati

Architettura del piano Pro di Adobe Commerce su infrastruttura cloud

## Problema

Riceverai un avviso gestito in [!DNL New Relic] se hai firmato fino a [Avvisi gestiti per Adobe Commerce](managed-alerts-for-magento-commerce.md) e una o più soglie di avviso sono state superate. Questi avvisi sono stati sviluppati da Adobe Commerce per fornire ai clienti un set standard utilizzando informazioni provenienti da Supporto e Progettazione.

<u>**Esegui!**</u>:

* Interrompi qualsiasi distribuzione pianificata fino a quando l&#39;avviso non viene cancellato.
* Attiva immediatamente la modalità di manutenzione se il sito non risponde o se non risponde completamente. Per ulteriori informazioni, vedere [Attivare o disattivare la modalità di manutenzione](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella Guida all&#39;installazione di Commerce. Assicurarsi di aggiungere l&#39;IP all&#39;elenco degli indirizzi IP esenti per assicurarsi di poter accedere al sito per la risoluzione dei problemi. Per ulteriori informazioni, vedere [Gestire l&#39;elenco degli indirizzi IP esenti](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses) nella Guida all&#39;installazione di Commerce.

<u>**Non fare!**</u>:

* Avvia ulteriori campagne di marketing che possono portare ulteriori visualizzazioni di pagina sul sito.
* Eseguire gli indicizzatori o altri nodi, che possono causare ulteriore stress sul CPU o sul disco.
* Esegui le principali attività amministrative (ad esempio, l’amministratore di Commerce, le importazioni/esportazioni di dati).
* Cancella la cache.

Se esegui una delle azioni &quot;Non rispondere&quot; prima di aver indagato e risolto la causa dell’avviso, il sito potrebbe non rispondere (se non stai già verificando un’interruzione).

## Soluzione

Per identificare e risolvere la causa, seguire la procedura riportata di seguito.

>[!WARNING]
>
>Poiché si tratta di un avviso critico, è consigliabile completare il **passaggio 1** prima di provare a risolvere il problema (passaggio 2 in poi).

Controlla se è presente il ticket di supporto Adobe Commerce. Per i passaggi, consulta [Tracciare i ticket di supporto](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) nella Knowledge Base di supporto di Commerce. Il supporto potrebbe aver ricevuto un avviso di soglia [!DNL New Relic], creato un ticket e iniziato a lavorare sul problema. Se non esiste alcun ticket, creane uno. Il ticket deve contenere le seguenti informazioni:

1. Motivo contatto: selezionare **[!UICONTROL New Relic CRITICAL alert received]**.
1. Descrizione dell&#39;avviso.
1. [[!DNL New Relic] Collegamento per incidente](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Questo è incluso nei tuoi [Avvisi gestiti per Adobe Commerce](managed-alerts-for-magento-commerce.md).
1. Utilizza la pagina Transazioni di [[!DNL New Relic] APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) per identificare le transazioni con problemi di prestazioni:
   * Ordina le transazioni in base ai punteggi di Apdex crescenti. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) fa riferimento alla soddisfazione degli utenti per il tempo di risposta delle applicazioni e dei servizi Web. Un punteggio [basso [!DNL Apdex] basso](managed-alerts-for-magento-commerce-apdex-warning-alert.md) può indicare un collo di bottiglia (una transazione con un tempo di risposta maggiore). In genere è correlato al database, [!DNL Redis] o PHP. Per i passaggi, fare riferimento a New Relic [Visualizza le transazioni con il più alto [!DNL Apdex] insoddisfazione](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Ordina le transazioni in base alla velocità effettiva più elevata, al tempo medio di risposta più lento, alla quantità di tempo più elevata e ad altre soglie. Per i passaggi, consultare [!DNL New Relic] [Trova problemi di prestazioni specifici](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Se non riesci ancora a identificare l&#39;origine, utilizza la pagina Infrastruttura di [[!DNL New Relic] APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page) per identificare i servizi che richiedono molte risorse. Per i passaggi, vedere [!DNL New Relic] [Pagina Host di monitoraggio dell&#39;infrastruttura: scheda Processi](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Se identifichi l’origine, SSH nell’ambiente per approfondire l’analisi. Per i passaggi, consulta [SSH nel tuo ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=it) nella Guida di Commerce su Cloud.
1. Se hai ancora difficoltà a identificare l’origine:
   * Esamina le tendenze recenti per identificare i problemi relativi alle recenti implementazioni del codice o modifiche alla configurazione (ad esempio, nuovi gruppi di clienti e modifiche di grandi dimensioni al catalogo). È consigliabile verificare negli ultimi sette giorni di attività le correlazioni presenti nelle distribuzioni o nelle modifiche del codice.
   * Valutare la possibilità di verificare e disabilitare i cataloghi flat. Per i passaggi, consultare [Crons con prestazioni lente e esecuzione lenta](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) nella Knowledge Base del supporto Commerce.
   * Se sospetti di avere un attacco DDoS, prova a bloccare il traffico da bot. Per ulteriori informazioni, vedere [Come bloccare il traffico dannoso per Adobe Commerce sull&#39;infrastruttura cloud al livello Fastly](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) nella Knowledge Base di supporto Commerce.
1. Se il problema sembra temporaneo, esegui passaggi di mitigazione quali un upsize o imposta il sito in modalità di manutenzione. Per ulteriori informazioni, vedere [Come richiedere il ridimensionamento temporaneo](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) nella Knowledge Base del supporto tecnico Commerce e [Attivare o disattivare la modalità di manutenzione](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) nella Guida all&#39;installazione di Commerce. Se l’upsize ripristina le normali operazioni del sito, è consigliabile richiedere un upsize permanente (contatta il team dell’account Adobe) o provare a riprodurre il problema nella gestione temporanea dedicata eseguendo un test di carico e ottimizzando le query o il codice che riduce la pressione sui servizi. Per i passaggi, consulta [Test di carico e stress](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) in Commerce on Cloud Guide.
