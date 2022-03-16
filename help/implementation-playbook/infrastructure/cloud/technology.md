---
title: Tecnologie dell'infrastruttura cloud
description: Scopri più da vicino la raccolta di tecnologie utilizzate per Adobe Commerce sull’infrastruttura cloud.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Tecnologie

Come accennato, Adobe Commerce sfrutta una serie di soluzioni software per supportare la piattaforma. In particolare, per quanto riguarda la produzione, abbiamo suddiviso alcune delle soluzioni e funzionalità tecniche incluse in Adobe Commerce sull&#39;infrastruttura cloud che consentono di sfruttare al meglio l&#39;ambiente di produzione.

![Diagramma che mostra la tecnologia dell’infrastruttura cloud Adobe Commerce](../../../assets/playbooks/infrastructure-technology.svg)

## Soluzioni software

- **Nginx**- Server web che utilizza PHP-FPM. C&#39;è un&#39;istanza con più lavoratori.

- **GlusterFS**- File server per la gestione di tutte le distribuzioni di file statici e la sincronizzazione con quattro installazioni di directory:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**- Un server per VM con un solo server attivo e gli altri due come repliche.

- **Elasticsearch**—Cerca Adobe Commerce versione 2.2.x e successive.

- **Galera**- Cluster di database con un database MySQL MariaDB per nodo con un&#39;impostazione di incremento automatico di tre ID univoci per ogni database.

## Caratteristiche e vantaggi

- Con tre istanze dedicate in un VPC, esiste un bilanciamento del carico elastico su tre aree di disponibilità o centri dati separati.

- Viene fornita una maggiore resilienza rispetto agli eventi che possono causare il mancato funzionamento di una singola istanza. Ad esempio, un’interruzione di un’intera zona di disponibilità AWS o di un centro dati.

- Riduzione del downtime pari a zero per l&#39;intero stack, inclusi web, memorizzazione in cache, ricerca e database, in meno di 15 minuti.
