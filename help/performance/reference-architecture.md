---
title: Architettura di riferimento
description: Esamina i diagrammi dell’architettura di riferimento consigliata per le implementazioni di Adobe Commerce.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Architettura di riferimento

Questo argomento descrive una configurazione consigliata generica per le istanze di Adobe Commerce che utilizzano server semplici ospitati fisicamente in un centro dati (non virtualizzato) in cui le risorse non vengono condivise con altri utenti. Il provider di hosting, soprattutto se è specializzato nell&#39;hosting ad alte prestazioni di Commerce, potrebbe consigliare una configurazione diversa che sia ugualmente o più efficace per le tue esigenze.

Per Adobe Commerce sugli ambienti dell&#39;infrastruttura cloud, consulta [Architettura Starter](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## [!DNL Commerce] Diagramma dell&#39;architettura di riferimento

Il diagramma dell&#39;architettura di riferimento [!DNL Commerce] rappresenta l&#39;approccio ottimale per impostare un sito [!DNL Commerce] scalabile.

Il colore di ciascun elemento nel diagramma indica se l’elemento fa parte di Magento Open Source o Adobe Commerce e se è obbligatorio.

* Gli elementi arancioni sono necessari per il Magento Open Source
* Gli elementi grigi sono facoltativi per il Magento Open Source
* Gli elementi blu sono facoltativi per Adobe Commerce

![Diagramma dell&#39;architettura di riferimento di Commerce](../assets/performance/images/ref-architecture-2.3.png)

Nelle sezioni seguenti vengono forniti consigli e considerazioni per ogni sezione del diagramma Commerce Reference Architecture.

### [!DNL Varnish]

* Un cluster [!DNL Varnish] può essere ridimensionato al traffico di un sito
* Ottimizza la dimensione dell’istanza in base al numero di pagine della cache necessarie
* In un sito con traffico elevato, utilizza un master [!DNL Varnish] per garantire lo scaricamento della cache di una richiesta (al massimo) per livello web

### Web

* Abilita la scalabilità dei nodi per il traffico e la ridondanza
* Un nodo è principale ed esegue cron
* In alternativa, utilizza nodi Admin e worker dedicati.

### Cache

* Prendi in considerazione l’implementazione di un’istanza Redis separata per le sessioni
* È possibile avere un’istanza Redis per cache
* Ridimensiona l’istanza in modo che contenga la dimensione cache più grande prevista

### Database e code

* I siti a traffico elevato possono regolare le prestazioni del database con database slave e database suddivisi per ordini/carrelli (in Adobe Commerce)
* Prendere in considerazione l&#39;utilizzo di un database slave per consentire il ripristino rapido e il backup dei dati
* I siti a traffico ridotto possono memorizzare immagini nel database

### Ricerca {#search-heading}

* Ottimizzare il numero di istanze in base al traffico di ricerca

### Storage

* Prendere in considerazione l&#39;utilizzo di GFS o GlusterFS per lo storage di pub/supporti
* In alternativa, utilizzare l&#39;archiviazione DB per i siti a traffico ridotto

### Architettura di riferimento [!DNL Varnish] consigliata

Il Magento supporta diversi motori di caching a pagina intera (File, Memcache, Redis, [!DNL Varnish]) preconfigurati, insieme a una copertura estesa tramite le estensioni. [!DNL Varnish] è il motore di cache a pagina intera consigliato.  [!DNL Commerce] supporta diverse configurazioni di [!DNL Varnish].

Per i siti che non richiedono elevata disponibilità, si consiglia di utilizzare una configurazione [!DNL Varnish] semplice con terminazione SSL Nginx.

![Configurazione [!DNL Varnish] semplice con terminazione SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Per i siti che richiedono elevata disponibilità, è consigliabile utilizzare una configurazione [!DNL Varnish] a 2 livelli con un load balancer di terminazione SSL.

![Configurazione a due livelli di elevata disponibilità [!DNL Varnish] con SSL che termina il load balancer](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
