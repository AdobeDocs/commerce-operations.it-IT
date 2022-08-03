---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Aggiorna il sistema di compilazione

**Per aggiornare il sistema di compilazione**:

1. Accedi al sistema di compilazione come proprietario del file system.
1. Passa alla directory principale dell&#39;applicazione.

   ```bash
   cd <Magento root dir>
   ```

1. Recupera le modifiche apportate a `app/etc/config.php` dal controllo del codice sorgente.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Compila il codice.

   ```bash
   bin/magento setup:di:compile
   ```

1. Dopo aver compilato il codice, genera file di visualizzazione statici.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Controlla le modifiche nel controllo del codice sorgente.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
