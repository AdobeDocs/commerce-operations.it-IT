---
title: Architettura di riferimento
description: Esamina i diagrammi dell’architettura di riferimento consigliata per le distribuzioni di Adobe Commerce e di Magento Open Source.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Architettura di riferimento

In questo argomento viene descritta una configurazione generica consigliata per le istanze di Adobe Commerce e di Magento Open Source che utilizzano server semplici ospitati fisicamente in un centro dati (non virtualizzato) in cui le risorse non vengono condivise con altri utenti. Il provider di hosting, soprattutto se è specializzato nell’hosting ad alte prestazioni di Commerce, potrebbe consigliare una configurazione diversa che sia ugualmente o più efficace per i tuoi requisiti.

Per Adobe Commerce sugli ambienti dell’infrastruttura cloud, consulta [Architettura iniziale](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Diagramma dell’architettura di riferimento

Il [!DNL Commerce] Il diagramma dell’architettura di riferimento rappresenta l’approccio migliore per impostare un’architettura [!DNL Commerce] sito.

Il colore di ciascun elemento nel diagramma indica se l’elemento fa parte di Magenti Open Source o Adobe Commerce e se è obbligatorio.

* Gli elementi arancioni sono necessari per il Magento Open Source
* Gli elementi grigi sono facoltativi per il Magento Open Source
* Gli elementi blu sono facoltativi per Adobe Commerce

![Diagramma dell’architettura di riferimento di Commerce](../assets/performance/images/ref-architecture-2.3.png)

Le sezioni seguenti forniscono consigli e considerazioni per ogni sezione del diagramma Commerce Reference Architecture.

### [!DNL Varnish]

* A [!DNL Varnish] il cluster può adattarsi al traffico di un sito
* Ottimizza la dimensione dell’istanza in base al numero di pagine della cache necessarie
* In un sito con traffico elevato, utilizza [!DNL Varnish] Master per garantire lo svuotamento della cache di una richiesta (al massimo) per livello web

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

### Consigliato [!DNL Varnish] architettura di riferimento

Il Magento supporta diversi motori di caching a pagina intera (File, Memcache, Redis, [!DNL Varnish]) pronto all’uso, insieme a una copertura espansa tramite le estensioni. [!DNL Varnish] è il motore di cache a pagina intera consigliato.  [!DNL Commerce] supporta molti diversi [!DNL Varnish] configurazioni.

Per i siti che non richiedono un&#39;elevata disponibilità, si consiglia di utilizzare un [!DNL Varnish] configurazione con terminazione SSL Nginx.

![Semplice [!DNL Varnish] Configurazione con terminazione SSL](../assets/performance/images/single-varnish-with-ssl-termination.png)

Per i siti che richiedono un&#39;elevata disponibilità, si consiglia di utilizzare un [!DNL Varnish] con SSL che termina il load balancer.

![Elevata disponibilità a due livelli [!DNL Varnish] configurazione con SSL che termina il load balancer](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
