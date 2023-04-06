---
title: Attivare o disattivare i moduli
description: Segui questi passaggi per gestire i moduli Adobe Commerce o Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---


# Attivare o disattivare i moduli

Questo comando non ha prerequisiti.

## Stato del modulo

Utilizzare il seguente comando per elencare i moduli abilitati e disabilitati:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Dove

* `--enabled` elenca tutti i moduli abilitati.
* `--disabled` elenca tutti i moduli disabilitati.
* `<module-list>` è un elenco di moduli delimitato da spazi per controllare lo stato. Se un nome di modulo contiene caratteri speciali, racchiudi il nome tra virgolette singole o doppie.

## Attiva modulo, disattiva

Per attivare o disattivare i moduli disponibili, utilizzare il comando seguente:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Dove

* `<module-list>` è un elenco delimitato da spazi di moduli da attivare o disattivare. Se un nome di modulo contiene caratteri speciali, racchiudi il nome tra virgolette singole o doppie.
* `--all` per attivare o disattivare tutti i moduli contemporaneamente.
* `-f` o `--force` per forzare l’attivazione o la disattivazione di un modulo nonostante le dipendenze. Prima di utilizzare questa opzione, consulta [Informazioni sull’abilitazione e la disabilitazione dei moduli](#about-enabling-and-disabling-modules).
* `-c` o `--clear-static-content` pulizie [file di visualizzazione statica generati](../../configuration/cli/static-view-file-deployment.md).

   Se non si cancellano i file di visualizzazione statica, potrebbero verificarsi problemi se sono presenti più file con lo stesso nome e non vengono cancellati tutti.

   In altre parole, a causa del [fallback del file statico](../../configuration/cli/static-view-file-deployment.md) regole, se non si cancellano i file statici ed è presente più di un file denominato `logo.svg` che sono diversi, il fallback potrebbe causare la visualizzazione del file errato.

Ad esempio, per disabilitare il `Magento_Weee` modulo, immetti:

```bash
bin/magento module:disable Magento_Weee
```

Per informazioni importanti sull’abilitazione e la disattivazione dei moduli, consulta [Informazioni sull’abilitazione e la disabilitazione dei moduli](#about-enabling-and-disabling-modules).

## Aggiornare il database

Se hai abilitato uno o più moduli, esegui il comando seguente per aggiornare il database:

```bash
bin/magento setup:upgrade
```

Quindi pulisci la cache:

```bash
bin/magento cache:clean
```

## Informazioni sull’abilitazione e la disabilitazione dei moduli

Adobe Commerce e Magenti Open Source consentono di abilitare o disabilitare i moduli attualmente disponibili; in altre parole, qualsiasi modulo fornito da Adobe o qualsiasi modulo di terze parti attualmente disponibile.

Alcuni moduli hanno dipendenze da altri moduli, nel qual caso potrebbe non essere possibile abilitare o disabilitare un modulo perché ha dipendenze da altri moduli.

Inoltre, potrebbe essere *in conflitto* moduli che non possono essere abilitati contemporaneamente.

Esempi:

* Il modulo A dipende dal modulo B. Non è possibile disabilitare il modulo B a meno che non si disattivi prima il modulo A.

* Il modulo A dipende dal modulo B, entrambi disattivati. È necessario attivare il modulo B prima di attivare il modulo A.

* Il modulo A è in conflitto con il modulo B. È possibile disabilitare il modulo A e il modulo B, oppure è possibile disabilitare entrambi i moduli, ma è possibile *impossibile* attivare contemporaneamente il modulo A e il modulo B.

* Le dipendenze vengono dichiarate nella variabile `require` in Adobe Commerce e nel Magento Open Source `composer.json` file per ciascun modulo. I conflitti sono dichiarati nella `conflict` campo nei moduli&quot; `composer.json` file. Usiamo queste informazioni per creare un grafico delle dipendenze: `A->B` significa che il modulo A dipende dal modulo B.

* A *catena di dipendenza* è il percorso da un modulo a un altro. Ad esempio, se il modulo A dipende dal modulo B e il modulo B dipende dal modulo C, la catena di dipendenza è `A->B->C`.

Se tenti di abilitare o disabilitare un modulo che dipende da altri moduli, il grafico della dipendenza viene visualizzato nel messaggio di errore.

>[!NOTE]
>
>È possibile che il modulo A sia `composer.json` dichiara un conflitto con il modulo B ma non viceversa.

*Solo riga di comando:* Per forzare l’abilitazione o la disattivazione di un modulo indipendentemente dalle sue dipendenze, utilizza l’ `--force` argomento.

>[!NOTE]
>
>Utilizzo `--force` può disattivare l&#39;archivio e causare problemi nell&#39;accesso all&#39;amministratore.
