---
title: Configurare ed eseguire processi cron
description: Scopri come gestire i processi cron.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Configurare i processi cron

{{file-system-owner}}

Diverse funzioni di Commerce richiedono almeno un processo cron, che pianifica le attività in modo che si verifichino in futuro. Segue un elenco parziale di tali attività:

- Regole prezzo catalogo
- Newsletter
- Generazione di sitemap Google
- Avvisi/notifiche cliente (modifica del prezzo del prodotto, prodotto di nuovo in magazzino)
- Reindicizzazione
- Vendite private (solo Adobe Commerce)
- Aggiornamento automatico dei tassi di cambio
- Tutti i messaggi di posta elettronica di Commerce (inclusi quelli di conferma e quelli transazionali)

>[!WARNING]
>
>Non è più possibile eseguire `dev/tools/cron.sh` perché lo script è stato rimosso.

>[!INFO]
>
>Commerce dipende dalla corretta configurazione dei processi cron per molte importanti funzioni di sistema, inclusa l’indicizzazione. Se non viene configurato correttamente, Commerce non funzionerà come previsto.

I sistemi UNIX pianificano le attività che devono essere eseguite da determinati utenti utilizzando un _crontab_, ovvero un file contenente istruzioni per il daemon cron che indicano al daemon di eseguire il comando in questa data. Ogni utente dispone di una propria scheda cronologica e i comandi in una determinata scheda cronologica vengono eseguiti come l&#39;utente proprietario.

Per eseguire cron in un browser Web, vedere [Secure cron.php per l&#39;esecuzione in un browser](../security/secure-cron-php.md).

## Creare o rimuovere la scheda cronologica di Commerce

Questa sezione illustra come creare o rimuovere la scheda cronologica di Commerce (ovvero la configurazione per i processi Commerce Cron).

_crontab_ è la configurazione utilizzata per eseguire i processi cron.

L’applicazione Commerce utilizza attività cron che possono essere eseguite con configurazioni diverse. La configurazione della riga di comando PHP controlla il processo cron generale che reindicizza gli indicizzatori, genera e-mail, genera la sitemap e così via.

>[!WARNING]
>
>- Per evitare problemi durante l&#39;installazione e l&#39;aggiornamento, si consiglia vivamente di applicare le stesse impostazioni PHP sia alla configurazione della riga di comando PHP che alla configurazione del plug-in del server Web PHP. Per ulteriori informazioni, vedere [Impostazioni PHP richieste](../../installation/prerequisites/php-settings.md).
>- In un sistema a più nodi, crontab può essere eseguito su un solo nodo. Questo vale solo se imposti più nodi web per motivi legati alle prestazioni o alla scalabilità.

### Creare la scheda cronologica di Commerce

A partire dalla versione 2.2, Commerce crea una scheda Cronc per te. Aggiungiamo la scheda cronologica Commerce a qualsiasi scheda cronologica configurata per il proprietario del file system Commerce. In altre parole, se hai già impostato le schede cronologiche per altre estensioni o applicazioni, vi aggiungiamo la scheda cronologica Commerce.

La scheda cronologica di Commerce si trova all&#39;interno di `#~ MAGENTO START` e `#~ MAGENTO END` commenti nella scheda cronologica.

Per creare la scheda cronologica di Commerce:

1. Accedi come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.
1. Passare alla directory di installazione di Commerce.
1. Immetti il comando seguente:

   ```bash
   bin/magento cron:install [--force]
   ```

Utilizzare `--force` per riscrivere una scheda cronologica esistente.

>[!INFO]
>
>- `magento cron:install` non riscrive un crontab esistente all&#39;interno di `#~ MAGENTO START` e `#~ MAGENTO END` commenti nel crontab.
>- `magento cron:install --force` non ha alcun effetto sui processi cron al di fuori dei commenti di Commerce.

Per visualizzare la scheda cronologica, immettere il comando seguente come proprietario del file system:

```bash
crontab -l
```

Di seguito è riportato un esempio:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Il file `update/cron.php` è stato rimosso in Commerce 2.4.0. Se il file esiste nell&#39;installazione, può essere rimosso senza problemi.
>
>Qualsiasi riferimento a `update/cron.php` e `bin/magento setup:cron:run` deve essere rimosso anche dalla scheda Cronc&#39;

### Rimuovi la scheda cronologica di Commerce

Rimuovere la scheda cronologica di Commerce solo prima di disinstallare l&#39;applicazione Commerce.

Per rimuovere la scheda cronologica di Commerce:

1. Accedi come o passa al [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passare alla directory di installazione di Commerce.
1. Immetti il comando seguente:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Questo comando non ha alcun effetto sui processi cron al di fuori dei commenti `#~ MAGENTO START` e `#~ MAGENTO END` nella scheda Cronc.

## Esegui cron dalla riga di comando

Opzioni comando:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

dove `--group` specifica il gruppo cron da eseguire (omettere questa opzione per eseguire cron per tutti i gruppi)

Per eseguire il processo cron di indicizzazione, immettere:

```bash
bin/magento cron:run --group index
```

Per eseguire il processo cron predefinito, immettere:

```bash
bin/magento cron:run --group default
```

Per impostare processi e gruppi cron personalizzati, vedere [Configurare processi e gruppi cron personalizzati](../cron/custom-cron.md).

>[!INFO]
>
>È necessario eseguire cron due volte: la prima volta per individuare le attività da eseguire e la seconda volta per eseguire le attività stesse. La seconda esecuzione cron deve avvenire al momento o dopo il `scheduled_at` per ogni attività.

## Registrazione

Tutte le informazioni sul processo `cron` sono state spostate da `system.log` in un `cron.log` separato.
Per impostazione predefinita, le informazioni cron sono disponibili in `<install_directory>/var/log/cron.log`.
Tutte le eccezioni dai processi cron sono registrate da `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Oltre ad aver effettuato l&#39;accesso a `cron.log`:

- I processi non riusciti con stato `ERROR` e `MISSED` sono registrati in `<install_directory>/var/log/support_report.log`.

- I processi con stato `ERROR` vengono sempre registrati come `CRITICAL` in `<install_directory>/var/log/exception.log`.

- I processi con stato `MISSED` vengono registrati come `INFO` nella directory `<install_directory>/var/log/debug.log` (solo modalità sviluppatore).

>[!INFO]
>
>Tutti i dati cron vengono scritti anche nella tabella `cron_schedule` nel database di Commerce. La tabella fornisce una cronologia dei processi cron, tra cui:
>
>- ID processo e codice
>- Stato
>- Data di creazione
>- Data pianificata
>- Data di esecuzione
>- Data di fine
>
>Per visualizzare i record nella tabella, accedere al database di Commerce dalla riga di comando e immettere `SELECT * from cron_schedule;`.
