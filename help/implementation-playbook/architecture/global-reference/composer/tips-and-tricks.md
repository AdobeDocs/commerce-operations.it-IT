---
title: Suggerimenti e trucchi per il compositore
description: Scopri le attività di sviluppo comuni del Compositore e le linee guida per risolvere rapidamente i problemi.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Suggerimenti e trucchi per il compositore

È possibile che si verifichino problemi durante lo sviluppo di moduli Adobe Commerce con Composer. Queste best practice descrivono alcune attività comuni per semplificare lo sviluppo e aiutarti a risolvere rapidamente i problemi.

>[!NOTE]
>
>Queste linee guida si applicano principalmente a [progetti GRA (Global Reference Architecture)](../overview.md).

## Compositore velocità

Installa [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) per velocizzare Composer con download asincroni dei pacchetti.

```bash
composer global require hirak/prestissimo
```

In caso di problemi, disinstallare `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## Risoluzione di problemi vaghi di controllo delle versioni

Il compositore a volte si blocca a causa delle versioni dei pacchetti. Potresti visualizzare messaggi relativi a versioni non compatibili, anche in caso contrario. Prima di eseguire il debug dei problemi di compatibilità, provare a reimpostare Compositore:

1. Cancellare la cache del Compositore.

   ```bash
   composer clearcache
   ```

1. Rimuovi il file `composer.lock` per tutti i pacchetti.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Reinstalla i pacchetti Composer.

   ```bash
   composer install
   ```

>[!TIP]
>
>Questi passaggi aggiornano tutti i pacchetti alla versione più recente disponibile. Ripristina il file `composer.lock` da Git per annullare questi aggiornamenti.

## Verificare la presenza di eventuali aggiornamenti nei pacchetti client

1. Individuare i pacchetti che potrebbero non essere aggiornati.

   ```bash
   composer outdated
   ```

1. Filtra utilizzando i caratteri jolly e/o l&#39;opzione `--minor-only` per ignorare gli aggiornamenti incompatibili con le versioni precedenti:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Verificare se è installato un modulo

Visualizza i dettagli di tutti i pacchetti installati in un ramo Git.

```bash
composer info
```

Esegui `composer install` dopo aver cambiato rami Git e prima di eseguire `composer info`. In caso contrario, Composer mostra i dettagli relativi al ramo precedente estratto.

>[!TIP]
>
>Per filtrare o eseguire ricerche, utilizzare uno dei seguenti comandi.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Scopri perché è installato un pacchetto (versione specifica di un pacchetto)

A volte, Composer installa l’ultima versione disponibile di un pacchetto a causa di una stretta dipendenza in un altro pacchetto.

Scopri se esiste una dipendenza rigida in un altro pacchetto.

```bash
composer why client/module-example
```

Se nei risultati viene visualizzato un elenco di metapackages o di un altro pacchetto non esplicitamente richiesto, eseguire il comando su tale pacchetto:

```bash
composer why example/metapackage
```

## Informazioni sul motivo per cui un pacchetto non è installato

A volte, Composer non installa un pacchetto perché è in conflitto con un altro pacchetto, un altro pacchetto lo sostituisce o non è stato definito come dipendenza.

Scopri perché un pacchetto non è installato.

```bash
composer why-not client/module-example
```

## Ospitare un archivio Compositore privato

Se hai bisogno di un repository Composer privato, utilizza [Private Packagist](https://packagist.com/) o [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). Non utilizzare [Satis](https://github.com/composer/satis).

- **Il Packagist privato** è sicuro, costa circa 600 $ all&#39;anno con tre utenti amministratori ed è in hosting.

- **JFrog Artifactory** parte da $1.176 USD all&#39;anno. Non viene comunemente utilizzato come Packagist, ma supporta più lingue rispetto a PHP.

- **Satis** non dispone di protezione incorporata, nessuna automazione e richiede un hosting aggiuntivo. È gratuito solo se anche il tuo tempo è libero.

## Pacchetti di controllo delle versioni

Utilizzare [Controllo delle versioni semantiche 2.0.0](https://semver.org/spec/v2.0.0.html) come descritto nello schema di controllo delle versioni [Adobe Commerce](https://developer.adobe.com/commerce/php/development/versioning/). Non reinventare la ruota.

Per le dipendenze dei moduli Adobe Commerce, segui la documentazione [dipendenze delle versioni del modulo](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

Non utilizzare la definizione della versione all&#39;interno del file `composer.json`. Utilizza invece i tag Git per le versioni. Consulta [Versioni e vincoli del Compositore](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Dove inserire i moduli in un file di archivio e non tramite Compositore

Crea un archivio Git per i moduli in un archivio e ospitali autonomamente. Ogni modulo di Adobe Commerce ha un file `composer.json`. Dopo averlo ospitato in Git e sincronizzato con Private Packagist, puoi installarlo con Composer.

Quando ricevi una nuova versione del pacchetto, carica il codice su Git, assegna i tag desiderati e installa la nuova versione con Composer.
