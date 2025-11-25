---
title: Avvisi gestiti per Adobe Commerce
description: Se sei un cliente Adobe Commerce su infrastruttura cloud Pro plan architecture, puoi utilizzare avvisi gestiti per comprendere lo stato del sito. Se sei un cliente Adobe Commerce su infrastruttura cloud con architettura di piano Starter, riceverai solo avvisi per  [!DNL Apdex]  e condizioni relative al tasso di errore.
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 4560e7d000ad8333c3089b8b5e8ffd25f5d31b67
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# Avvisi gestiti per Adobe Commerce


Abbiamo creato dashboard e avvisi chiave per aiutarti a capire quando il tuo sito sta raggiungendo i livelli di storage critici e [!DNL Apdex] (soddisfazione degli utenti per i tempi di risposta di applicazioni e servizi). Questo può aiutarti a intraprendere azioni prima di notare tempi di risposta lenti o un’interruzione. Potrai risolvere i problemi relativi agli avvisi con gli articoli elencati di seguito. Prima di poter utilizzare gli avvisi, imposta i canali di notifica. Fare riferimento a [[!DNL New Relic] Configurare i canali di notifica](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) nella Guida di Commerce su Cloud.

>[!NOTE]
>
>Se gli avvisi gestiti per i criteri di avviso di Adobe Commerce non sono disponibili, è possibile che l&#39;account sia stato creato di recente o che [!DNL New Relic] sia stato configurato di recente. Ogni martedì viene eseguito un processo per aggiungere i criteri di avviso a tali account. I criteri di avviso dovrebbero essere disponibili il giorno successivo all&#39;esecuzione del processo successivo. Se il criterio risulta ancora mancante, [invia una richiesta di supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) e includi l&#39;ID progetto.

Di seguito sono riportati i collegamenti agli articoli della Knowledge Base che forniscono passaggi per la risoluzione dei problemi relativi a questi avvisi:

* Avvisi gestiti per Adobe Commerce: avviso di CPU
* Avvisi gestiti per Adobe Commerce: avviso critico CPU
* Avvisi gestiti per Adobe Commerce: avviso di avvertenza memoria
* Avvisi gestiti per Adobe Commerce: avvisi critici per la memoria
* Avvisi gestiti per Adobe Commerce: [!DNL Apdex] avviso
* Avvisi gestiti per Adobe Commerce: [!DNL Apdex] avviso critico
* Avvisi gestiti per Adobe Commerce: avviso di disco
* Avvisi gestiti per Adobe Commerce: avviso disco critico
* Avvisi gestiti su Adobe Commerce: avvisi MariaDB
* Avvisi gestiti su Adobe Commerce: avviso di memoria [!DNL Redis]
* Avvisi gestiti su Adobe Commerce: [!DNL Redis] avviso di memoria critica

>[!NOTE]
>
>La definizione delle soglie per gli avvisi di avvertenza e gli avvisi critici si basa su ricerche condotte utilizzando dati cronologici sulle prestazioni della base clienti e rappresenta le informazioni più recenti fornite dai team di supporto e progettazione di Adobe Commerce. Tieni presente che queste soglie sono soggette a modifiche sulla base dell’ultima analisi continua. In genere, il flusso di avvisi riceve avvisi di gravità inferiore o superiore. È quindi probabile che prima di ricevere un avviso Critico venga visualizzato un avviso di avvertenza. Per informazioni sulla risoluzione dei problemi, consulta i collegamenti agli articoli.

| Gravità | CPU | Memoria | Disco | [!DNL Apdex] | MariaDB | Memoria [!DNL Redis] | Articolo sulla risoluzione dei problemi |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Avvertenza | ✅ |        |      |       |         |              | [Avvisi gestiti per Adobe Commerce: avviso di CPU](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Critico | ✅ |        |      |       |         |              | [Avvisi gestiti per Adobe Commerce: avviso critico CPU](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Avvertenza |     | ✅ |      |       |         |              | [Avvisi gestiti per Adobe Commerce: avviso di memoria](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Critico |     | ✅ |      |       |         |              | [Avvisi gestiti per Adobe Commerce: avviso di memoria critica](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Avvertenza |     |        |      | ✅ |         |              | [Avvisi gestiti per Adobe Commerce: [!DNL Apdex] avviso](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Critico |     |        |      | ✅ |         |              | [Avvisi gestiti per Adobe Commerce: [!DNL Apdex] avviso critico](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Avvertenza |     |        | ✅ |       |         |              | [Avvisi gestiti per Adobe Commerce: avviso disco](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Critico |     |        | ✅ |       |         |              | [Avvisi gestiti per Adobe Commerce: avviso disco critico](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Avviso e critico |     |        |      |       | ✅ |              | [Avvisi gestiti su Adobe Commerce: avvisi MariaDB](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Avvertenza |     |        |      |       |         | ✅ | [Avvisi gestiti in Adobe Commerce: [!DNL Redis] avviso di avviso memoria](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Critico |     |        |      |       |         | ✅ | [Avvisi gestiti in Adobe Commerce: [!DNL Redis] avviso di memoria critica](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |

## Verifica soglie di avviso impostate per gli avvisi gestiti

Puoi rivedere le soglie di avviso configurate per gli avvisi gestiti dal tuo account New Relic. Per istruzioni, vedere [Monitorare le prestazioni con avvisi gestiti](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/investigate/investigate-performance#monitor-performance-with-managed-alerts).
