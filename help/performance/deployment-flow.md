---
title: Flusso di distribuzione
description: 'Scopri i passaggi necessari per distribuire Adobe Commerce o Magenti Open Source in un ambiente di produzione. '
source-git-commit: 9ab52374e031bd2b0a846dd5f47c89ff788dcafa
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Flusso di distribuzione

La [!DNL Commerce] il flusso di distribuzione della produzione aiuta un negozio a raggiungere le massime prestazioni.

## Installare le dipendenze

La `composer.json` e `composer.lock` gestione file [!DNL Commerce] dipendenze e installare la versione appropriata per ciascun pacchetto. È necessario installare le dipendenze prima di [istruzioni per l&#39;iniezione di dipendenza di preelaborazione](#preprocess-dependency-injection-instructions) se si prevede di aggiornare [caricatore automatico](#update-the-autoloader).

Per installare [!DNL Commerce] dipendenze:

```bash
composer install --no-dev
```

## Istruzioni per l&#39;iniezione di dipendenza del processo preliminare

Quando si preelaborano e si compilano le istruzioni di iniezione di dipendenza (DI), Magento:

* Legge ed elabora tutte le configurazioni presenti
* Analizza le dipendenze tra le classi
* Crea file generati automaticamente (inclusi proxy, fabbriche, ecc.)
* Memorizza i dati e la configurazione compilati in una cache che consente di risparmiare fino al 25% di tempo sull&#39;elaborazione delle richieste

Per preelaborare e compilare le istruzioni ID:

```bash
bin/magento setup:di:compile
```

## Aggiornare il caricatore automatico

Al termine della compilazione, confermare che [APCu abilitato](https://devdocs.magento.com/guides/v2.4/performance-best-practices/software.html#php-settings) e aggiorna il caricatore automatico:

Per aggiornare il caricatore automatico:

>[!INFO]
>
>La `-o` l&#39;opzione converte l&#39;autoloading PSR-0/4 in classmap per ottenere un autoloader più veloce. La `--apcu` l&#39;opzione utilizza APCu per memorizzare in cache le classi trovate/non trovate.

```bash
composer dump-autoload -o --apcu
```

Se si prevede di aggiornare l&#39;autoloader, è necessario eseguire i seguenti comandi nell&#39;ordine seguente:

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Distribuzione di contenuto statico

Distribuzione di cause di contenuto statico [!DNL Commerce] per eseguire le azioni seguenti:

* Analizzare tutte le risorse statiche
* Eseguire l’unione, la minimizzazione e il bundle dei contenuti
* Lettura ed elaborazione dei dati dei temi
* Analizzare il fallback del tema
* Archiviare tutti i contenuti elaborati e materializzati in una cartella specifica per un ulteriore utilizzo

Se il contenuto statico non viene distribuito, [!DNL Commerce] esegue al volo tutte le operazioni elencate, con conseguente significativo aumento del tempo di risposta.

È possibile utilizzare una varietà di opzioni per personalizzare le operazioni di distribuzione in base alle dimensioni dello store e alle esigenze di conformità. La più comune è la strategia di implementazione compatta. Vedi [Strategie di distribuzione dei file statici](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-static-deploy-strategies.html)

Per distribuire contenuto statico:

```bash
bin/magento setup:static-content:deploy
```

Questo comando consente a Composer di ricostruire la mappatura ai file di progetto in modo che vengano caricati più velocemente.

## Imposta la modalità di produzione

>[!INFO]
>
>L&#39;impostazione della modalità su produzione viene eseguita automaticamente `setup:di:compile` e `setup:static-content:deploy`.

Infine, è necessario posizionare il negozio in modalità Produzione. La modalità di produzione è ottimizzata in modo specifico per le massime prestazioni dello store. Inoltre, disattiva tutte le funzioni specifiche per gli sviluppatori. Questa operazione può essere eseguita nel `.htaccess` o `nginx.conf` file:

`SetEnv MAGE_MODE production`

È inoltre possibile distribuire contenuto statico, compilare il contenuto e impostare la modalità in un unico comando CLI:

```bash
bin/magento deploy:mode:set production
```

Il comando viene eseguito in background e non consente di impostare opzioni aggiuntive per ogni passaggio specifico.

## Azioni preliminari aggiuntive

Questi passaggi sono consigliati, ma non obbligatori. Puoi eseguirli immediatamente prima di avviare il negozio in modalità di produzione. L’elenco include:

* Reindicizza i dati per evitare la presenza di dati incoerenti negli indici.
* Esegui lo scaricamento della cache per verificare che nella cache non siano presenti dati vecchi o non corretti.
* Riscaldare la cache, che richiama in anticipo le pagine del negozio più popolari o critiche, in modo che la cache per loro sia generata e memorizzata. Questa operazione può essere eseguita con qualsiasi Internet crawler o manualmente, se si dispone di un piccolo negozio.
