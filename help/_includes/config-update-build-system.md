---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Aggiorna sistema di build

**Per aggiornare il sistema di build**:

1. Accedi al sistema di build come proprietario del file system.
1. Passare alla directory radice dell&#39;applicazione.

   ```bash
   cd <Magento root dir>
   ```

1. Richiama le modifiche in `app/etc/config.php` dal controllo del codice sorgente.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Compila il codice.

   ```bash
   bin/magento setup:di:compile
   ```

1. Dopo la compilazione del codice, generare i file di visualizzazione statica.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Controllare le modifiche apportate al controllo del codice sorgente.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
