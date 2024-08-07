---
title: Panoramica sulla distribuzione
description: Scopri le strategie di distribuzione per l’applicazione Commerce.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Panoramica sulla distribuzione

In questi argomenti viene illustrato il processo di distribuzione dell&#39;applicazione Commerce in un sito di produzione per Adobe Commerce versione 2.2 e successive. L&#39;Adobe consiglia questo metodo di distribuzione per tutti coloro che dispongono di un sito di grandi dimensioni e non desiderano subire tempi di inattività durante la distribuzione.

Se si distribuisce Commerce in un singolo computer e si tollera alcuni tempi di inattività durante la distribuzione, vedere [Distribuzione su un singolo computer](../deployment/single-machine.md).

## Distribuzione della pipeline

Con la versione 2.2 di Commerce, Adobe ha introdotto la _distribuzione pipeline_ come nuovo modo di distribuire in produzione con tempi di inattività minimi. Questo processo di distribuzione si verifica su sistemi diversi e consente di mantenere configurazioni coerenti per tutti i sistemi di distribuzione della pipeline. Si tratta di un modello semplice ma potente che consente di separare le impostazioni di configurazione ordinarie dalle impostazioni specifiche del sistema (come host e porta) o dalle impostazioni sensibili (come nomi e password).

Per utilizzare la distribuzione della pipeline, l’Adobe presuppone che tu sia:

- Un integratore di sistemi esperto con un&#39;eccellente conoscenza delle opzioni di configurazione di Adobe Commerce.
- Gestione di un sito Commerce di grandi dimensioni (migliaia di SKU (Stock-Keeping Unit)) e riduzione al minimo dei tempi di inattività del sito di produzione.
- Conoscenza della programmazione PHP.
- Esperienza con i metodi di controllo del codice sorgente.
- Il codice si trova in un archivio del controllo del codice sorgente. In questa guida, si presume che si stia utilizzando un archivio basato su Git.

### Riduzione dei tempi di inattività

Quando si distribuiscono risorse statiche e si compila il codice in un computer separato dal sistema di produzione, si riducono al minimo i tempi di inattività. I tempi di inattività del sistema di produzione sono limitati al tempo necessario per trasferire i file statici e il codice compilato sul server.

## Sistemi di distribuzione

I termini seguenti vengono utilizzati per descrivere i sistemi coinvolti nella distribuzione.

- **Sistema di sviluppo**: computer su cui gli sviluppatori lavorano per personalizzare il codice e installano estensioni, temi e pacchetti di linguaggio da Commerce Marketplace. Inoltre, puoi apportare tutte le modifiche di configurazione al sistema di sviluppo. Puoi avere molti sistemi di sviluppo.

- **Genera sistema**: un sistema in cui vengono distribuite risorse statiche e viene compilato il codice per il sistema di produzione. Poiché queste risorse vengono create su un sistema non in produzione, i tempi di inattività del sistema di produzione vengono ridotti al minimo.

  Non è necessario che nel sistema di build sia installato Commerce. È necessario solo il codice Commerce, ma non è richiesta alcuna connessione al database. Inoltre, non è necessario che il sistema di build sia un server fisicamente separato.

- **Sistema di gestione temporanea**—_Facoltativo_. Facoltativamente, puoi impostare un sistema di staging da utilizzare per il test finale di tutto il codice integrato, incluso User Acceptance Testing (UAT). Impostare un sistema di gestione temporanea nello stesso modo in cui si imposta un sistema di produzione. Ad eccezione del fatto che la gestione temporanea non è il tuo negozio live e non elabora gli ordini dei clienti, è identica alla produzione.

- **Sistema di produzione**: il tuo archivio live. È necessario apportare modifiche di configurazione dirette minime qui, e sicuramente nulla che non sia stato testato su un’istanza di staging. Se possibile, apportare modifiche alla configurazione con [Patch dati](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) che sono state testate in un&#39;istanza di gestione temporanea/sviluppo.

## Altri metodi di distribuzione

Facoltativamente, puoi utilizzare altri metodi di distribuzione, tra cui:

- Copia sicura con SCP o rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- Strumento [Distribuzione](https://deployer.org/)

## Gestire la configurazione

Dopo il [fattore 3 nella progettazione di app a 12 fattori](https://12factor.net/config), Commerce memorizza ora la configurazione per ogni sistema nel sistema stesso. (Le impostazioni di configurazione di sviluppo sono memorizzate nel sistema di sviluppo, le impostazioni di produzione nel sistema di produzione.)

Dell offre un modo per sincronizzare la configurazione dei sistemi:

- **Configurazione condivisa**—Impostazioni che non sono specifiche del sistema né sensibili.

  Le impostazioni condivise sono impostazioni che desideri siano coerenti nei sistemi di sviluppo e produzione. Imposta la configurazione condivisa nell&#39;Admin nel tuo sistema di sviluppo (o Adobe Commerce sull&#39;infrastruttura cloud _integrazione_).

  Il file di configurazione condiviso, `app/etc/config.php`, deve essere incluso nel controllo del codice sorgente in modo da poter essere condiviso tra i sistemi di sviluppo, generazione e produzione.

- **Configurazione specifica del sistema**: impostazioni che variano in base al sistema, ad esempio i nomi host e le porte dei motori di ricerca.

- **Configurazione sensibile**—Impostazioni che devono essere _non_ nel controllo del codice sorgente perché espongono informazioni personali identificabili (PII) o impostazioni quali chiavi API o password.

  Il file di configurazione specifico del sistema, `app/etc/env.php`, deve _non_ essere incluso nel controllo del codice sorgente o condiviso in altro modo tra i sistemi. Utilizzare invece i comandi [`magento config:set` e `magento:sensitive:set`](../cli/set-configuration-values.md) per fornire i valori per tali impostazioni nel sistema di produzione.

>[!INFO]
>
>Questi nuovi metodi per gestire la configurazione sono facoltativi. Non è necessario, ma si consiglia vivamente di usarli.

Nella maggior parte dei casi, le opzioni di configurazione impostate nella configurazione condivisa, specifica del sistema o sensibile non possono essere modificate nell’amministratore. Questo consente di mantenere le impostazioni coerenti in tutti i sistemi. (Facoltativamente, è possibile utilizzare il comando [`magento config:set`](../cli/set-configuration-values.md) senza l&#39;opzione `--lock` per configurare le impostazioni modificabili in Admin.)

Ogni opzione di configurazione di Commerce ha un _percorso di configurazione_ univoco. Per impostare un valore per un&#39;opzione di configurazione, è possibile utilizzare un comando CLI o una variabile di ambiente per impostare il valore per il percorso di configurazione in un sistema specifico.
