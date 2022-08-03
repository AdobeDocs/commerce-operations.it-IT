---
title: Configurare ed eseguire i lavori cron
description: Scopri come gestire i lavori cron.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# Configurare i lavori cron

{{file-system-owner}}

Diverse funzioni Commerce richiedono almeno un lavoro cron, che pianifica le attività da eseguire in futuro. Segue un elenco parziale di queste attività:

- Regole del prezzo del catalogo
- Newsletter
- Generazione di sitemap Google
- Avvisi/Notifiche del cliente (variazione del prezzo del prodotto, riacquisto del prodotto)
- Reindicizzazione
- Vendite private (solo Adobe Commerce)
- Aggiornamento automatico dei tassi di cambio
- Tutte le e-mail Commerce (inclusa la conferma dell’ordine e le transazioni)

>[!WARNING]
>
>Non è più possibile eseguire `dev/tools/cron.sh` perché lo script è stato rimosso.

>[!INFO]
>
>Commerce dipende da una corretta configurazione del lavoro cron per molte importanti funzioni di sistema, inclusa l&#39;indicizzazione. In caso contrario, Commerce non funzionerà come previsto.

I sistemi UNIX pianificano le attività che devono essere eseguite da utenti particolari utilizzando un _crontab_, che è un file che contiene istruzioni al daemon cron che dicono al daemon in effetti di &quot;eseguire questo comando a questa ora a questa data&quot;. Ogni utente dispone di un proprio crontab e i comandi di qualsiasi crontab vengono eseguiti come utente proprietario dell&#39;utente.

Per eseguire cron in un browser Web, vedi [Proteggi cron.php per l&#39;esecuzione in un browser](../security/secure-cron-php.md).

## Creare o rimuovere la scheda comparativa Commerce

Questa sezione illustra come creare o rimuovere il tuo crontab Commerce (ovvero la configurazione per i lavori Commerce cron).

La _crontab_ è la configurazione utilizzata per eseguire i processi cron.

L’applicazione Commerce utilizza attività cron che possono essere eseguite con configurazioni diverse. La configurazione della riga di comando PHP controlla il processo cron generale che reindicizza gli indici, genera e-mail, genera la mappa del sito e così via.

>[!WARNING]
>
>- Per evitare problemi durante l&#39;installazione e l&#39;aggiornamento, si consiglia vivamente di applicare le stesse impostazioni PHP sia alla configurazione della riga di comando PHP che alla configurazione del plug-in del server web PHP. Per ulteriori informazioni, consulta [Impostazioni PHP richieste](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
>- In un sistema a più nodi, crontab può essere eseguito su un solo nodo. Ciò vale solo se si impostano più nodi Web per motivi legati a prestazioni o scalabilità.


### Creare la scheda multimediale Commerce

A partire dalla versione 2.2, Commerce crea un crontab per te. Aggiungiamo la crontab Commerce a qualsiasi crontab configurato per il proprietario del file system Commerce. In altre parole, se hai già configurato crontab per altre estensioni o applicazioni, gli aggiungiamo la crontab Commerce .

La crontab Commerce si trova all’interno di `#~ MAGENTO START` e `#~ MAGENTO END` commenti nella tua crontab.

Per creare la scheda comparativa Commerce:

1. Accedi come o passa a [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Passa alla directory di installazione Commerce.
1. Immetti il seguente comando:

   ```bash
   bin/magento cron:install [--force]
   ```

Utilizzo `--force` per riscrivere un crontab esistente.

>[!INFO]
>
>- `magento cron:install` non riscrive un crontab esistente all&#39;interno di `#~ MAGENTO START` e `#~ MAGENTO END` commenti nella tua crontab.
>- `magento cron:install --force` non ha alcun effetto su alcun lavoro cron al di fuori dei commenti Commerce.


Per visualizzare il crontab, immettere il comando seguente come proprietario del file system:

```bash
crontab -l
```

Segue un esempio:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>La `update/cron.php` Il file è stato rimosso in Commerce 2.4.0 e, se presente nell’installazione, può essere rimosso in modo sicuro.
>
>Qualsiasi riferimento a `update/cron.php` e `bin/magento setup:cron:run` deve essere rimosso anche dalla crontab&#39;

### Rimuovi la scheda comparativa Commerce

È necessario rimuovere la scheda comparativa Commerce solo prima di disinstallare l’applicazione Commerce.

Per rimuovere la scheda comparativa Commerce:

1. Accedi come o passa al [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Passare alla directory di installazione Commerce.
1. Immetti il seguente comando:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Questo comando non ha alcun effetto sui lavori cron al di fuori del `#~ MAGENTO START` e `#~ MAGENTO END` commenti nella tua crontab.

## Esegui cron dalla riga di comando

Opzioni di comando:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

dove `--group` specifica il gruppo cron da eseguire (omette questa opzione per eseguire cron per tutti i gruppi)

Per eseguire il lavoro cron di indicizzazione, immetti:

```bash
bin/magento cron:run --group index
```

Per eseguire il lavoro cron predefinito, immetti:

```bash
bin/magento cron:run --group default
```

Per impostare i lavori e i gruppi predefiniti personalizzati, vedi [Configurare i lavori cron personalizzati e i gruppi cron](../cron/custom-cron.md).

>[!INFO]
>
>Devi eseguire il cron due volte: la prima volta che si scoprono le attività da eseguire e la seconda volta, per eseguire le attività stesse. La seconda esecuzione del cron deve essere eseguita su o dopo il `scheduled_at` tempo per ogni compito.

## Registrazione

Tutto `cron` le informazioni sul processo sono state spostate da `system.log` in un separato `cron.log`.
Per impostazione predefinita, le informazioni cron si trovano in `<install_directory>/var/log/cron.log`.
Tutte le eccezioni dai lavori cron sono registrate da `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Oltre all&#39;accesso `cron.log`:

- Processi non riusciti con `ERROR` e `MISSED` gli stati vengono registrati nel `<install_directory>/var/log/support_report.log`.

- Processi con un `ERROR` lo stato viene sempre registrato come `CRITICAL` in `<install_directory>/var/log/exception.log`.

- Processi con una `MISSED` stato registrato come `INFO` in `<install_directory>/var/log/debug.log` directory (solo modalità sviluppatore).

>[!INFO]
>
>Tutti i dati cron vengono scritti anche nel `cron_schedule` nel database Commerce. La tabella fornisce una cronologia dei lavori di cron, tra cui:
>
>- ID processo e codice
>- Stato
>- Data creazione
>- Data pianificata
>- Data di esecuzione
>- Data di fine
>
>Per visualizzare i record nella tabella, accedere al database Commerce nella riga di comando e immettere `SELECT * from cron_schedule;`.
