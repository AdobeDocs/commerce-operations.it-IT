---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Aggiorna sistema di build

**Per aggiornare il sistema di compilazione**:

1. Accedi al sistema di build come proprietario del file system.
1. Passare alla directory radice dell&#39;applicazione.

   ```shell
   cd <Magento root dir>
   ```

1. Estrarre le modifiche a `app/etc/config.php` dal controllo del codice sorgente.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Compila il codice.

   ```shell
   bin/magento setup:di:compile
   ```

1. Dopo la compilazione del codice, generare i file di visualizzazione statica.

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. Controllare le modifiche apportate al controllo del codice sorgente.

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
