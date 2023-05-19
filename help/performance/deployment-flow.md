---
title: Flusso di implementazione
description: Scopri i passaggi necessari per distribuire Adobe Commerce o Magenti Open Source in un ambiente di produzione.
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Flusso di distribuzione

Il [!DNL Commerce] il flusso di distribuzione di produzione consente a un archivio di raggiungere le massime prestazioni.

## Installare le dipendenze

Il `composer.json` e `composer.lock` file gestire [!DNL Commerce] e installare la versione appropriata per ciascun pacchetto. È necessario installare le dipendenze prima di [istruzioni per l’iniezione della dipendenza di pre-elaborazione](#preprocess-dependency-injection-instructions) se prevedi di aggiornare [autoloader](#update-the-autoloader).

Per installare [!DNL Commerce] dipendenze:

```bash
composer install --no-dev
```

## Istruzioni per l’iniezione della dipendenza di pre-elaborazione

Quando pre-elabora e compila le istruzioni di iniezione di dipendenza (DI), Magento:

* Legge ed elabora tutte le configurazioni presenti
* Analizza le dipendenze tra le classi
* Crea file generati automaticamente (inclusi proxy, factory e così via)
* Memorizza i dati e la configurazione compilati in una cache che consente di risparmiare fino al 25% di tempo sull’elaborazione delle richieste

Per pre-elaborare e compilare le istruzioni ID:

```bash
bin/magento setup:di:compile
```

## Aggiornare il caricatore automatico

Al termine della compilazione, confermare che [APCu è abilitato](../performance/software.md#php-settings) e aggiornare l&#39;autoloader:

Per aggiornare il caricatore automatico:

>[!INFO]
>
>Il `-o` L&#39;opzione converte il caricamento automatico PSR-0/4 in classmap per ottenere un autoloader più veloce. Il `--apcu` L’opzione utilizza APCu per memorizzare in cache le classi trovate/non trovate.

```bash
composer dump-autoload -o --apcu
```

Se si prevede di aggiornare il caricatore automatico, è necessario eseguire i seguenti comandi per:

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

## Distribuire contenuto statico

La distribuzione di contenuto statico causa [!DNL Commerce] per eseguire le azioni seguenti:

* Analizzare tutte le risorse statiche
* Eseguire l’unione, la riduzione a icona e il raggruppamento dei contenuti
* Lettura ed elaborazione dei dati dei temi
* Analisi del fallback del tema
* Memorizza tutti i contenuti elaborati e materializzati in una cartella specifica per un ulteriore utilizzo

Se il contenuto statico non viene distribuito, [!DNL Commerce] esegue al volo tutte le operazioni elencate, determinando un aumento significativo dei tempi di risposta.

È possibile utilizzare diverse opzioni per personalizzare le operazioni di distribuzione in base alle dimensioni del negozio e alle esigenze di evasione. La più comune è la strategia di installazione compatta. Consulta [Strategie di distribuzione dei file statici](../configuration/cli/static-view-file-strategy.md)

Per distribuire il contenuto statico:

```bash
bin/magento setup:static-content:deploy
```

Questo comando consente a Composer di ricreare la mappatura ai file di progetto in modo che vengano caricati più rapidamente.

## Imposta modalità di produzione

>[!INFO]
>
>L’impostazione della modalità di produzione viene eseguita automaticamente `setup:di:compile` e `setup:static-content:deploy`.

Infine, devi mettere il negozio in modalità Produzione. La modalità di produzione è ottimizzata in modo specifico per garantire le massime prestazioni del punto vendita. Disattiva inoltre tutte le funzioni specifiche per gli sviluppatori. Questa operazione può essere eseguita nel `.htaccess` o `nginx.conf` file:

`SetEnv MAGE_MODE production`

È inoltre possibile distribuire contenuto statico, compilare il contenuto e impostare la modalità in un comando CLI:

```bash
bin/magento deploy:mode:set production
```

Il comando viene eseguito in background e non consente di impostare opzioni aggiuntive per ogni passaggio specifico.

## Azioni aggiuntive prima del lancio

Questi passaggi sono consigliati, ma non sono obbligatori. Puoi eseguirli immediatamente prima di avviare il negozio in modalità di produzione. L&#39;elenco include:

* Reindicizza i dati per evitare la presenza di dati incoerenti negli indici.
* Svuota la cache per assicurarti di non lasciare dati obsoleti o errati nella cache.
* Riscaldamento della cache, che richiama in anticipo le pagine più popolari o critiche dello store, in modo che la cache per esse venga generata e memorizzata. Questa operazione può essere eseguita con qualsiasi crawler Internet o manualmente, se si dispone di un piccolo negozio.
