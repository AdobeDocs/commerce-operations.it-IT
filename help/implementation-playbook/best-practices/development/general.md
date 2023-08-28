---
title: Best practice generali di sviluppo
description: Scopri le best practice generali per lo sviluppo di progetti Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Best practice generali di sviluppo per Adobe Commerce

Questo argomento descrive la linea di base per un processo di sviluppo Adobe Commerce efficiente. Descrive i processi fondamentali, i principi di codifica e i principi di progettazione delle applicazioni per guidare gli sviluppatori.

>[!NOTE]
>
>Gli architetti tecnici Adobi utilizzano queste best practice come riferimento durante gli impegni che coinvolgono lo sviluppo.

Queste best practice sono state sviluppate sulla base di anni di esperienza nello sviluppo e nella realizzazione di progetti Commerce. L’Adobe consiglia di seguire queste best practice nelle iniziative tecniche e di migliorare i processi e il codice esistenti per allinearli.

## Convenzioni testo

Le parole chiave &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHALL&quot;, &quot;SHALL NOT&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;RECOMMENDATIONS&quot;, &quot;MAY&quot; e &quot;OPTIONAL&quot; in questa variabile devono essere interpretate come descritto in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Processo

1. Prima di avviare le attività del progetto, DEVE essere concordata una metodologia di progetto definita. Può essere Scrum, Waterfall, o qualsiasi altra metodologia o combinazione di metodologie, purché sia definita.
1. LO SVILUPPO NON DEVE INIZIARE FINCHÉ non sarà disponibile per il team di sviluppo una strategia di ramificazione per il sistema di controllo delle versioni.
1. LO SVILUPPO NON DEVE INIZIARE FINCHÉ non siano state approvate le specifiche tecniche, approvate le storie degli utenti e i casi d’uso e il team di sviluppo non avrà avuto a disposizione l’approvazione dei casi di test.
1. LO SVILUPPO NON DEVE INIZIARE finché non sia disponibile almeno un ambiente di sviluppo e di controllo qualità.
1. I requisiti specifici del progetto obbligatori per l&#39;avvio dello sviluppo possono essere documentati in un _Definizione di Pronto_.
1. L’approvazione DEVE essere effettuata da un rappresentante del cliente autorizzato a firmare i risultati finali del progetto.
1. Nelle metodologie di progetto Agile, requisiti aggiuntivi POSSONO seguire l’approvazione. Questi requisiti DEVONO essere trattati come nuovi requisiti e DEVONO essere acquisiti, progettati e pianificati di conseguenza.
1. Tutti gli sviluppi DEVONO essere testati dal punto di vista funzionale dallo sviluppatore prima dell’invio.
1. Tutti gli sviluppi DEVONO superare test automatizzati prima di essere inviati per la revisione del codice. PUÒ essere configurato come processo automatizzato dopo la creazione della richiesta di pull.
1. Tutti gli sviluppi DEVONO superare l&#39;esame manuale del codice da parte di un architetto tecnico o di un lead develeloper prima che venga inviato per il controllo qualità.
1. Tutti gli sviluppi DEVONO superare il controllo qualità prima della consegna al cliente.
1. I requisiti specifici del progetto che sono obbligatori per la consegna POSSONO essere documentati in una &quot;Definizione di completato&quot;.

## Ambiente

1. Tutti gli sviluppatori DEVONO utilizzare lo stesso IDE. PhpStorm è l’IDE consigliato per lo sviluppo Adobe Commerce.
1. Tutti gli sviluppatori DEVONO sviluppare e testare utilizzando lo stesso stack di tecnologia utilizzato sui (futuri) server di produzione. Le versioni del software in questo stack di tecnologia DEVONO corrispondere alla versione principale e alla versione secondaria del software installato sui server di produzione. Consulta [requisiti di sistema](../../../installation/system-requirements.md) per informazioni dettagliate sullo stack tecnologico tipico di Adobe Commerce.
1. L’amministratore di sistema o l’architetto tecnico PUÒ fornire al team un ambiente di sviluppo locale gestito a livello centrale per garantire e promuovere ambienti locali uguali e aggiornati.
1. Sviluppatori e ingegneri QA DEVONO avere accesso alla riga di comando, al database e ai file di registro dell’ambiente QA. Potrebbe essere necessaria una connessione VPN.

## Norme di codifica

1. Tutto il codice DEVE seguire le convenzioni degli standard di architettura, metodologia e codifica. La creatività è desiderata nella funzione, non nella forma.
1. Tutto il codice DEVE essere in linea con [Guida all’architettura di Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. Tutto il codice DEVE rispettare il [Standard di codifica Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/).
1. Tutto il codice DEVE rispettare il [Linee guida tecniche di Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. Tutto il codice DEVE implementare [Best practice per Adobe Commerce](../phases.md), se applicabile.
1. Tutto il codice DEVE rispettare il [Standard PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/).
1. Ove possibile, si RACCOMANDA di [Visioni tecniche di Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/technical-vision/) in considerazione.
1. Tutte le integrazioni con sistemi esterni DEVONO disporre di test di integrazione che convalidano il processo aziendale.
1. Tutti i moduli DEVONO avere copertura di test. Cosa verificare esattamente DEVE essere determinato dal team di sviluppo in collaborazione con l’architetto tecnico o lo sviluppatore principale. Tale determinazione DOVREBBE basarsi su misure qualitative e non su misure quantitative; una percentuale elevata di copertura del codice non è un indicatore di successo né implica un&#39;elevata qualità del codice. Determinare piuttosto il rischio di non coprire una parte del codice valutando la probabilità e la gravità delle regressioni in tale parte del programma.

## Controllo delle versioni

Le versioni del modulo DEVONO rispettare la [Controllo delle versioni semantiche 2.0.0 standard](https://semver.org/).
Le dipendenze dalla base di codice di Adobe Commerce DEVONO seguire la [Linee guida sulle dipendenze delle versioni dei moduli](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## CONTROLLO DELLE REVISIONI

I commit DEVONO essere accompagnati da messaggi di commit significativi.

## Sicurezza

1. [Funzioni non sicure](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) NON DEVE essere utilizzato.
1. [Strategie di prevenzione XSS](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) DEVE essere applicato.
1. [Informativa sulla sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) DEVE essere applicato.
1. Le nuove istanze di Adobe Commerce DEVONO essere consegnate all’ultima versione di sicurezza di una versione che non ha ancora raggiunto la data di &quot;Fine delle correzioni di sicurezza&quot;. Consulta [Criteri del ciclo di vita del software Adobe Commerce](../../../release/lifecycle-policy.md).
