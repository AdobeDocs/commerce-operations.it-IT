---
title: Best practice generali di sviluppo
description: Scopri le best practice generali per lo sviluppo di progetti Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Best practice generali di sviluppo per Adobe Commerce

Questo argomento descrive la linea di base per un processo di sviluppo Adobe Commerce efficiente. Descrive i processi fondamentali, i principi di codifica e i principi di progettazione delle applicazioni per guidare gli sviluppatori.

>[!NOTE]
>
>Gli architetti tecnici Adobi utilizzano queste best practice come riferimento durante gli impegni che coinvolgono lo sviluppo.

Queste best practice sono state sviluppate sulla base di anni di esperienza nello sviluppo e nella distribuzione di progetti Commerce. L’Adobe consiglia di seguire queste best practice nelle iniziative tecniche e di migliorare i processi e il codice esistenti per allinearli.

## Convenzioni testo

Le parole chiave &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHALL&quot;, &quot;SHALL NOT&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;RECOMMENDATIONS&quot;, &quot;MAY&quot; e &quot;OPTIONAL&quot; in questo argomento devono essere interpretate come descritto in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Processo

1. Prima di avviare le attività del progetto, DEVE essere concordata una metodologia di progetto definita. Può essere Scrum, Waterfall, o qualsiasi altra metodologia o combinazione di metodologie, purché sia definita.
1. LO SVILUPPO NON DEVE INIZIARE FINCHÉ non sarà disponibile per il team di sviluppo una strategia di ramificazione per il sistema di controllo delle versioni.
1. LO SVILUPPO NON DEVE INIZIARE FINCHÉ non siano state approvate le specifiche tecniche, approvate le storie degli utenti e i casi d’uso e il team di sviluppo non avrà avuto a disposizione l’approvazione dei casi di test.
1. LO SVILUPPO NON DEVE INIZIARE finché non sia disponibile almeno un ambiente di sviluppo e di controllo qualità.
1. I requisiti specifici del progetto obbligatori per l&#39;avvio dello sviluppo possono essere documentati in una _Definizione di Pronto_.
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
1. Tutto il codice deve essere conforme alla [Guida all&#39;architettura di Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. Tutto il codice deve rispettare i [Standard di codifica Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/).
1. Tutto il codice deve rispettare le [linee guida tecniche di Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. Tutto il codice DEVE implementare le [Best practice per Adobe Commerce](../phases.md), se applicabili.
1. Tutto il codice DEVE rispettare gli standard [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/).
1. Ove possibile, si consiglia di prendere in considerazione [Visioni tecniche di Adobe Commerce](https://developer.adobe.com/commerce/php/architecture/technical-vision/).
1. Tutte le integrazioni con sistemi esterni DEVONO disporre di test di integrazione che convalidano il processo aziendale.
1. Tutti i moduli DEVONO avere copertura di test. Cosa verificare esattamente DEVE essere determinato dal team di sviluppo in collaborazione con l’architetto tecnico o lo sviluppatore principale. Tale determinazione DOVREBBE basarsi su misure qualitative e non su misure quantitative; una percentuale elevata di copertura del codice non è un indicatore di successo né implica un&#39;elevata qualità del codice. Determinare piuttosto il rischio di non coprire una parte del codice valutando la probabilità e la gravità delle regressioni in tale parte del programma.

## Controllo delle versioni

Le versioni del modulo DEVONO rispettare lo standard [Controllo delle versioni semantiche 2.0.0](https://semver.org/).
Le dipendenze nella base di codice di Adobe Commerce DEVONO seguire le [linee guida sulle dipendenze della versione del modulo](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## CONTROLLO DELLE REVISIONI

I commit DEVONO essere accompagnati da messaggi di commit significativi.

## Sicurezza

1. [FUNZIONI non sicure](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) NON DEVONO essere utilizzate.
1. È necessario applicare [strategie di prevenzione XSS](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/).
1. È necessario applicare [Criteri di sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/).
1. Le nuove istanze di Adobe Commerce DEVONO essere consegnate all’ultima versione di sicurezza di una versione che non ha ancora raggiunto la data di &quot;Fine delle correzioni di sicurezza&quot;. Consulta [Adobe Commerce Software Lifecycle Policy](../../../release/lifecycle-policy.md).
