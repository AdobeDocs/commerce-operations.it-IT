---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Aggiorna la configurazione condivisa

**Per aggiornare la configurazione**:

1. Accedi al tuo sistema di sviluppo come proprietario del file system o passa a tale proprietario.

1. Passa alla radice dell&#39;applicazione ed esegui il comando dump.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Ad esempio, se Commerce è installato in `/var/www/html/magento2`, immetti:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Conferma che `app/etc/config.php` è stato aggiornato.

   ```bash
   git status
   ```

   Risposta di esempio:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Do _not_ invia modifiche al `generated`, `pub/media`oppure `pub/static` directory al controllo del codice sorgente. Questi file vengono generati sul sistema di compilazione. Il sistema di sviluppo ha probabilmente codici, temi e così via che non sono pronti per l&#39;uso sul sistema di produzione.

1. Archivia le modifiche apportate a `app/etc/config.php` solo al controllo del codice sorgente.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
