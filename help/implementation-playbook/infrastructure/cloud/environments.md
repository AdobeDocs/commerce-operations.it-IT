---
title: Ambienti di infrastruttura cloud
description: Utilizza gli ambienti giusti per i casi d’uso appropriati.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Ambienti

L&#39;architettura Adobe Commerce su infrastruttura cloud Pro supporta ambienti che possono essere utilizzati per sviluppare, testare e avviare lo store. Ogni ambiente contiene un database e un server web. I quattro ambienti utilizzati da Adobe Commerce sono:

- **Integrazione**- Fornisce un singolo ramo di ambiente e puoi creare fino a quattro rami di ambiente aggiuntivi. Questo consente di distribuire fino a cinque rami attivi nei contenitori Platform-as-a-Service (PaaS).

- **Staging**- Fornisce un singolo ramo di ambiente implementato in contenitori IaaS (Infrastructure-as-as-a-Service) dedicati.

- **Produzione**- Fornisce un singolo ramo di ambiente implementato in contenitori IaaS (Infrastructure-as-as-a-Service) dedicati.

- **Master globale**- Fornisce un ramo principale distribuito ai contenitori Platform-as-a-Service (PaaS).

![Diagramma che mostra la relazione tra gli ambienti cloud Adobe Commerce](../../../assets/playbooks/environment-diagram.svg)

## Rilievi Git

L’ambiente di integrazione fornisce un singolo ramo di integrazione di base contenente il codice Adobe Commerce distribuito nei contenitori Platform-as-a-Service (PaaS).

Adobe Commerce sugli ambienti di infrastruttura cloud supporta un processo di integrazione flessibile e continuo. Inizia clonando il ramo di integrazione nella cartella di progetto locale. Crea un nuovo ramo, o più rami, per sviluppare nuove funzioni, configurare modifiche e aggiungere estensioni. Con un ramo di codice sviluppato e i file di configurazione corrispondenti, le modifiche del codice sono pronte per essere unite al ramo di integrazione per un test più completo.

![Diagramma che mostra la strategia di diramazione basata su Git per gli ambienti cloud Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
