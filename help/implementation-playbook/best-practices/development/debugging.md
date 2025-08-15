---
title: Best practice per il debug
description: Scopri le tecniche per risolvere i problemi comuni di sviluppo di Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Best practice per il debug per Adobe Commerce

Questo argomento spiega come eseguire il debug sistematico ed efficace del framework Adobe Commerce. L’obiettivo è quello di aiutarti a individuare rapidamente la radice di un problema e ridurre al minimo i tempi di investigazione.

## Risoluzione dei problemi: sospetti abituali

Questa sezione descrive i problemi più comuni che potresti riscontrare durante lo sviluppo.

### Cache

- Svuota la cache prima di ulteriori indagini
- Considera la cache APC, la rete CDN, la vernice, il codice generato e le directory `var/view_preprocessed` e `pub/static/`
- Arresta e riavvia i gestori code dopo lo svuotamento della cache o la modifica del codice

Il codice di esempio seguente fornisce comandi utili relativi alla gestione della cache (non eseguire in ambienti di produzione):

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### Dati indicizzati

Reindicizza tutto se il problema potrebbe essere correlato all’indice. Il debug dei dati indicizzati si verifica in genere in ambienti non di produzione. Negli ambienti di produzione, potrebbe essere utile analizzare l’origine del disallineamento dell’indice prima di reindicizzarlo. Le caratteristiche dello stato difettoso possono dirvi qualcosa sull&#39;origine del problema.

### Compositore

È possibile che il codice sia obsoleto a causa di una modifica del ramo o a causa di file core modificati in un precedente tentativo di debug. Per eliminare potenziali problemi, eseguire i comandi seguenti:

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Contenuto generato

Rigenera i file front-end prima di eseguire il debug del contenuto generato in JS, CSS, immagini, traduzioni e altri file.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Modalità sviluppatore

Verificare che l&#39;installazione locale sia in modalità `developer`.

### Nuovo modulo

Se hai creato un modulo, verifica la presenza dei seguenti problemi:

- Il modulo è abilitato?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Controlla il file `app/etc/config.php` per il nuovo modulo.

- Controllare la nidificazione della struttura del file e della directory. Ad esempio, i file di layout si trovano nella directory `view/layout/` invece che nella directory `view/frontend/layout`? I modelli si trovano nella directory `view/frontend/template` invece che nella directory `view/frontend/templates`?

## Risoluzione dei problemi: Suddivisione in parti uguali

Se i soliti sospetti non offrono una soluzione al problema, il modo più veloce per procedere è quello di dividere il problema per metà (o bisecare). Con questo metodo, si eliminano grandi blocchi e si divide ciò che rimane per individuare la causa principale invece di passare attraverso il codice in modo lineare.

Vedere i seguenti diagrammi:

![Diagramma bisettile](../../../assets/playbooks/bisect.png)

![Diagramma bisettile](../../../assets/playbooks/bisect2.png)

Esistono diversi approcci alla bisezione, ma Adobe consiglia di seguire questo ordine:

- Bisetta per argomento
- Bisetta per commit
- Bisect per file

### Passaggio 1: Bisect per argomento

Se il problema non è correlato al codice, eliminare prima i blocchi di grandi dimensioni. Alcuni dei blocchi più grandi a cui pensare includono:

- **Framework Adobe Commerce**: il problema è relativo ad Adobe Commerce o potrebbe essere correlato a un altro sistema connesso?
- **Server e client** - Cancella la cache e l&#39;archiviazione del browser. Il problema è risolto? Questo potrebbe escludere una causa relativa al server. Il problema esiste ancora? Non è necessario sprecare altro tempo nel debug del browser.
- **Sessione**: il problema si verifica per ogni utente? In caso contrario, il problema potrebbe essere limitato ad argomenti relativi alla sessione o al browser.
- **Cache**: la disattivazione di tutte le cache comporta delle modifiche? In tal caso, puoi concentrarti su argomenti relativi alla cache.
- **Database**: il problema si verifica in tutti gli ambienti che eseguono lo stesso codice? In caso contrario, cercare problemi nella configurazione e altri argomenti correlati al database.
- **Codice** - Cercare i problemi di codice se nessuno dei problemi sopra indicati ha risolto il problema.

### Passaggio 2: eseguire il bisect per commit

Se il problema è iniziato tra ora e due mesi fa, riporta il codice a due mesi fa. Verificare se il problema persiste. Andare avanti di un mese. Il problema si verifica qui? In caso contrario, procedere di due settimane. Si verifica ora? Torna indietro di una settimana. Ancora lì? Torna indietro di quattro giorni. A un certo punto, è rimasto un solo commit che probabilmente conterrà il codice relativo al problema. La causa principale è ora probabilmente limitata ai file modificati in tale commit.

È possibile sostituire settimane e giorni con commit. Ad esempio, esegui il rollback di 100 commit, avanti 50, avanti 25, indietro 12.

### Passaggio 3: creare un file Bisect by

- Dividi Adobe Commerce per tipi di file (core e non-core). Innanzitutto, disabilita tutti i moduli cliente e marketplace. Il problema esiste ancora? Molto probabilmente si tratta di un problema non fondamentale.
- Abilitare di nuovo circa la metà dei moduli nel file `app/etc/config.php`. Presta attenzione alle dipendenze. È consigliabile abilitare i cluster di moduli con lo stesso argomento contemporaneamente. Il problema esiste ancora?
- Attiva un quarto dei moduli rimanenti. Il problema esiste ancora? Disattiva metà di ciò che hai abilitato. Questo metodo può aiutarti a isolare la causa principale in un singolo modulo.

## Risparmi di tempo

Oltre alle tecniche di risoluzione dei problemi, questa sezione fornisce alcune regole generali che possono aiutare a risparmiare tempo durante il debug.

### Limita dati

Valuta se è necessario il catalogo completo o tutte le visualizzazioni dello store per replicare il problema. È possibile eseguire il debug dei problemi di indicizzazione relativi a un clone di database in cui è stato rimosso il 95% del catalogo prima di avviare il debug. Questo metodo consente di risparmiare molto tempo durante i processi di indicizzazione. Crea un duplicato del database client con un numero di archivi e un catalogo ridotti. Questo potrebbe valere anche per altre entità (come i clienti) a seconda dell’area di cui si sta eseguendo il debug.

### Richiedi ulteriori informazioni

A volte, un passaggio facile da dimenticare tra tutto il codice e il lavoro tecnico: chiedere ulteriori informazioni. Acquisizioni a schermo intero, un video, una videoconferenza chat con la persona che ha identificato il problema, passaggi di replica, domande se altre cose apparentemente non importanti sono accadute intorno all&#39;evento problematico. Chiedi cosa si aspettava che accadesse. Si tratta davvero di un bug o forse solo di un&#39;incomprensione del modo in cui funziona il codice?

### Lingua e interpretazione

La descrizione del problema è chiara? Sei sicuro che nessun termine o descrizione possa essere interpretato in più modi? Se sì, assicurati di parlare della stessa cosa.

### Ricerca Internet

Eseguire una ricerca su Internet con i termini relativi al problema. È probabile che un altro utente abbia già riscontrato lo stesso problema. Cerca nei [problemi GitHub di Adobe Commerce](https://github.com/magento/magento2/issues).

### Fai una pausa

Se si sta cercando un problema troppo a lungo, può essere difficile trovare una soluzione. Metti giù il tuo lavoro e prendi un altro compito o fai una passeggiata. La risposta potrebbe venire quando si dimentica del problema per un po &#39;.

## Strumenti

Gli strumenti CLI n98 magerun ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) forniscono funzionalità utili per l&#39;utilizzo di Adobe Commerce dalla riga di comando. In particolare, i seguenti comandi:

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Frammenti di codice

Negli argomenti seguenti vengono forniti snippet di codice che possono essere utilizzati per registrare o identificare i problemi nei progetti Commerce.

### Controlla se Commerce utilizza un file XML

Aggiungi un errore di sintassi evidente in un file XML per verificare se è utilizzato. Apri un tag e non chiuderlo, ad esempio:

```xml
<?xml version="1.0"?>
<test
```

Se questo file viene utilizzato, genera un errore. In caso contrario, il modulo potrebbe non essere utilizzato o non essere abilitato, ad esempio, oppure il file XML potrebbe trovarsi in una posizione errata.

### Registrazione

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monologo]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### Registrazione di basso livello

Due esempi che funzionano sempre in qualsiasi file PHP:

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

E per una traccia dello stack:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
