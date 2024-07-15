---
title: Follow-up sulla migrazione dei dati
description: Scopri come verificare che la migrazione dei dati dal Magento 1 al Magento 2 sia stata eseguita correttamente e che tutte le funzionalità funzionino come previsto.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Follow-up sulla migrazione dei dati

Alcuni comportamenti e logiche del Magento 1 sono stati implementati diversamente nel Magento 2. [!DNL Data Migration Tool] se ne occupa. Ci sono alcuni aspetti relativi alla migrazione di cui dovresti essere a conoscenza e a volte devi adottare misure minori per garantire il corretto funzionamento di alcune funzionalità dopo la migrazione.

## Informazioni

### Divisione del database non supportata

[!DNL Data Migration Tool] non supporta database suddivisi.

### Prezzi gruppo convertiti in prezzi livello

Tutti i prezzi di gruppo vengono automaticamente convertiti in prezzi di livello durante la migrazione.

### Nuova numerazione per entità di vendita

Numeri di riferimento per Ordini, Fatture, Spedizioni, Note di credito e RMA eseguono la migrazione così com&#39;è. Dopo la migrazione, si applicano le nuove regole di assegnazione dei numeri del Magento 2. La numerazione per le nuove entità di vendita è diversa.

## Passaggi

### Salva nuovamente segmenti cliente [solo Adobe Commerce]

Dopo la migrazione, i segmenti dei clienti devono essere salvati nuovamente dal pannello di amministrazione per essere operativi.

### Configurare il fuso orario

Lo strumento non esegue la migrazione delle impostazioni del fuso orario, pertanto devi configurare manualmente il fuso orario dopo la migrazione in **Archivi** > **Configurazione** > **Opzioni internazionali** > **Fuso orario**.

Per impostazione predefinita, il Magento memorizza i dati temporali nel fuso UTC-0 nel database e li visualizza in base alle impostazioni correnti del fuso orario. Se i dati temporali sono già stati salvati nel database in una zona diversa da UTC-0, è necessario convertire l&#39;ora esistente in UTC-0 utilizzando il gestore `\Migration\Handler\Timezone` di [!DNL Data Migration Tool].

Nell’esempio seguente, il Magento 1 ha erroneamente risparmiato tempo nella zona UTC-7 del database (ad esempio, a causa di un’estensione di terze parti errata). Per convertire correttamente l’ora di creazione dell’account cliente nella zona UTC-0 al momento della migrazione, effettua le seguenti operazioni:

1. Copiare il file di configurazione `map-customer.xml.dist` dalla directory appropriata di [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) nel file `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Aggiorna il nodo `<customer_map_file>` in `config.xml` e rimuovi l&#39;estensione `.dist` da `map-customer.xml.dist`

1. Aggiungi la seguente regola al file `map-customer.xml`:

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
