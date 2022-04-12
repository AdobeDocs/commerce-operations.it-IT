---
title: Moduli ed estensioni di aggiornamento
description: Utilizza l’interfaccia a riga di comando e il Compositore per aggiornare i moduli e le estensioni Adobe Commerce e Magenti Open Source.
source-git-commit: 70f1bda91023526fbc0024b6a6fef93c7633ecc2
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Aggiornamento di moduli ed estensioni

Per aggiornare o aggiornare un modulo o un&#39;estensione:

1. Scarica il file aggiornato da Marketplace o da un altro sviluppatore di estensioni. Prendi nota del nome e della versione del modulo.

1. Esporta il contenuto nella directory di installazione principale di Adobe Commerce o Magenti Open Source.

1. Se esiste un pacchetto Composer per il modulo, esegui una delle seguenti operazioni.

   Aggiornamento per nome del modulo:

   ```bash
   composer update vendor/module-name
   ```

   Aggiornamento per versione:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Esegui i seguenti comandi per aggiornare, distribuire e pulire la cache.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Estensioni bundle fornitore (VBEs)

Adobe rimosso tutti [VBE](https://devdocs.magento.com/extensions/vendor/) in 2.4.4. I fornitori continuano a supportare queste estensioni su Adobe Commerce Marketplace.

Se desideri continuare a utilizzare queste estensioni con Adobe Commerce e Magenti Open Source 2.4.4 e versioni successive, devi aggiornare le dipendenze dei pacchetti corrispondenti nella tua `composer.json` file _prima_ aggiornamento a 2.4.4. Contattare il fornitore per il nome e la versione del pacchetto da utilizzare.
