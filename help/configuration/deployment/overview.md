---
title: Panoramica sulla distribuzione
description: Informazioni sulle strategie di distribuzione per l’applicazione Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---


# Panoramica sulla distribuzione

Questi argomenti trattano il processo di distribuzione dell’applicazione Commerce a un sito di produzione per Adobe Commerce versione 2.2 e successive. Adobe consiglia questo metodo di distribuzione per tutti coloro che dispongono di un sito di grandi dimensioni e che non desiderano riscontrare tempi di inattività durante l&#39;implementazione.

Se distribuisci Commerce su un singolo computer e puoi tollerare alcuni tempi di inattività durante l’implementazione, consulta [Distribuzione a macchina singola](../deployment/single-machine.md).

## Distribuzione di pipeline

Con Commerce versione 2.2, Adobe introdotto _distribuzione della pipeline_ come nuovo modo per implementare in produzione con tempi di inattività minimi. Questo processo di distribuzione si verifica su diversi sistemi e consente di mantenere configurazioni coerenti per tutti i sistemi di distribuzione della pipeline. Si tratta di un modello semplice ma potente che consente di separare le impostazioni di configurazione ordinarie da quelle specifiche del sistema (come host e porta) o da quelle sensibili (come nomi e password).

Per utilizzare la distribuzione della pipeline, l’Adobe presuppone che:

- Integratore di sistema esperto con un&#39;eccellente conoscenza delle opzioni di configurazione di Adobe Commerce.
- Gestione di un sito Commerce di grandi dimensioni (migliaia di unità di gestione delle scorte (SKU)) e riduzione al minimo dei tempi di inattività del sito di produzione.
- Conoscenza della programmazione PHP.
- Esperienza con i metodi di controllo del codice sorgente.
- Il codice si trova in un archivio di controllo del codice sorgente. In questa guida si presuppone che utilizzi un archivio basato su Git.

### Riduzione dei tempi di inattività

Quando si distribuiscono risorse statiche e si compila il codice su un computer separato dal sistema di produzione, si riducono al minimo i tempi di inattività. Il tempo di inattività del sistema di produzione è limitato al tempo necessario per trasferire i file statici e il codice compilato sul server.

## Sistemi di distribuzione

Utilizziamo i seguenti termini per descrivere i sistemi coinvolti nell&#39;implementazione.

- **Sistema di sviluppo**- Macchina su cui gli sviluppatori lavorano per personalizzare il codice; e installare estensioni, temi e pacchetti linguistici da Commerce Marketplace. Inoltre, puoi apportare tutte le modifiche alla configurazione sul tuo sistema di sviluppo. Si possono avere molti sistemi di sviluppo.

- **Sistema di compilazione**- Un sistema su cui distribuire le risorse statiche e compilare il codice per il sistema di produzione. Poiché si creano queste risorse su un sistema non in produzione, i tempi di inattività del sistema di produzione vengono ridotti al minimo.

   Nel sistema di compilazione non è necessario che sia installato Commerce. È necessario solo il codice Commerce, ma non è necessaria alcuna connessione al database. Inoltre, il sistema di compilazione non deve essere un server fisicamente separato.

- **Sistema di staging**—_Facoltativo_. Facoltativamente, puoi impostare un sistema di staging da utilizzare per il test finale di tutto il codice integrato, incluso il test di accettazione dell’utente (UAT). Impostare un sistema di gestione temporanea nello stesso modo in cui si imposta un sistema di produzione. Eccetto per il fatto che la gestione temporanea non è il tuo Live Store e non elabora gli ordini dei clienti, è identica alla produzione.

- **Sistema di produzione**- Il tuo negozio in diretta. In questo caso è necessario apportare minime modifiche di configurazione diretta e di certo nulla che non sia stato testato su un&#39;istanza di staging. Se possibile, apporta modifiche alla configurazione con [Patch dati](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) che sono stati testati su un’istanza di Staging/Sviluppo.

## Altri metodi di distribuzione

Facoltativamente, puoi utilizzare altri metodi di distribuzione, tra cui:

- Copia protetta con SCP o rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- La [Strumento di distribuzione](https://deployer.org/)

## Gestire la configurazione

Modellazione dopo [fattore 3 nel design dell&#39;app a 12 fattori](https://12factor.net/config), Commerce ora memorizza la configurazione di ogni sistema nel sistema stesso. (Le impostazioni di configurazione dello sviluppo sono memorizzate nel sistema di sviluppo, le impostazioni di produzione sono memorizzate nel sistema di produzione.)

Forniamo un modo per sincronizzare la configurazione dei sistemi:

- **Configurazione condivisa**- Impostazioni che non sono né specifiche del sistema né sensibili.

   Le impostazioni condivise sono impostazioni che devono essere coerenti nei sistemi di sviluppo e produzione. Imposta la configurazione condivisa nell’amministratore nello sviluppo (o nell’infrastruttura cloud di Adobe Commerce) _integrazione_).

   Il file di configurazione condiviso, `app/etc/config.php`, deve essere incluso nel controllo del codice sorgente in modo che possa essere condiviso tra i sistemi di sviluppo, generazione e produzione.

- **Configurazione specifica del sistema**- Impostazioni che variano a seconda del sistema, ad esempio nomi host e porte del motore di ricerca.

- **Configurazione sensibile**- Impostazioni che devono _not_ essere nel controllo del codice sorgente perché espongono informazioni personali identificabili (PII) o impostazioni come chiavi API o password.

   Il file di configurazione specifico del sistema, `app/etc/env.php`, _not_ essere inclusi nel controllo del codice sorgente o altrimenti condivisi tra i sistemi. Invece, utilizza la [`magento config:set` e `magento:sensitive:set` comandi](../cli/set-configuration-values.md) per fornire i valori per tali impostazioni nel sistema di produzione.

>[!INFO]
>
>Questi nuovi metodi per gestire la configurazione sono facoltativi. Non è necessario, ma si consiglia vivamente di utilizzarli.

Nella maggior parte dei casi, le opzioni di configurazione impostate nella configurazione condivisa, specifica del sistema o sensibile non possono essere modificate in Admin. Questo consente di mantenere le impostazioni coerenti in tutti i sistemi. (È possibile utilizzare facoltativamente il [`magento config:set` command](../cli/set-configuration-values.md) senza `--lock` per configurare le impostazioni modificabili in Admin.)

Ogni opzione di configurazione Commerce ha un _percorso di configurazione_. Per impostare un valore per un&#39;opzione di configurazione, è possibile utilizzare un comando CLI o una variabile di ambiente per impostare il valore per quel percorso di configurazione su un sistema specifico.
