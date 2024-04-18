---
title: Aggiornare moduli ed estensioni
description: Utilizza l’interfaccia della riga di comando e il Compositore per aggiornare moduli ed estensioni di Adobe Commerce.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Aggiornare moduli ed estensioni

Per aggiornare un modulo o un’estensione:

1. Scarica il file aggiornato da Marketplace o da un altro sviluppatore di estensioni. Prendi nota del nome e della versione del modulo.

1. Esporta i contenuti nella directory di installazione principale di Adobe Commerce.

1. Se esiste un pacchetto Compositore per il modulo, esegui una delle seguenti operazioni.

   Nome aggiornamento per modulo:

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

## Estensioni in bundle con i fornitori (VBE)

Adobe rimosso tutto [VBE](https://devdocs.magento.com/extensions/vendor/) al punto 2.4.4. I fornitori continuano a supportare queste estensioni sul Marketplace Adobe Commerce.

Se desideri continuare a utilizzare queste estensioni con Adobe Commerce 2.4.4 e versioni successive, devi aggiornare le dipendenze dei pacchetti corrispondenti nel `composer.json` file _prima di_ aggiornamento a 2.4.4. Contatta il fornitore per il nome e la versione del pacchetto da utilizzare.

Per ulteriori informazioni, consulta i seguenti elenchi di Adobe Commerce Marketplace:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigitale](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vertice](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
