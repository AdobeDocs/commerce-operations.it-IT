---
title: Panoramica sulla distribuzione
description: Scopri le strategie di distribuzione per l’applicazione Commerce.
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Panoramica sulla distribuzione

Questi argomenti illustrano il processo di distribuzione dell’applicazione Commerce in un sito di produzione per Adobe Commerce versione 2.2 e successive. L&#39;Adobe consiglia questo metodo di distribuzione per tutti coloro che dispongono di un sito di grandi dimensioni e non desiderano subire tempi di inattività durante la distribuzione.

Se distribuisci Commerce su un singolo computer e tolleri tempi di inattività durante la distribuzione, consulta [Distribuzione su un singolo computer](../deployment/single-machine.md).

## Distribuzione della pipeline

Con Commerce versione 2.2, è stato introdotto un Adobe _distribuzione della pipeline_ come nuovo metodo di implementazione in produzione con tempi di inattività minimi. Questo processo di distribuzione si verifica su sistemi diversi e consente di mantenere configurazioni coerenti per tutti i sistemi di distribuzione della pipeline. Si tratta di un modello semplice ma potente che consente di separare le impostazioni di configurazione ordinarie dalle impostazioni specifiche del sistema (come host e porta) o dalle impostazioni sensibili (come nomi e password).

Per utilizzare la distribuzione della pipeline, l’Adobe presuppone che tu sia:

- Un integratore di sistemi esperto con un&#39;eccellente conoscenza delle opzioni di configurazione di Adobe Commerce.
- Gestione di un sito Commerce di grandi dimensioni (migliaia di SKU (Stock-Keeping Unit)) per ridurre al minimo i tempi di inattività del sito di produzione.
- Conoscenza della programmazione PHP.
- Esperienza con i metodi di controllo del codice sorgente.
- Il codice si trova in un archivio del controllo del codice sorgente. In questa guida, si presume che si stia utilizzando un archivio basato su Git.

### Riduzione dei tempi di inattività

Quando si distribuiscono risorse statiche e si compila il codice in un computer separato dal sistema di produzione, si riducono al minimo i tempi di inattività. I tempi di inattività del sistema di produzione sono limitati al tempo necessario per trasferire i file statici e il codice compilato sul server.

## Sistemi di distribuzione

I termini seguenti vengono utilizzati per descrivere i sistemi coinvolti nella distribuzione.

- **Sistema di sviluppo**: computer su cui gli sviluppatori lavorano per personalizzare il codice e installare estensioni, temi e pacchetti di linguaggio da Commerce Marketplace. Inoltre, puoi apportare tutte le modifiche di configurazione al sistema di sviluppo. Puoi avere molti sistemi di sviluppo.

- **Genera sistema**- Un sistema in cui vengono distribuite le risorse statiche e viene compilato il codice per il sistema di produzione. Poiché queste risorse vengono create su un sistema non in produzione, i tempi di inattività del sistema di produzione vengono ridotti al minimo.

   Non è necessario che nel sistema di build sia installato Commerce. È necessario solo il codice Commerce, ma non è richiesta alcuna connessione al database. Inoltre, non è necessario che il sistema di build sia un server fisicamente separato.

- **Sistema di staging**—_Facoltativo_. Facoltativamente, puoi impostare un sistema di staging da utilizzare per il test finale di tutto il codice integrato, incluso User Acceptance Testing (UAT). Impostare un sistema di gestione temporanea nello stesso modo in cui si imposta un sistema di produzione. Ad eccezione del fatto che la gestione temporanea non è il tuo negozio live e non elabora gli ordini dei clienti, è identica alla produzione.

- **Sistema di produzione**- Il vostro negozio live. È necessario apportare modifiche di configurazione dirette minime qui, e sicuramente nulla che non sia stato testato su un’istanza di staging. Se possibile, apporta modifiche alla configurazione con [Patch dati](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) che sono stati testati in un’istanza di staging/sviluppo.

## Altri metodi di distribuzione

Facoltativamente, puoi utilizzare altri metodi di distribuzione, tra cui:

- Copia sicura con SCP o rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- Il [Strumento di distribuzione](https://deployer.org/)

## Gestire la configurazione

Modellazione dopo [fattore 3 nella progettazione di app a 12 fattori](https://12factor.net/config), Commerce ora memorizza la configurazione per ciascun sistema nel sistema stesso. (Le impostazioni di configurazione di sviluppo sono memorizzate nel sistema di sviluppo, le impostazioni di produzione nel sistema di produzione.)

Dell offre un modo per sincronizzare la configurazione dei sistemi:

- **Configurazione condivisa**- Impostazioni che non sono specifiche del sistema né sensibili.

   Le impostazioni condivise sono impostazioni che desideri siano coerenti nei sistemi di sviluppo e produzione. Imposta la configurazione condivisa nell’amministratore nel tuo sviluppo (o in Adobe Commerce nell’infrastruttura cloud) _integrazione_).

   Il file di configurazione condiviso, `app/etc/config.php`, devono essere inclusi nel controllo del codice sorgente in modo da poter essere condivisi tra i sistemi di sviluppo, generazione e produzione.

- **Configurazione specifica del sistema**- Impostazioni che variano in base al sistema, ad esempio i nomi host e le porte dei motori di ricerca.

- **Configurazione sensibile**- Impostazioni che devono essere _non_ essere inclusi nel controllo del codice sorgente perché espongono informazioni personali (PII, personally identifiable information) o impostazioni quali chiavi API o password.

   Il file di configurazione specifico del sistema, `app/etc/env.php`, devono _non_ essere inclusi nel controllo del codice sorgente o condivisi in altro modo tra sistemi. Invece, utilizza [`magento config:set` e `magento:sensitive:set` comandi](../cli/set-configuration-values.md) per fornire i valori per tali impostazioni nel sistema di produzione.

>[!INFO]
>
>Questi nuovi metodi per gestire la configurazione sono facoltativi. Non è necessario, ma si consiglia vivamente di usarli.

Nella maggior parte dei casi, le opzioni di configurazione impostate nella configurazione condivisa, specifica del sistema o sensibile non possono essere modificate nell’amministratore. Questo consente di mantenere le impostazioni coerenti in tutti i sistemi. (Facoltativamente, è possibile utilizzare il [`magento config:set` comando](../cli/set-configuration-values.md) senza `--lock` per configurare le impostazioni modificabili in Admin.)

Ogni opzione di configurazione di Commerce ha un _percorso di configurazione_. Per impostare un valore per un&#39;opzione di configurazione, è possibile utilizzare un comando CLI o una variabile di ambiente per impostare il valore per il percorso di configurazione in un sistema specifico.
