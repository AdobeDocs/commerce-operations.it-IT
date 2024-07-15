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

Questa guida descrive come impostare e gestire l&#39;opzione [pacchetti separati](../examples.md#option-1-separate-packages) descritta negli esempi di architettura di riferimento globale (GRA).

## Prerequisiti

Prima di iniziare, verifica quanto segue:

- Disponi di un archivio Git
- Disponi di un archivio Compositore (in questo argomento viene evidenziato Private Packagist)
- Il repository Composer è stato configurato per riflettere gli archivi `repo.magento.com` e `packagist.org`

## Archivio principale del progetto Git

L’archivio principale del progetto Git deve contenere solo un progetto Composer. Puoi gestire tutto il resto con i pacchetti Composer. Il progetto principale non deve mai contenere elementi diversi dalla seguente struttura di file, in quanto Composer installa tutti gli altri pacchetti attraverso le dipendenze:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Aggiungi il seguente contenuto al file `.gitignore`:

```tree
/*
!/composer.json
!/composer.lock
```

## Inizializzare il progetto principale

1. Creare un archivio Git denominato `project-<region/country/brand>`.

1. Creare `composer.json` e `composer.lock` file:

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

1. Aggiungere il file `app/etc/config.xml` all&#39;archivio Git.

   È possibile utilizzare il modulo che si sta per creare per installare altri file specifici dell&#39;area geografica o del marchio, ad esempio `.htaccess`, file di testo di autenticazione Google o Bing, file eseguibili o altri file statici non gestiti dai moduli di Adobe Commerce.

   Utilizzare pacchetti di tipo `magento2-component` per creare un mapping di file per copiare i file nell&#39;archivio Git principale durante le operazioni `composer install` e `composer update`.

1. Creare un archivio Git che segue la convenzione di denominazione `component-environment-<region/country/brand>`:

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

1. Aggiungi il file `app/etc/config.php` come mapping nell&#39;attributo `extra.map` del file `composer.json`:

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

1. Convalida il file `composer.json` e esegui il commit nell&#39;archivio Git:

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

1. Verificare che Composer abbia copiato il file `app/etc/config.php` da `<client>/component-environment-<region/country/brand>`.

## Distribuisci il codice

Sul server web, puoi distribuire il codice utilizzando Compositore, ma non puoi aggiornare il progetto principale. Reinstalla il progetto utilizzando Composer con ogni nuova distribuzione, eliminando la necessità per i server di produzione e di test di avere accesso a Git.

## Aggiungere altre istanze e pacchetti

Ogni istanza (area geografica, marchio o installazione univoca di Adobe Commerce) deve ottenere la propria istanza del **progetto principale**, il **metapackage specifico** e il **pacchetto di componenti dell&#39;ambiente**. Il metapackage **GRA** deve essere **condiviso** in tutte le istanze.

I pacchetti funzionali (come moduli, temi, Language Pack e librerie di Adobe Commerce) e i pacchetti di terze parti devono essere richiesti da:

- **GRA metapackage**—Per l&#39;installazione su _tutte_ le istanze
- **metapackage specifico dell&#39;istanza** - Per l&#39;installazione su un singolo marchio o area geografica

>[!IMPORTANT]
>
>Non richiedere pacchetti nel file `composer.json` del progetto principale sui rami `main` o `release`.

## Prepararsi per lo sviluppo

Per lo sviluppo, installare `develop` versioni di tutti i moduli gestiti.

A seconda della strategia di ramificazione, è possibile che siano presenti `develop`, `qa`, `uat` e `main` rami. Ogni ramo esiste in Composer con il prefisso `dev-`. Pertanto, il ramo `develop` può essere richiesto tramite Composer come versione `dev-develop`.

1. Crea `develop` rami in tutti i moduli e gli archivi dei progetti.

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

   Il passaggio precedente genera le righe seguenti nel file `composer.json`:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Non unire** queste `composer.json` modifiche al file nel ramo di produzione. Installa solo versioni stabili dei pacchetti nei rami `release` e `main`. È possibile definire queste dipendenze per `qa` rami e altri rami non principali.
