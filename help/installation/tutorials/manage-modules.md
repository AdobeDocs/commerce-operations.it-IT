---
title: Abilitare o disabilitare i moduli
description: Per gestire i moduli Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Abilitare o disabilitare i moduli

Questo comando non ha prerequisiti.

## Stato del modulo

Utilizza il seguente comando per elencare i moduli abilitati e disabilitati:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Dove

* `--enabled` elenca tutti i moduli abilitati.
* `--disabled` elenca tutti i moduli disabilitati.
* `<module-list>` è un elenco di moduli delimitato da spazi per verificare lo stato. Se un nome di modulo contiene caratteri speciali, racchiuderlo tra virgolette singole o doppie.

>[!NOTE]
>
>Non puoi abilitare o disabilitare i moduli direttamente nei progetti cloud. È necessario eseguire questi comandi localmente e quindi inviare le modifiche al file `app/etc/config.php` per un ambiente. Vedi [Flusso di lavoro del progetto Pro: flusso di lavoro di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## Attivazione modulo, disattivazione

Per attivare o disattivare i moduli disponibili, utilizzare il comando seguente:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Dove

* `<module-list>` è un elenco delimitato da spazi di moduli da abilitare o disabilitare. Se un nome di modulo contiene caratteri speciali, racchiuderlo tra virgolette singole o doppie.
* `--all` per abilitare o disabilitare tutti i moduli contemporaneamente.
* `-f` o `--force` per forzare l&#39;abilitazione o la disabilitazione di un modulo nonostante le dipendenze. Prima di utilizzare questa opzione, vedere [Informazioni sull&#39;attivazione e la disattivazione dei moduli](#about-enabling-and-disabling-modules).
* `-c` o `--clear-static-content` pulisce [file di visualizzazione statica generati](../../configuration/cli/static-view-file-deployment.md).

  Se non si cancellano i file di visualizzazione statica, potrebbero verificarsi dei problemi se sono presenti più file con lo stesso nome e non si cancellano tutti.

  In altre parole, a causa delle [regole di fallback del file statico](../../configuration/cli/static-view-file-deployment.md), se non si cancellano i file statici e sono presenti più file denominati `logo.svg` diversi, il fallback potrebbe causare la visualizzazione del file errato.

Ad esempio, per disabilitare il modulo `Magento_Weee`, immettere:

```bash
bin/magento module:disable Magento_Weee
```

Per informazioni importanti sull&#39;attivazione e la disattivazione dei moduli, vedere [Informazioni sull&#39;attivazione e la disattivazione dei moduli](#about-enabling-and-disabling-modules).

## Aggiornare il database

Se sono stati attivati uno o più moduli, eseguire il comando seguente per aggiornare il database:

```bash
bin/magento setup:upgrade
```

Quindi pulisci la cache:

```bash
bin/magento cache:clean
```

## Informazioni sull&#39;attivazione e la disattivazione dei moduli

Adobe Commerce consente di abilitare o disabilitare i moduli attualmente disponibili, ovvero qualsiasi modulo fornito da Adobe o qualsiasi modulo di terze parti attualmente disponibile.

Alcuni moduli hanno dipendenze da altri moduli, nel qual caso potrebbe non essere possibile abilitare o disabilitare un modulo perché presenta dipendenze da altri moduli.

Inoltre, potrebbero essere presenti *moduli in conflitto* che non possono essere attivati entrambi contemporaneamente.

Esempi:

* Il modulo A dipende dal modulo B. È possibile disattivare il modulo B solo dopo aver prima disattivato il modulo A.

* Il modulo A dipende dal modulo B, entrambi disabilitati. È necessario abilitare il modulo B prima di abilitare il modulo A.

* Il modulo A è in conflitto con il modulo B. È possibile disabilitare i moduli A e B oppure disabilitare entrambi i moduli, ma *non è possibile* abilitare contemporaneamente i moduli A e B.

* Le dipendenze sono dichiarate nel campo `require` nel file Adobe Commerce `composer.json` per ciascun modulo. I conflitti sono dichiarati nel campo `conflict` nei file `composer.json` dei moduli. Queste informazioni vengono utilizzate per creare un grafico delle dipendenze: `A->B` significa che il modulo A dipende dal modulo B.

* Una *catena di dipendenze* è il percorso da un modulo a un altro. Ad esempio, se il modulo A dipende dal modulo B e il modulo B dipende dal modulo C, la catena di dipendenze è `A->B->C`.

Se tenti di abilitare o disabilitare un modulo che dipende da altri moduli, il grafico delle dipendenze viene visualizzato nel messaggio di errore.

>[!NOTE]
>
>È possibile che il modulo A `composer.json` dichiari un conflitto con il modulo B ma non viceversa.

*Solo riga di comando:* Per forzare l&#39;attivazione o la disattivazione di un modulo indipendentemente dalle dipendenze, utilizzare l&#39;argomento facoltativo `--force`.

>[!NOTE]
>
>L&#39;utilizzo di `--force` può disabilitare l&#39;archivio e causare problemi di accesso all&#39;amministratore.
