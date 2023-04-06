---
title: Follow-up della migrazione dei dati
description: Scopri come verificare che la migrazione dei dati dal Magento 1 al Magento 2 sia avvenuta con successo e che tutte le funzionalità funzionino come previsto.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Follow-up della migrazione dei dati

Alcuni comportamenti e logiche del Magento 1 sono stati implementati in modo diverso nel Magento 2. La [!DNL Data Migration Tool] Se ne prende cura. È necessario conoscere alcuni aspetti della migrazione e a volte è necessario compiere piccoli passi affinché alcune funzionalità funzionino correttamente dopo la migrazione.

## Informazioni

### Database diviso non supportato

La [!DNL Data Migration Tool] non supporta i database suddivisi.

### Prezzi di gruppo convertiti in prezzi di classe

Tutti i prezzi di gruppo vengono automaticamente convertiti in prezzi di livello durante la migrazione.

### Nuova numerazione per le entità di vendita

I numeri di riferimento per gli ordini, le fatture, le spedizioni, le note di credito e la RMA migrano così come sono. Dopo la migrazione, si applicano le nuove regole di assegnazione dei numeri di Magento 2. La numerazione per le nuove entità di vendita è diversa.

## Passaggi

### Salvataggio dei segmenti dei clienti [Solo Adobe Commerce]

Dopo la migrazione, i segmenti cliente devono essere salvati nuovamente dal pannello di amministrazione per essere operativi.

### Configurare il fuso orario

Lo strumento non esegue la migrazione delle impostazioni del fuso orario, pertanto devi configurare manualmente il fuso orario dopo la migrazione in **Negozi** > **Configurazione** > **Opzioni internazionali** > **Fuso orario**.

Per impostazione predefinita, il Magento memorizza i dati dell’ora nel fuso orario UTC-0 del database e li visualizza in base alle impostazioni correnti del fuso orario. Se i dati relativi all’ora sono già stati salvati nel database in una zona diversa da UTC-0, è necessario convertire l’ora esistente in UTC-0 utilizzando la variabile [!DNL Data Migration Tool]s `\Migration\Handler\Timezone` handler.

Nell’esempio seguente, il Magento 1 ha risparmiato in modo errato il tempo nella zona UTC-7 del database (ad esempio, a causa di un’estensione di terze parti difettosa). Per convertire correttamente l’ora di creazione dell’account cliente nel fuso UTC-0 al momento della migrazione, effettua le seguenti operazioni:

1. Copia il `map-customer.xml.dist` file di configurazione dalla directory appropriata del [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) nel `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` file.

1. Aggiorna `<customer_map_file>` nodo in `config.xml` e rimuovere `.dist` estensione da `map-customer.xml.dist`

1. Aggiungi la seguente regola al `map-customer.xml` file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
