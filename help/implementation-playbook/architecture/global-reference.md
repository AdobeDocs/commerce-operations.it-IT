---
title: Architettura di riferimento globale di Adobe Commerce
description: Sfrutta al massimo l’implementazione Commerce di Adobe sfruttando un’architettura di riferimento globale.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# Architettura di riferimento globale (GRA)

Quando gestisci aziende che dispongono di più siti per più marchi in più mercati locali (con valute localizzate, lingue, media, cataloghi condivisi e carrelli univoci) e che desiderano evitare costi inutili per l’implementazione delle stesse funzionalità e integrazioni - Global Reference Architecture (GRA) è sempre una buona opzione.

![Table explaining the cost of divergence in architecture](../../assets/playbooks/divergent-architecture.svg)

![Tabella che illustra il costo del consolidamento in architettura](../../assets/playbooks/consolidated-architecture.svg)

GRA è:

- Un approccio di implementazione
- Una strategia di distribuzione
- A process governance model

GRA non è:

- Una &quot;caratteristica&quot; del prodotto
- Unico a qualsiasi piattaforma di e-commerce
- Only for global business use cases

Effetti del GRA:

- Modalità di distribuzione del codice

   - Basato su archivi di codice specifici per uno scopo, che offrono diverse esperienze.

- Integrare i sistemi aziendali

   - Consolidare le connessioni ai sistemi aziendali per marchio e/o regione.

- Modalità di sviluppo e manutenzione della personalizzazione

   - Ensures customizations are centralized and domain-specific so that all customization effort is done from a holistic point of view for the business.

- Modalità di attivazione dei nuovi mercati

   - Semplifica la diffusione di più canali e mercati che altrimenti costerebbero molto più tempo e denaro.

