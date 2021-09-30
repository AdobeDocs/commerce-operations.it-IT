---
title: Ambienti di infrastruttura cloud
description: Utilizza gli ambienti giusti per i casi d’uso appropriati.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Ambienti

L&#39;architettura Adobe Commerce su cloud Infrastructure Pro supporta ambienti che possono essere utilizzati per sviluppare, testare e avviare il proprio negozio. Ogni ambiente contiene un database e un server web. I quattro ambienti utilizzati da Adobe Commerce sono:

- **Integrazione** (Integration) - Fornisce un singolo ramo di ambiente ed è possibile creare fino a quattro rami di ambiente aggiuntivi. Questo consente di distribuire fino a cinque rami attivi nei contenitori Platform-as-a-Service (PaaS).

- **Staging** (Staging) - Fornisce un singolo ramo di ambiente implementato in contenitori IaaS (Infrastructure-as-a-Service) dedicati.

- **Produzione** - Fornisce un singolo ramo di ambiente implementato in contenitori IaaS (Infrastructure-as-a-Service) dedicati.

- **Master globale** (Global Master) - Fornisce un ramo principale implementato nei contenitori Platform-as-a-Service (PaaS).

![Diagramma che mostra la relazione tra gli ambienti Adobe Commerce cloud](../../../assets/playbooks/environment-diagram.svg)

## Rilievi Git

L’ambiente di integrazione fornisce un singolo ramo di integrazione di base contenente il codice Commerce di Adobe distribuito ai contenitori Platform-as-a-Service (PaaS).

Adobe Commerce sugli ambienti di infrastruttura cloud supporta un processo di integrazione continuo e flessibile. Inizia clonando il ramo di integrazione nella cartella di progetto locale. Crea un nuovo ramo, o più rami, per sviluppare nuove funzioni, configurare modifiche e aggiungere estensioni. Con un ramo di codice sviluppato e i file di configurazione corrispondenti, le modifiche del codice sono pronte per essere unite al ramo di integrazione per un test più completo.

![Diagramma che mostra la strategia di diramazione basata su Git per gli ambienti Adobe Commerce cloud](../../../assets/playbooks/branching-diagram.svg)
