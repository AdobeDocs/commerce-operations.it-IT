---
title: Utilizzo
description: Scopri come utilizzare il [!DNL Quality Patches Tool].
source-git-commit: 9e719cdf888caa3fa34f6416650e62bbf1b81175
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Utilizzo

La [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) offre patch individuali sviluppate dall&#39;Adobe e la comunità del Magento Open Source. Consente di applicare, ripristinare e visualizzare informazioni generali su tutte le singole patch disponibili per la versione installata di Adobe Commerce o Magento Open Source. È possibile applicare patch ai progetti Adobe Commerce e Magenti Open Source indipendentemente da chi ha sviluppato la patch. Ad esempio, puoi applicare una patch sviluppata dalla community ai progetti Adobe Commerce.


Guarda questo [video tecnico](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) e scopri come utilizzare lo strumento Quality Patch per Adobe Commerce e Magenti Open Source.

>[!INFO]
>
>Vedi [Applicare singole patch](#apply-individual-patches) per istruzioni su come applicare patch ai progetti Adobe Commerce o Magenti Open Source. Vedi [Patch disponibili](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) per rivedere un elenco completo delle patch rilasciate.

>[!WARNING]
>
>Si sconsiglia di utilizzare il [!DNL Quality Patches Tool] per applicare un numero elevato di patch in quanto aumenta la complessità del codice e rende più difficile l’aggiornamento a una nuova versione.

## Installa

>[!INFO]
>
>Se non è già installato, è necessario installare [[!DNL Git]](https://github.com/git-guides/install-git) o [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) prima di installare [!DNL Quality Patches Tool]. Aggiungi il `magento/quality-patches` Pacchetto Compositore per il tuo `composer.json` file:

```bash
composer require magento/quality-patches
```

## Visualizzare singole patch

Per visualizzare l’elenco delle singole patch disponibili per la versione di Adobe Commerce o Magento Open Source in uso:

```bash
./vendor/bin/magento-patches status
```

Verrà visualizzato un output simile al seguente:

| Id | Titolo | Tipo | Stato | Dettagli |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC viene disattivato durante le distribuzioni | Facoltativo | Non applicato | Componenti interessati:<br> - magento/module-page-cache |
| MCLOUD-5650 | Blocca la configurazione di distribuzione dopo la lettura del file | Facoltativo | Non applicato | Componenti interessati:<br> - magento/framework |
| MCLOUD-5684 | Impaginazione Non funzionante - product_list_limit=all | Facoltativo | Non applicato | Componenti interessati: - magento/modulo-elasticsearch |
| MCLOUD-5837 | Correggere il problema del load balancer | Obsoleto | Applicato | Sostituzione consigliata: MC-1 <br> Componenti interessati: - magento/framework |
| BUNDLE-2554 | Imposta bug di informazioni di pagamento | Facoltativo | Non applicato | Componenti interessati: <br>- modulo amzn/amazon-pay |
| MC-1 | Problema di correzione 1 | Facoltativo | Applicato | Componenti interessati: <br> - magento/module-cms |
| MC-2 | Problema di correzione 2 | Facoltativo | Non applicato | Componenti interessati: <br> - magento/module-cms |
| MC-3 | Problema di correzione 3 | Facoltativo | Non applicato | Patch richieste:<br> - MC-2 <br>Componenti interessati: <br>- magento/module-cms |
| MC-3-V2 | Correzione aggiornata per il problema 3, sostituisce la patch MC-3 | Facoltativo | N/D | Componenti interessati:  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

La tabella di stato include:

- **Tipo**:
   - `Optional` — Tutte le patch dal [!DNL Quality Patches Tool] e [Patch cloud](https://devdocs.magento.com/cloud/project/project-patch.html) Il pacchetto è facoltativo per le installazioni Adobe Commerce e Magenti Open Source.
   - `Deprecated` — Adobe ha dichiarato obsoleta la singola patch. Se hai applicato la patch, ti consigliamo di ripristinarla. L&#39;operazione di ripristino rimuove anche la patch dalla tabella di stato.

- **Stato**:
   - `Applied` — La patch è stata applicata.
   - `Not applied` — La patch non è stata applicata.
   - `N/A` — Lo stato della patch non può essere definito a causa di conflitti.

- **Dettagli**:
   - `Affected components` — Elenco dei moduli interessati.
   - `Required patches` — L&#39;elenco di patch che devono essere applicate affinché una patch indicata funzioni correttamente (dipendenze).
   - `Recommended replacement` — La patch che rappresenta una sostituzione consigliata per una patch obsoleta.

>[!INFO]
>
>Dopo l’aggiornamento a una nuova versione di Adobe Commerce o Magenti Open Source, è necessario riapplicare le patch se queste non sono incluse nella nuova versione. Vedi [Riapplicare le patch dopo un aggiornamento](#re-apply-patches-after-an-upgrade).

## Applicare singole patch {#apply-individual-patches}

>[!WARNING]
>
>È consigliabile testare tutte le patch in un ambiente di staging o di sviluppo prima della distribuzione in produzione. Si consiglia inoltre di eseguire il backup dei dati prima di applicare una patch. Vedi [Eseguire il backup e il rollback del file system](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Per applicare una singola patch, eseguire il comando seguente dove `MAGETWO-XXXX` è l&#39;ID patch specificato nella tabella di stato:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Puoi anche applicare più patch contemporaneamente separando ogni ID patch aggiuntivo con uno spazio:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

È necessario pulire la cache dopo aver applicato le patch per visualizzare le modifiche nell’applicazione Adobe Commerce:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Considera la possibilità di mantenere un elenco di patch applicate in una posizione separata. Potrebbe essere necessario riapplicare alcune di esse dopo l’aggiornamento a una nuova versione di Adobe Commerce o Magento Open Source. Vedi [Riapplicare le patch dopo un aggiornamento](#re-apply-patches-after-an-upgrade).

## Ripristino di singole patch

>[!WARNING]
>
>È consigliabile testare tutte le patch in un ambiente di staging o di sviluppo prima della distribuzione in produzione. Si consiglia inoltre di eseguire il backup dei dati prima di applicare una patch. Vedi [Eseguire il backup e il rollback del file system](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Per ripristinare una singola patch, eseguire il comando seguente dove `MAGETWO-XXXX` è l&#39;ID patch specificato nella tabella di stato:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Inoltre, puoi ripristinare più patch contemporaneamente separando ogni ID patch aggiuntivo con uno spazio:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Per ripristinare tutte le patch applicate:

```bash
./vendor/bin/magento-patches revert --all
```

Per visualizzare le modifiche nell’applicazione Adobe Commerce, è necessario pulire la cache dopo aver ripristinato le patch:

```bash
./bin/magento cache:clean
```

## Aggiornamenti

Adobe Commerce rilascia periodicamente nuove patch individuali. È necessario aggiornare [!DNL Quality Patches Tool] per ottenere nuove patch individuali:

```bash
composer update magento/quality-patches
```

Visualizza le patch aggiunte:

>[!TIP]
>
>Le nuove patch aggiunte vengono visualizzate nella parte inferiore della tabella.

```bash
./vendor/bin/magento-patches status
```

## Riapplicare le patch dopo un aggiornamento {#re-apply-patches-after-an-upgrade}

Quando esegui l’aggiornamento a una nuova versione di Adobe Commerce o Magenti Open Source, devi riapplicare le patch se queste non sono incluse nella nuova versione.

Per riapplicare le patch:

1. Aggiorna [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Apri l’elenco delle patch precedentemente applicate, consigliato in [Applicare singole patch](#apply-individual-patches).

1. Applica le patch:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   La best practice consiste nell’applicare le patch una alla volta.

1. Pulisci la cache:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Quando esegui la `status` le patch incluse nella nuova versione non vengono più visualizzate nella tabella delle patch disponibili.

## Registrazione

La [!DNL Quality Patches Tool] registra tutte le operazioni nel `<Magento_root>/var/log/patch.log` file.
