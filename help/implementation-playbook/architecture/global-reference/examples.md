---
title: Esempi di architettura di riferimento globale
description: Vedi esempi di gestione del codice per progetti Adobe Commerce su larga scala.
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Esempi di architettura di riferimento globale

In questo argomento vengono descritti i metodi comuni per organizzare una [base di codice per l&#39;architettura di riferimento globale (GRA)](overview.md). Anche se l&#39;opzione [pacchetti separati](#option-1-separate-packages) è preferita, alcune situazioni richiedono una delle altre opzioni descritte di seguito.

## Definizioni

{{$include /help/_includes/gra-definitions.md}}

## Opzione 1: pacchetti separati

Consulta le [Best practice per la configurazione di questo metodo nella struttura del progetto del compositore](composer/project-structure.md).

![Diagramma che illustra l&#39;opzione dei pacchetti separati per l&#39;architettura di riferimento globale](../../../assets/playbooks/gra-separate-packages.png)

Il modo più flessibile per gestire i pacchetti GRA Composer è attraverso i metapackages. I metapacchetti contengono solo un file `composer.json`, che definisce altre dipendenze del pacchetto. Creare metapacchetti utilizzando [archivi Packagist privati](https://packagist.com/).

### Progetto principale `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

Ogni modulo, Language Pack, tema e libreria dispone di un proprio archivio Git. Ogni archivio Git si sincronizza automaticamente con l&#39;archivio del Packagist privato e genera un pacchetto in tale archivio purché nella radice dell&#39;archivio Git sia presente un file `composer.json`.

## Opzioni 2: pacchetti in blocco

Di seguito è riportato un esempio di più moduli all’interno di un singolo pacchetto Compositore.

Un pacchetto bulk può includere solo pacchetti dello stesso tipo. Ad esempio, se disponi di più pacchetti per moduli, temi, Language Pack e librerie di Adobe Commerce, devi creare pacchetti in blocco separati per ciascun tipo.

La struttura del file all’interno della directory del fornitore deve essere simile a quella dell’esempio seguente. Tuttavia, controlla il progetto per vedere cosa deve essere incluso nell’archivio Git):

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

Il file `composer.json` deve essere simile al seguente:

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## Opzione 3: Suddivisione di Git

Questa architettura utilizza quattro archivi Git per memorizzare il codice:

- `core`: contiene l&#39;installazione di base di Adobe Commerce. Viene utilizzato per aggiornare le versioni di Adobe Commerce.
- `GRA`: contiene codice GRA. Tutti i moduli GRA, i Language Pack, i temi delle etichette bianche e le librerie.
- `brand/region`: ogni marchio o area geografica ha il proprio archivio con solo codice specifico per il marchio o l&#39;area geografica.
- `release`: tutte le operazioni precedenti sono state unite in questo archivio Git. Qui sono consentiti solo i commit di unione.

![Diagramma che illustra l&#39;opzione Git divisa per l&#39;architettura di riferimento globale](../../../assets/playbooks/gra-split-git.png)

Per impostare questa opzione:

1. Crea i quattro tipi di archivio in Git. Creare gli archivi `core` e `GRA` una sola volta. Creare un archivio `brand/region` e un archivio `release` per ogni marchio.

   Nomi repository suggeriti:

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (ad esempio `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (ad esempio `m2-release-emea`/`m2-release-adobe`)

1. Creare una directory `release/` ed eseguire quanto segue per creare una cronologia Git condivisa per tutti gli archivi.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. Clonare ogni repository, ad eccezione di `core`, in una directory diversa nel computer.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Installa Adobe Commerce con Composer](../../../installation/composer.md). Rimuovi il file `.gitignore`, aggiungi il remoto `core`, aggiungi e conferma il codice e invia.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. Nell&#39;archivio `GRA` creare le directory seguenti:

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. Aggiungi il codice. Rimuovi il file `.gitignore`, aggiungi e conferma il codice, aggiungi il remoto e invia.

1. Nell&#39;archivio `brand/region`. Effettua le stesse operazioni eseguite nell&#39;archivio `GRA` e ricorda che i file devono essere univoci. Non è possibile includere lo stesso file sia in questo repository che in quello `GRA`.

1. Nell&#39;archivio `release`, applicare l&#39;unione.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. Rimuovi il file `.gitkeep`.

1. Distribuire l&#39;archivio `release` nei server di produzione, test, controllo qualità e sviluppo. L&#39;aggiornamento del codice `core`, `GRA` e `brand` è altrettanto semplice dell&#39;esecuzione dei seguenti comandi:

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## Opzione 4: Monorepo (scelta consigliata)

Questa strategia simula da vicino il funzionamento dell’archivio Git del Magento Open Source.

Tutto il codice viene sviluppato e testato in un unico archivio. L’automazione distilla i pacchetti da questo singolo archivio, che può essere installato su UAT e sugli ambienti di produzione utilizzando Composer.

![Diagramma che illustra l&#39;opzione monorepo per l&#39;architettura di riferimento globale](../../../assets/playbooks/gra-monorepo1.png)

L’opzione monorepo ti offre la facilità di lavorare in un singolo archivio, fornendo al contempo la flessibilità di comporre le istanze con i pacchetti.

Il controllo delle versioni e la distillazione dei pacchetti vengono eseguiti tramite automazione, utilizzando le azioni GitHub o GitLab.

![Diagramma che illustra l&#39;opzione monorepo per l&#39;architettura di riferimento globale](../../../assets/playbooks/gra-monorepo2.png)

Per ulteriori informazioni su questa automazione, consulta le risorse seguenti:

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>La configurazione di un monorepo è avanzata, ma offre la massima flessibilità al minor costo di gestione.

## Non mescolare strategie

Non è consigliabile utilizzare un approccio combinato utilizzando Composer per i pacchetti GRA e la directory `app/` per i pacchetti di marchio o area geografica.

Non solo ottieni tutti i _vantaggi_, ma anche tutti i _svantaggi_ di entrambi i metodi. Dovresti scegliere una delle due (Git o Compositore) per lavorare in modo ottimale.

## Soluzioni da evitare

- **Convenzioni di denominazione dei moduli per indicare GRA o brand**

  I moduli di denominazione per indicare GRA o marchio portano a una mancanza di flessibilità. Utilizza invece i metapacchetti Compositore per determinare a quale gruppo appartiene un modulo. Ad esempio, per il file VF del cliente, il pacchetto `vf/meta-gra` contiene riferimenti a tutti i pacchetti GRA e può essere installato utilizzando il comando `composer require vf/meta-gra`. Il pacchetto `vf/meta-kipling` contiene riferimenti a tutti i pacchetti specifici Kipling e al pacchetto `vf/meta-gra`. I moduli sono denominati ad esempio `vf/module-sales` e `vf/module-sap`. Questa convenzione di denominazione consente di spostare i pacchetti tra lo stato del marchio e lo stato GRA, con un impatto ridotto.

- **Aggiornamenti principali di Adobe Commerce per istanza**

  Pianifica gli aggiornamenti di base di Adobe Commerce, inclusi gli aggiornamenti delle patch, per far sì che diversi marchi o aree geografiche vengano eseguiti il più vicino possibile. Il supporto di più versioni di Adobe Commerce per i moduli condivisi comporta il forking dei moduli a causa di vincoli di compatibilità e raddoppia lo sforzo di manutenzione. Per evitare questo sforzo maggiore, accertati che tutte le istanze siano in esecuzione sulla stessa versione di Adobe Commerce prima di continuare lo sviluppo regolare.
