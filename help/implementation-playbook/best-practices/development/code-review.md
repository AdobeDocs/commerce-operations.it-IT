---
title: Best practice per la revisione del codice
description: Scopri le best practice per la revisione del codice nella fase di sviluppo dei progetti Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 1ef78bce-2e69-4c95-a26e-1bf7196ce546
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---

# Best practice per la revisione del codice per Adobe Commerce

L’obiettivo principale della revisione del codice è quello di verificare che le funzionalità implementate soddisfino i requisiti in modo ottimale dal punto di vista delle prestazioni, dell’architettura e della sicurezza.

Inoltre, la revisione del codice ha lo scopo di garantire che il codice soddisfi le best practice di sviluppo di Adobe Commerce, sia facile da comprendere e mantenere e rispetti gli standard di codifica. La maggior parte degli standard di codifica dovrebbe essere controllata automaticamente con gli strumenti appropriati.

## Processo di revisione del codice consigliato

Ad alto livello, il processo di revisione del codice dovrebbe consistere nelle seguenti fasi:

1. Estrai ramo funzionalità nell’ambiente di sviluppo locale.
1. Se è trascorso un po’ di tempo dall’invio del codice per la revisione, unisci le ultime modifiche dal ramo di destinazione (in genere un ramo QA) e invia gli aggiornamenti al ramo delle funzioni remoto (se presenti).
1. Esegui una revisione di alto livello per verificare che il codice implementi tutti i requisiti. In caso di discrepanze importanti, contatta lo sviluppatore per chiarimenti.
1. L’esecuzione del codice è facoltativa, ma se hai dubbi sul fatto che il codice funzioni come previsto o se agevola l’efficienza del processo, verifica che la funzionalità implementata funzioni come previsto per gli scenari di utilizzo principali. In caso di problemi gravi, interrompi il processo di revisione e riapri il ticket con i commenti appropriati.
1. Esegui una revisione completa per verificare che il codice implementi tutti i requisiti. In caso di problemi, aggiungi i commenti appropriati alla richiesta di pull e riapri il ticket.
1. Se tutto sembra a posto, unisci la richiesta di pull (o trasmettila al livello successivo di revisione del codice, se ne è stata stabilita una).

Inoltre, considera i seguenti punti quando implementi i processi di revisione del codice:

- La revisione del codice è uno strumento principale per la comunicazione e il trasferimento di conoscenze all’interno di un team. Anche se una richiesta di pull non contiene problemi importanti e implementa la logica di business richiesta, puoi utilizzarla come opportunità per suggerire ulteriori miglioramenti dopo l’unione.

- In media, la revisione del codice non dovrebbe richiedere più del 10-20% dello sforzo di sviluppo. Ciò presuppone che il team di sviluppo sia composto da ingegneri esperti che lavorano bene insieme. Se la revisione del codice richiede più tempo, può influire sul budget e sulla sequenza temporale del progetto.

- Risolvi i problemi che richiedono uno sforzo eccessivo per le revisioni del codice identificando la causa principale. Di solito, è perché i requisiti sono scarsamente tradotti in ticket di sviluppo (a causa di problemi di comunicazione, storie di utenti poveri) o è un problema di coaching. Nel primo caso, la mitigazione consigliata è quella di assicurarsi che i ticket abbiano informazioni sufficienti per consentire ai membri del gruppo di soddisfare in modo efficiente i requisiti. Nel secondo caso, potrebbe essere necessario modificare la struttura del team per includere ingegneri più esperti o ottenere l’approvazione di un tutoraggio e coaching esterni.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Cosa cercare nella revisione del codice

### Stile

Lo stile può essere testato automaticamente eseguendo l&#39;ispezione PhpStorm (vedi sotto).

Assicurati di configurare [PHPMD e PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) e di eseguire lo strumento [Coding Standard](https://github.com/magento/magento-coding-standard) dalla CLI (anche di seguito). Esiste una sovrapposizione, ma entrambi dispongono di test univoci.

### Convenzione e struttura

Le revisioni per convenzione e struttura vengono eseguite manualmente.

- La funzionalità di classe è limitata a una singola responsabilità?
- La struttura della directory ha senso?
- È funzionalità eseguita al livello giusto (server, client, CSS, JS, database, framework, infrastruttura).
- Il controllo delle versioni è corretto?
- Il codice non sembra convenzionale o cerca di risolvere un problema nel modo sbagliato?
- La convenzione di denominazione per il nome del modulo, il nome del pacchetto e il nome dell’archivio viene applicata correttamente?
- Verifica che gli stili CSS globali siano applicati correttamente e non vengano utilizzati in modo eccessivo.

### Completezza

Le verifiche della completezza vengono eseguite manualmente.

- Il codice può essere abilitato o disabilitato dalla configurazione e tutto il codice necessario si comporta come previsto?
- È presente tutta la configurazione menzionata nel ticket? Controlla l’ambito, il tipo di dati, la convalida, la traduzione e i valori predefiniti.
- La configurazione viene sempre recuperata al livello più basso possibile (livello di visualizzazione archivio, livello sito Web o livello globale)? Il recupero della configurazione deve corrispondere alla definizione dell&#39;ambito nel file `system.xml`.
- Sono coperti tutti i percorsi nel diagramma di flusso delle specifiche tecniche? Sono contemplate tutte le altre specifiche tecniche?
- Per la nuova funzionalità sono stati definiti degli ACL?
- PhpDocs è chiaro? I messaggi di commit sono chiari?
- Esiste un codice fuori commento o viene visualizzato il codice di debug?

### Prestazioni

Le verifiche delle prestazioni vengono eseguite manualmente, il che può essere facilitato dall’esecuzione del codice in caso di dubbi.

- Le query vengono eseguite in loop? Questo ciclo può essere esterno ai file modificati.
- È possibile individuare qualsiasi attributo `cachable="false"`? Sono applicate correttamente?

### Sicurezza

Le verifiche sulla sicurezza vengono effettuate manualmente, e possono essere supportate dalla ricerca di testo. Parte del controllo di sicurezza è effettuata tramite test automatizzati.

- Le eccezioni vengono registrate quando necessario? Vengono utilizzati i giusti tipi di eccezioni?
- È possibile evitare `around` plug-in?
- I plug-in restituiscono i tipi di dati corretti?
- È possibile trovare query SQL non elaborate che devono essere create utilizzando il livello di astrazione del database?
- Esistono nuovi tipi di dati esposti a qualsiasi tipo di utente, amministratore o front-end? L&#39;esposizione è un rischio per la sicurezza?
- I dati generati dall&#39;utente vengono convalidati? Tutto ciò che proviene dal browser viene considerato generato dall’utente, inclusi i valori dei cookie e le intestazioni del server.

### Privacy e RGPD

Le revisioni per privacy e [RGPD](../../../security-and-compliance/privacy/gdpr.md) vengono eseguite manualmente.

- Il codice gestisce i dati o le e-mail dei clienti? Faccia particolare attenzione.
- Se questo codice può essere eseguito in un ciclo continuo, può causare la perdita di dati del cliente da un ciclo continuo all&#39;altro?
- Gli indicatori di un rischio sono le importazioni, i processi cron, le e-mail transazionali e i gestori di code batch.
- Garantire l&#39;isolamento dei dati utente nei loop. Adobe consiglia di utilizzare le fabbriche o i repository per creare modelli nel ciclo del ciclo, che non sono accessibili al di fuori del ciclo.

### Tutoraggio

Le revisioni per il tutoraggio vengono effettuate manualmente.

- Cercate luoghi in cui condividere le conoscenze con l&#39;obiettivo di formare il team.
- Se il tuo commento è puramente educativo, ma non critico per soddisfare gli standard, indica che non è obbligatorio per l&#39;autore risolverlo.
- Se vedi qualcosa di bello, informa lo sviluppatore, soprattutto quando ha affrontato uno dei tuoi commenti in modo eccellente. Le revisioni del codice spesso si concentrano sugli errori, ma dovrebbero offrire incoraggiamento e apprezzamento anche per le buone pratiche. A volte è ancora più utile, in termini di mentoring, dire a uno sviluppatore cosa ha fatto bene che dire cosa ha sbagliato.

## Automazione

Gli sviluppatori possono utilizzare l’automazione per rivedere la compilazione DI, lo schema del database, la convalida del compositore e la conformità con gli standard di codifica:

- Compilazione DI: eseguire i seguenti comandi CLI per verificare se il codice può essere compilato senza problemi.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Schema di database `whitelist.json`: eseguire il comando CLI seguente e verificare che il file `db_schema_whitelist.json` non sia stato aggiunto o modificato.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer validate - Convalida il file `composer.json` eseguendo il seguente comando CLI nella directory che contiene il file `composer.json`.

  ```bash
  composer validate
  ```

- Standard di codifica: consente di installare ed eseguire lo strumento Standard di codifica e di eseguirlo in base al modulo. Nel file seguente viene illustrato come consentire l&#39;esecuzione in qualsiasi posizione digitando `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- Ispezione PhpStorm

- Rilevatore di copia/incolla PHP PhpStorm
