---
title: Architettura di riferimento globale
description: Sfrutta un’architettura di riferimento globale per ottenere il massimo dall’implementazione di Adobe Commerce.
feature: Deploy
hide: true
hidefromtoc: true
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Architettura di riferimento globale (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

Quando si eseguono aziende che hanno più siti per più marchi in più mercati locali (con valute localizzate, lingue, supporti, cataloghi condivisi e carrelli univoci) e che desiderano evitare costi superflui per l’implementazione della stessa funzione e delle stesse integrazioni, Global Reference Architecture (GRA) è sempre una buona opzione.

![Tabella che illustra il costo della divergenza nell’architettura](../../../assets/playbooks/divergent-architecture.svg)

![Tabella che illustra il costo del consolidamento nell&#39;architettura](../../../assets/playbooks/consolidated-architecture.svg)

Il GRA è:

- Un approccio di implementazione
- Una strategia di implementazione
- Un modello di governance dei processi

GRA non è:

- Una &quot;funzionalità&quot; del prodotto
- Univoco per qualsiasi piattaforma commerce
- Solo per casi d’uso aziendali globali

Impatti GRA:

- Modalità di distribuzione del codice

   - Basato su archivi di codice specifici, che offrono esperienze diverse.

- Integrazione dei sistemi aziendali

   - Consolida le connessioni ai sistemi aziendali per marchio e/o area geografica.

- Come viene sviluppata e mantenuta la personalizzazione

   - Garantisce che le personalizzazioni siano centralizzate e specifiche per il dominio, in modo che tutte le attività di personalizzazione vengano eseguite da un punto di vista olistico per l’azienda.

- Come si abilitano i nuovi mercati

   - Semplifica il rilascio di più canali e mercati che altrimenti costerebbero molto più tempo e denaro.

>[!TIP]
>
>Consulta [Esempi di GRA](examples.md).
