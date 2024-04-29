---
title: Struttura del progetto Compositore
description: Scopri come impostare e gestire l’opzione dei pacchetti separati, descritta negli esempi di architettura di riferimento globale.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Struttura del progetto Compositore

Questa guida descrive come impostare e gestire [opzione pacchetti separati](../examples.md#option-1-separate-packages) descritte negli esempi di architettura di riferimento globale (GRA).

## Prerequisiti

Prima di iniziare, verifica quanto segue:

- Disponi di un archivio Git
- Disponi di un archivio Compositore (in questo argomento viene evidenziato Private Packagist)
- Hai configurato l’archivio del Compositore in modo da rispecchiare `repo.magento.com` e `packagist.org` archivi

## Archivio principale del progetto Git

L’archivio principale del progetto Git deve contenere solo un progetto Composer. Puoi gestire tutto il resto con i pacchetti Composer. Il progetto principale non deve mai contenere elementi diversi dalla seguente struttura di file, in quanto Composer installa tutti gli altri pacchetti attraverso le dipendenze:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Aggiungi il seguente contenuto al `.gitignore` file:

```tree
/*
!/composer.json
!/composer.lock
```

## Inizializzare il progetto principale

1. Creare un archivio Git denominato `project-<region/country/brand>`.

1. Crea `composer.json` e `composer.lock` file:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Salva file non modulo

1. Aggiungi il `app/etc/config.xml` nell’archivio Git.

   Puoi utilizzare il modulo che stai per creare per installare altri file specifici per l’area geografica o il marchio, ad esempio `.htaccess`File di testo, eseguibili o altri file statici di autenticazione Google o Bing non gestiti dai moduli Adobe Commerce.

   Utilizzare `magento2-component` digita i pacchetti per creare una mappatura file per copiare i file nell’archivio Git principale durante `composer install` e `composer update` operazioni.

1. Crea un archivio Git che segue la convenzione di denominazione `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Aggiungi il `app/etc/config.php` file come mappatura in `extra.map` attributo del tuo `composer.json` file:

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Convalidare `composer.json` file e esegui il commit nell’archivio Git:

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Configurare i metapacchetti

1. Crea i seguenti archivi Git:

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Impostare la seguente struttura di dipendenze:

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Creare il metapacchetto GRA:

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Creare il metapacchetto del brand:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Richiedi la raccolta tramite la gestione delle dipendenze nel progetto principale:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Verifica che Composer abbia copiato `app/etc/config.php` file da `<client>/component-environment-<region/country/brand>`.

## Distribuisci il codice

Sul server web, puoi distribuire il codice utilizzando Compositore, ma non puoi aggiornare il progetto principale. Reinstalla il progetto utilizzando Composer con ogni nuova distribuzione, eliminando la necessità per i server di produzione e di test di avere accesso a Git.

## Aggiungere altre istanze e pacchetti

Ogni istanza (area geografica, marchio o altra installazione univoca di Adobe Commerce) deve avere il proprio **progetto principale** istanza, **metapacchetto specifico**, e **pacchetto dei componenti dell’ambiente**. Il **Metapackage GRA** dovrebbe essere **condiviso** in tutte le istanze.

I pacchetti funzionali (come moduli, temi, Language Pack e librerie di Adobe Commerce) e i pacchetti di terze parti devono essere richiesti da:

- **Metapackage GRA**- Per installazione su _tutto_ istanze
- **metapackage specifico dell’istanza**- Per l&#39;installazione su un&#39;unica marca o regione

>[!IMPORTANT]
>
>Non richiedere pacchetti nel del progetto principale `composer.json` file su `main` o `release` rami.

## Prepararsi per lo sviluppo

Per lo sviluppo, installare `develop` versioni di tutti i moduli gestiti.

A seconda della strategia di ramificazione, è possibile che `develop`, `qa`, `uat`, e `main` rami. Ogni ramo esiste in Compositore con `dev-` prefisso. Quindi il `develop` il ramo può essere richiesto tramite Compositore come versione `dev-develop`.

1. Crea `develop` diramazioni in tutti i moduli e archivi di progetti.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   Il passaggio precedente genera le seguenti righe nel `composer.json` file:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Non unire** questi `composer.json` modifiche al file nel ramo di produzione. Installa solo versioni stabili dei pacchetti su `release` e `main` rami. È possibile definire queste dipendenze per `qa` le filiali e le altre filiali non principali.
