---
title: Ambienti di infrastruttura cloud
description: Utilizza gli ambienti giusti per i casi d’uso giusti.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Ambienti

L’architettura Pro di Adobe Commerce su infrastruttura cloud supporta gli ambienti utilizzabili per sviluppare, testare e avviare lo store. Ogni ambiente contiene un database e un server web. I quattro ambienti utilizzati da Adobe Commerce sono:

- **Integrazione**- Fornisce un singolo ramo di ambiente e consente di creare fino a quattro rami di ambiente aggiuntivi. Questo consente un massimo di cinque rami attivi distribuiti nei contenitori Platform-as-a-Service (PaaS).

- **Staging**: fornisce un singolo ramo di ambiente distribuito in contenitori IaaS (Infrastructure-as-a-Service) dedicati.

- **Produzione**: fornisce un singolo ramo di ambiente distribuito in contenitori IaaS (Infrastructure-as-a-Service) dedicati.

- **Master globale**- Fornisce un ramo principale distribuito nei contenitori Platform-as-a-Service (PaaS).

![Diagramma che mostra la relazione tra gli ambienti cloud Adobe Commerce](../../../assets/playbooks/environment-diagram.svg)

## Rami Git

L’ambiente di integrazione fornisce un singolo ramo di integrazione di base contenente il codice Adobe Commerce distribuito nei contenitori Platform-as-a-Service (PaaS).

Adobe Commerce sugli ambienti dell’infrastruttura cloud supporta un processo di integrazione flessibile e continuo. Per prima cosa, copia il ramo di integrazione nella cartella di progetto locale. Crea un nuovo ramo, o più rami, per sviluppare nuove funzioni, configurare le modifiche e aggiungere estensioni. Con un ramo di codice sviluppato e i file di configurazione corrispondenti, le modifiche al codice sono pronte per essere unite al ramo di integrazione per test più completi.

![Diagramma che mostra la strategia di ramificazione basata su Git per gli ambienti cloud Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
