---
title: Panoramica sull'installazione locale
description: Scopri il processo di installazione per le implementazioni locali di Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 9ad18dac76f171ad0f90330e1a1347baa056403b
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 2%

---


# Panoramica sull&#39;installazione locale

Questa pagina fornisce una panoramica dell’installazione di Adobe Commerce sulla tua infrastruttura. Il processo di installazione prevede la configurazione dell&#39;ambiente server, l&#39;ottenimento del software e delle credenziali necessarie e l&#39;esecuzione del comando di installazione.

È possibile installare il software Adobe Commerce on-premise in circa 30-60 minuti. Tuttavia, il tempo necessario per configurare l&#39;ambiente server prima dell&#39;installazione varia in base all&#39;esperienza e alle tecnologie selezionate.

>[!TIP]
>
>Per procedere correttamente, devi disporre di conoscenze tecniche intermedie e di accesso al server.

L&#39;installazione crea un archivio Adobe Commerce completamente funzionante con una [vetrina per il cliente](https://experienceleague.adobe.com/it/docs/commerce-admin/start/storefront/storefront) e un [pannello amministrativo](https://experienceleague.adobe.com/it/docs/commerce-admin/start/admin/admin). Prima di iniziare il processo, è necessario disporre delle credenziali del database, delle informazioni sul dominio e delle chiavi di autenticazione.

## Responsabilità del commerciante

Con Adobe Commerce on-premise, è possibile ospitare e gestire la propria infrastruttura, inclusi server, ambienti di hosting e manutenzione dei sistemi. Adobe fornisce supporto specifico per l’applicazione Commerce di base, tra cui:

- Accesso agli aggiornamenti e alle correzioni dei prodotti
- Patch di sicurezza per risolvere le vulnerabilità
- Documentazione completa per aiutarti a gestire e ottimizzare la tua soluzione con hosting autonomo

Le aziende hanno il pieno controllo dell&#39;ambiente, consentendo una maggiore personalizzazione e flessibilità, ma sono responsabili di garantire le prestazioni, la sicurezza e la scalabilità dell&#39;infrastruttura. Ad esempio, sei responsabile di quanto segue:

- Progettazione, implementazione, configurazione, manutenzione, risoluzione dei problemi e test delle prestazioni di tutti i sistemi Adobe Commerce locali.
   - Server, sistema operativo, database, [!DNL PHP], ricerca, memorizzazione nella cache, cache a pagina intera e rete di distribuzione dei contenuti. I temi comuni possono includere [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] e qualsiasi [!DNL CDN] utilizzato.
- Pianificazione della capacità, scalabilità automatica, clustering, backup, disaster recovery
- Tutti i dati relativi a prodotti e clienti, progettazione, configurazione e configurazione, manutenzione di applicazioni e database, distribuzione del codice, aggiornamenti delle versioni e applicazione di patch
- Monitoraggio e avvisi tramite APM/registrazione/avvisi (ad esempio, [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- Applicazione di patch di sicurezza per il sistema operativo, [!DNL PHP], database, protezione avanzata middleware e aggiornamenti

## Flusso di lavoro

Il diagramma seguente illustra i passaggi principali necessari per l’installazione di Adobe Commerce per ambienti locali:

![Funzionamento dell&#39;installazione](../assets/installation/on-premises-install.drawio.svg)

### Configurare l’ambiente server

Installa e configura PHP, server Web, database e motore di ricerca in base ai [prerequisiti](prerequisites/overview.md).

### Ottieni chiavi di autenticazione

Genera nuove [chiavi di autenticazione](prerequisites/authentication-keys.md) (o copia le chiavi esistenti) da Commerce Marketplace per accedere ai pacchetti Adobe Commerce Composer.

### Ottieni il software Adobe Commerce

Scarica utilizzando [Compositore](prerequisites/commerce.md) (consigliato) o clona da GitHub per i contributi di sviluppo.

Se desideri contribuire al codebase di Magento Open Source o personalizzare l&#39;applicazione, [clona](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) l&#39;archivio GitHub. Questo metodo richiede familiarità sia con GitHub che con Composer.

### Installare l’applicazione

Eseguire il comando di installazione con la configurazione specifica. Per esempi completi, consulta la [guida rapida](composer.md).

>[!NOTE]
>
>Se i passaggi non riescono perché i prerequisiti software non sono configurati correttamente, esaminare i [prerequisiti](prerequisites/overview.md).

### Verificare l&#39;installazione

[Verifica](next-steps/verify.md) la vetrina e il pannello di amministrazione per verificare che tutto funzioni correttamente.

## Problemi comuni di installazione

- **Errori di autorizzazione**: garantire la proprietà e le autorizzazioni appropriate del file system
- **Errori di connessione al database**: verificare le credenziali del database e la connettività di rete
- **Errori chiave di autenticazione**: verificare che le chiavi Commerce Marketplace siano valide e attive
- **Limiti di memoria**: assicurarsi che la memoria PHP sia allocata a sufficienza (si consiglia un minimo di 2 GB)
