---
title: Aggiornare moduli ed estensioni
description: Utilizza l’interfaccia della riga di comando e il Compositore per aggiornare moduli ed estensioni di Adobe Commerce.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%
---
# Aggiornare moduli ed estensioni

Per aggiornare un modulo o un’estensione:

1. Scarica il file aggiornato da Marketplace o da un altro sviluppatore di estensioni. Prendi nota del nome e della versione del modulo.

1. Esporta i contenuti nella directory di installazione principale di Adobe Commerce.

1. Se esiste un pacchetto Compositore per il modulo, esegui una delle seguenti operazioni.

   Nome aggiornamento per modulo:

   ```shell
   composer update vendor/module-name
   ```

   Aggiornamento per versione:

   ```shell
   composer require vendor/module-name ^x.x.x
   ```

1. Esegui i seguenti comandi per aggiornare, distribuire e pulire la cache.

   ```shell
   bin/magento setup:upgrade --keep-generated
   ```

   ```shell
   bin/magento setup:static-content:deploy
   ```

   ```shell
   bin/magento cache:clean
   ```

## Estensioni in bundle con i fornitori (VBE)

Adobe ha rimosso tutti i [VBE](/help/upgrade/modules/upgrade.md) nella versione 2.4.4. I fornitori continuano a supportare queste estensioni sul Marketplace Adobe Commerce.

Se si desidera continuare a utilizzare queste estensioni con Adobe Commerce 2.4.4 e versioni successive, è necessario aggiornare le dipendenze del pacchetto corrispondenti nel file `composer.json` _prima_ dell&#39;aggiornamento alla versione 2.4.4. Contatta il fornitore per il nome e la versione del pacchetto da utilizzare.

Per ulteriori informazioni, consulta i seguenti elenchi di Adobe Commerce Marketplace:

- [Amazon Pay](https://commercemarketplace.adobe.com//amzn-amazon-pay-magento-2-module.html)
- [Dotdigitale](https://commercemarketplace.adobe.com//dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html)
- [Vertice](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html)
- [Yotpo](https://commercemarketplace.adobe.com//yotpo-module-yotpo.html)
