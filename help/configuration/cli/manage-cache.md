---
title: Gestire la cache
description: Gestisci i tipi di cache e visualizza lo stato della cache.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# Gestire la cache

{{file-system-owner}}

## Tipi di cache

Commerce 2 dispone dei seguenti tipi di cache:

| Nome &quot;descrittivo&quot; del tipo di cache | Nome del codice del tipo di cache | Descrizione |
|--- |--- |--- |
| Configurazione | config | Commerce raccoglie la configurazione da tutti i moduli, la unisce e salva il risultato unito nella cache. Questa cache contiene anche le impostazioni specifiche dello store memorizzate nel file system e nel database. Pulisci o svuota questo tipo di cache dopo aver modificato i file di configurazione. |
| Layout | layout | Layout di pagina compilati (ovvero i componenti di layout di tutti i componenti). Pulisci o svuota questo tipo di cache dopo aver modificato i file di layout. |
| Uscita HTML a blocchi | block_html | Frammenti di pagina di HTML per blocco. Pulisci o svuota questo tipo di cache dopo aver modificato il livello di visualizzazione. |
| Dati delle raccolte | collezioni | Risultati delle query del database. Se necessario, Commerce pulisce automaticamente questa cache, ma gli sviluppatori di terze parti possono inserire qualsiasi dato in qualsiasi segmento della cache. Pulisci o scarica questo tipo di cache se il modulo personalizzato utilizza una logica che restituisce voci di cache che Commerce non può pulire. |
| DDL | db_ddl | Schema del database. Se necessario, Commerce pulisce automaticamente questa cache, ma gli sviluppatori di terze parti possono inserire qualsiasi dato in qualsiasi segmento della cache. Pulisci o svuota questo tipo di cache dopo aver apportato modifiche personalizzate allo schema del database. (In altre parole, gli aggiornamenti che Commerce non esegue autonomamente). Un modo per aggiornare automaticamente lo schema del database è quello di utilizzare `magento setup:db-schema:upgrade` comando. |
| Configurazione compilata | compila_config | Configurazione della compilazione |
| Valore dell&#39;attributo dell&#39;entità (EAV) | eav | Metadati relativi agli attributi EAV (ad esempio, le etichette del negozio, i collegamenti al codice PHP correlato, il rendering degli attributi, le impostazioni di ricerca e così via). In genere non è necessario pulire o svuotare questo tipo di cache. |
| Cache della pagina | full_page | Pagine HTML generate. Se necessario, Commerce pulisce automaticamente questa cache, ma gli sviluppatori di terze parti possono inserire qualsiasi dato in qualsiasi segmento della cache. Pulisci o svuota questo tipo di cache dopo aver modificato il livello di codice che influisce sull’output di HTML. Si consiglia di mantenere abilitata la cache perché la memorizzazione in cache di HTML migliora notevolmente le prestazioni. |
| Riflessione | riflessione | Rimuove una dipendenza tra il modulo Webapi e il modulo Customer. |
| Traduzioni | tradurre | Dopo aver unito le traduzioni da tutti i moduli, la cache di fusione verrà pulita. |
| Configurazione dell’integrazione | config_integration | Integrazioni compilate. Pulisci o svuota la cache dopo aver modificato o aggiunto integrazioni. |
| Configurazione dell’API di integrazione | config_integration_api | Configurazione delle API di integrazione compilata delle integrazioni dello Store. |
| Configurazione servizi web | config_webservice | Memorizzazione in cache della struttura API Web. |
| Notifica al cliente | customer_notification | Notifiche temporanee visualizzate nell’interfaccia utente. |

## Visualizza lo stato della cache

Per visualizzare lo stato della cache, immetti

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Segue un esempio:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## Attiva o disattiva i tipi di cache

Questo comando consente di abilitare o disabilitare tutti i tipi di cache o solo quelli specificati. La disattivazione dei tipi di cache è utile durante lo sviluppo perché si vedono i risultati delle modifiche senza dover scaricare la cache; tuttavia, la disattivazione dei tipi di cache ha un effetto negativo sulle prestazioni.

>[!INFO]
>
>A partire dalla versione 2.2, è possibile abilitare o disabilitare i tipi di cache solo utilizzando la riga di comando durante l’esecuzione di Commerce in modalità di produzione. Se esegui Commerce in modalità sviluppatore, puoi abilitare o disabilitare i tipi di cache utilizzando la riga di comando o manualmente. Prima di eseguire questa operazione, devi effettuare manualmente `<magento_root>/app/etc/env.php` scrivibile da [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

È possibile pulire (indicato anche come _scaricatore_ o _aggiorna_) utilizzando la riga di comando o l’amministratore.

Opzioni di comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Dove omettere `[type]` abilita o disabilita tutti i tipi di cache contemporaneamente. La `type` è un elenco di tipi di cache separati da spazi.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Per elencare i tipi di cache e il relativo stato:

```bash
bin/magento cache:status
```

Ad esempio, per disabilitare la cache della pagina completa e la cache DDL:

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
>A partire dalla versione 2.3.4, Commerce memorizza nella cache tutti gli attributi EAV del sistema al momento del recupero. La memorizzazione in cache degli attributi EAV in questo modo migliora le prestazioni, perché diminuisce la quantità di richieste di inserimento/selezione al database. Tuttavia, aumenta anche le dimensioni della rete della cache. Gli sviluppatori possono memorizzare nella cache gli attributi EAV personalizzati eseguendo il `bin/magento config:set dev/caching/cache_user_defined_attributes 1` comando. Questa operazione può essere eseguita anche dall’amministratore durante l’accesso [Modalità Sviluppatore](../bootstrap/application-modes.md) impostando **Negozi** > Impostazioni **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni di memorizzazione in cache** > **Attributi definiti dall&#39;utente della cache** a **Sì**.

## Pulizia e svuotamento dei tipi di cache

Per eliminare gli elementi obsoleti dalla cache, puoi _pulito_ o _scaricatore_ tipi di cache:

- La pulizia di un tipo di cache elimina tutti gli elementi solo dai tipi di cache Commerce abilitati. In altre parole, questa opzione non influisce su altri processi o applicazioni perché cancella solo la cache utilizzata da Commerce.

   I tipi di cache disattivati non vengono puliti.

   >[!TIP]
   >
   >Pulisci sempre la cache dopo l’aggiornamento delle versioni di Magenti Open Source o Adobe Commerce, l’aggiornamento da Magenti Open Source ad Adobe Commerce o l’installazione di B2B per Adobe Commerce o qualsiasi modulo.

- Lo scaricamento di un tipo di cache elimina lo spazio di archiviazione cache, il che potrebbe interessare altre applicazioni di processi che utilizzano lo stesso spazio di archiviazione.

Tipi di cache scaricabili se hai già provato a pulire la cache e si verificano ancora problemi che non puoi isolare.

Utilizzo comando:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Dove `[type]` è un elenco di tipi di cache separati da spazi. Omissione `[type]` pulisce o scarica contemporaneamente tutti i tipi di cache. Ad esempio, per svuotare tutti i tipi di cache, immetti

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
   config_webservice
   translate
```

>[!TIP]
>
>Puoi anche pulire e svuotare i tipi di cache nell’amministratore. Vai a **Sistema** > **Strumenti** > **Gestione cache**. **Archiviazione cache scaricata** equivale a `bin/magento cache:flush`. **Svuotare la cache del Magento** equivale a `bin/magento cache:clean`.
