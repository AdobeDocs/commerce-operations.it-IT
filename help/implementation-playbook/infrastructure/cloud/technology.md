---
title: Tecnologie dell'infrastruttura cloud
description: Scopri più da vicino la raccolta di tecnologie utilizzate per Adobe Commerce sull’infrastruttura cloud.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Tecnologie

As we’ve mentioned, Adobe Commerce leverages a number of software solutions to support the platform. In particolare, per quanto riguarda la produzione, abbiamo suddiviso alcune delle soluzioni e funzionalità tecniche incluse in Adobe Commerce sull’infrastruttura cloud che consentono di sfruttare al meglio il tuo ambiente di produzione.

![Diagramma che mostra l’Adobe Commerce sulla tecnologia dell’infrastruttura cloud](../../../assets/playbooks/infrastructure-technology.svg)

## Soluzioni software

- **Nginx** - Server web che utilizza PHP-FPM. There is one instance with multiple workers.

- **GlusterFS** - File server per la gestione di tutte le distribuzioni di file statici e la sincronizzazione con quattro installazioni di directory:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** - Un server per VM con un solo server attivo e gli altri due come repliche.

- **Elasticsearch** - Cerca Adobe Commerce versione 2.2.x e successive.

- **Galera**—Database cluster with one MariaDB MySQL database per node with an auto-increment setting of three for unique IDs across every database.

## Features and benefits

- Con tre istanze dedicate in un VPC, esiste un bilanciamento del carico elastico su tre aree di disponibilità o centri dati separati.

- Viene fornita una maggiore resilienza rispetto agli eventi che possono causare il mancato funzionamento di una singola istanza. Ad esempio, un’interruzione di un’intera zona di disponibilità AWS o di un centro dati.

- Zero downtime scaling across the entire stack, including web, caching, search, and database, in less than 15 minutes.
