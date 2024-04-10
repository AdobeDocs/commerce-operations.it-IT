---
title: Gestire la cache
description: Gestisci i tipi di cache e visualizza lo stato della cache dalla riga di comando tramite Commerce CLI
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 1070291396144f866cadd5e42ebca3e77a484a9b
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Gestire la cache

{{file-system-owner}}

## Tipi di cache

Puoi utilizzare il sistema di gestione della cache di Adobe Commerce per migliorare le prestazioni del sito. Questo argomento spiega come gli amministratori di sistema o gli sviluppatori con accesso al server applicazioni Commerce possono gestire le cache dalla riga di comando.

>[!NOTE]
>
>
>Gli amministratori del sito di Commerce possono gestire la cache dall’amministratore utilizzando lo strumento Sistema di gestione della cache. Consulta [Gestione cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) nel _Guida ai sistemi di amministrazione_.


## Visualizzare lo stato della cache

Dalla riga di comando del server applicazioni Commerce, visualizzare lo stato della cache utilizzando `cache:status` Comando Commerce CLI.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Di seguito è riportato un esempio:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Per una descrizione dettagliata dei tipi di cache predefiniti supportati da Adobe Commerce, vedi [Cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) nel _Guida ai sistemi di amministrazione_.


## Abilitare o disabilitare i tipi di cache

Questo comando consente di abilitare o disabilitare tutti i tipi di cache o solo quelli specificati. La disabilitazione dei tipi di cache è utile durante lo sviluppo perché consente di visualizzare i risultati delle modifiche senza dover eseguire il flushing della cache; tuttavia, la disabilitazione dei tipi di cache ha un effetto negativo sulle prestazioni.

>[!INFO]
>
>A partire dalla versione 2.2, è possibile abilitare o disabilitare i tipi di cache solo utilizzando la riga di comando durante l’esecuzione di Commerce in modalità di produzione. Se esegui Commerce in modalità sviluppatore, puoi abilitare o disabilitare i tipi di cache utilizzando la riga di comando o manualmente. Prima di eseguire questa operazione, è necessario eseguire manualmente le operazioni `<magento_root>/app/etc/env.php` scrivibile da [proprietario del file system](../../installation/prerequisites/file-system/overview.md).

È possibile pulire (indicato anche come _scaricamento_ o _aggiorna_) i tipi di cache utilizzando la riga di comando o l&#39;amministratore.

Opzioni comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Se omesso `[type]` attiva o disattiva tutti i tipi di cache contemporaneamente. Il `type` option è un elenco di tipi di cache separati da spazi.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Per elencare i tipi di cache e il relativo stato:

```bash
bin/magento cache:status
```

Ad esempio, per disabilitare la cache della pagina intera e la cache DDL:

```bash
bin/magento cache:disable db_ddl full_page
```

Risultato di esempio:

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>L’abilitazione di un tipo di cache cancella automaticamente tale tipo di cache.

>[!INFO]
>
>A partire dalla versione 2.3.4, Commerce memorizza nella cache tutti gli attributi EAV di sistema durante il recupero. Memorizzare nella cache gli attributi EAV in questo modo migliora le prestazioni, perché riduce la quantità di richieste di inserimento/selezione al database. Tuttavia, aumenta anche la dimensione della rete cache. Gli sviluppatori possono memorizzare nella cache gli attributi EAV personalizzati eseguendo il comando `bin/magento config:set dev/caching/cache_user_defined_attributes 1` comando. Questa operazione può essere eseguita anche dall’amministratore durante la [Modalità sviluppatore](../bootstrap/application-modes.md) impostando **Negozi** > Impostazioni **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni di memorizzazione in cache** > **Memorizza nella cache attributi definiti dall&#39;utente** a **Sì**.

## Pulisci e svuota tipi di cache

>[!NOTE]
>
>La cache di più pagine può essere invalidata simultaneamente e automaticamente **_senza_** entità che modificano. Ad esempio, quando un prodotto nel catalogo viene assegnato a una categoria o quando [!UICONTROL related product rule] è stato modificato.

Per rimuovere gli elementi obsoleti dalla cache, puoi _pulita_ o _scaricamento_ tipi di cache:

- La pulizia di un tipo di cache comporta l’eliminazione di tutti gli elementi solo dai tipi di cache di Commerce abilitati. In altre parole, questa opzione non influisce su altri processi o applicazioni perché pulisce solo la cache utilizzata da Commerce.

  I tipi di cache disattivati non vengono puliti.

  >[!TIP]
  >
  >Pulisci sempre la cache dopo aver aggiornato le versioni di Magento Open Source o Adobe Commerce, aggiornato da Magento Open Source ad Adobe Commerce o installato B2B per Adobe Commerce o qualsiasi modulo.

- Lo svuotamento di un tipo di cache svuota la memoria cache, il che potrebbe influire su altre applicazioni di processi che utilizzano lo stesso spazio di archiviazione.

Svuota i tipi di cache se hai già provato a pulire la cache e riscontri ancora problemi che non puoi isolare.

Utilizzo comando:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Dove `[type]` è un elenco di tipi di cache separati da spazi. Omissione `[type]` pulisce o svuota tutti i tipi di cache contemporaneamente. Ad esempio, per eseguire il flushing di tutti i tipi di cache, immettere

```bash
   bin/magento cache:flush
```

Risultato di esempio:

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>Puoi anche pulire e svuotare i tipi di cache in Admin. Vai a **Sistema** > **Strumenti** > **Gestione cache**. **Svuota archiviazione cache** equivale a `bin/magento cache:flush`. **Svuota cache Magento** equivale a `bin/magento cache:clean`.
