---
title: Utilizzo
description: Scopri come utilizzare  [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Utilizzo

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) distribuisce singole patch sviluppate da Adobe e dalla community Magento Open Source. Consente di applicare, ripristinare e visualizzare informazioni generali su tutte le singole patch disponibili per la versione installata di Adobe Commerce. Puoi applicare le patch ai progetti Adobe Commerce indipendentemente da chi l’ha sviluppata. Ad esempio, puoi applicare ai progetti Adobe Commerce una patch sviluppata dalla community.

Guarda questo [video tecnico](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) e scopri come utilizzare lo strumento Quality Patches per Adobe Commerce.

>[!INFO]
>
>Consulta [Applicare singole patch](#apply-individual-patches) per istruzioni sull&#39;applicazione delle patch ai progetti Adobe Commerce. Vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) per esaminare un elenco completo delle patch rilasciate.

>[!WARNING]
>
>Si consiglia di non utilizzare [!DNL Quality Patches Tool] per applicare un numero elevato di patch, in quanto aumenta la complessità del codice e rende più difficile l&#39;aggiornamento a una nuova versione.

## Installa

>[!INFO]
>
>Se non è già installato, installare [[!DNL Git]](https://github.com/git-guides/install-git) o [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) prima di installare [!DNL Quality Patches Tool]. Aggiungere il pacchetto Compositore `magento/quality-patches` al file `composer.json`:

```bash
composer require magento/quality-patches
```

## Visualizzare singole patch

Per visualizzare l’elenco delle singole patch disponibili per la tua versione di Adobe Commerce:

```bash
./vendor/bin/magento-patches status
```

L’output sarà simile al seguente:

| ID | Titolo | Tipo | Stato | Dettagli |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC viene disabilitato durante le distribuzioni | Facoltativo | Non applicato | Componenti interessati:<br> - magento/module-page-cache |
| MCLOUD-5650 | Mantieni la configurazione di distribuzione dopo la lettura dal file | Facoltativo | Non applicato | Componenti interessati:<br> - magento/framework |
| MCLOUD-5684 | Paginazione non funzionante - product_list_limit=all | Facoltativo | Non applicato | Componenti interessati: - magento/module-elasticsearch |
| MCLOUD-5837 | Correggi il problema del load balancer | Obsoleto | Applicato | Sostituzione consigliata: MC-1 <br> Componenti interessati: - magento/framework |
| BUNDLE-2554 | Imposta bug informazioni pagamento | Facoltativo | Non applicato | Componenti interessati: <br>- amzn/amazon-pay-module |
| MC-1 | Correzioni del problema 1 | Facoltativo | Applicato | Componenti interessati: <br> - magento/module-cms |
| MC-2 | Correzioni del problema 2 | Facoltativo | Non applicato | Componenti interessati: <br> - magento/module-cms |
| MC-3 | Correzioni del problema 3 | Facoltativo | Non applicato | Patch richieste:<br> - MC-2 <br>Componenti interessati: <br>- magento/module-cms |
| MC-3-V2 | È stata aggiornata la correzione per il problema 3 e sostituisce la patch MC-3. | Facoltativo | N/D | Componenti interessati: <br>- magento/module-cms |

Adobe Commerce 2.3.5.

La tabella di stato include:

- **Tipo**:
   - `Optional` — Tutte le patch del pacchetto [!DNL Quality Patches Tool] e del pacchetto [Commerce on Cloud Infrastructure Guide > Apply patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) sono facoltative per le installazioni di Adobe Commerce.
   - `Deprecated` — Adobe ha dichiarato obsoleta la singola patch. Se ha applicato la patch, si consiglia di ripristinarla. L’operazione di ripristino rimuove anche la patch dalla tabella di stato.

- **Stato**:
   - `Applied` - La patch è stata applicata.
   - `Not applied` - La patch non è stata applicata.
   - `N/A` - Impossibile definire lo stato della patch a causa di conflitti.

- **Dettagli**:
   - `Affected components` — Elenco dei moduli interessati.
   - `Required patches` — Elenco di patch che devono essere applicate affinché una patch indicata funzioni correttamente (dipendenze).
   - `Recommended replacement` — La patch che si consiglia di sostituire con una patch obsoleta.

>[!INFO]
>
>Dopo l&#39;aggiornamento a una nuova versione di Adobe Commerce, è necessario riapplicare le patch se non sono incluse nella nuova versione. Vedi [Riapplicare le patch dopo un aggiornamento](#re-apply-patches-after-an-upgrade).

## Applicare singole patch {#apply-individual-patches}

>[!WARNING]
>
>È consigliabile eseguire il test di tutte le patch in un ambiente di staging o di sviluppo prima di distribuirle in produzione. Si consiglia inoltre di eseguire il backup dei dati prima di applicare una patch. Consulta [Eseguire il backup e il rollback del file system, del supporto e del database](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Per applicare una singola patch, eseguire il comando seguente dove `MAGETWO-XXXX` è l&#39;ID patch specificato nella tabella di stato:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Puoi anche applicare più patch contemporaneamente separando ogni ID patch aggiuntivo con uno spazio:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Per visualizzare le modifiche nell’applicazione Adobe Commerce, pulisci la cache dopo aver applicato le patch:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Prendere in considerazione la possibilità di mantenere un elenco di patch applicate in una posizione separata. Potrebbe essere necessario riapplicarne alcuni dopo l’aggiornamento a una nuova versione di Adobe Commerce. Vedi [Riapplicare le patch dopo un aggiornamento](#re-apply-patches-after-an-upgrade).

## Ripristinare singole patch

>[!WARNING]
>
>È consigliabile eseguire il test di tutte le patch in un ambiente di staging o di sviluppo prima di distribuirle in produzione. Si consiglia inoltre di eseguire il backup dei dati prima di applicare una patch. Consulta [Eseguire il backup e il rollback del file system, del supporto e del database](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Per ripristinare una singola patch, eseguire il comando seguente dove `MAGETWO-XXXX` è l&#39;ID patch specificato nella tabella di stato:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Inoltre, è possibile ripristinare più patch contemporaneamente separando ogni ID patch aggiuntivo con uno spazio:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Per ripristinare tutte le patch applicate:

```bash
./vendor/bin/magento-patches revert --all
```

Per visualizzare le modifiche nell’applicazione Adobe Commerce, pulisci la cache dopo il ripristino delle patch:

```bash
./bin/magento cache:clean
```

## Ottieni aggiornamenti

Adobe Commerce rilascia periodicamente nuove patch singole. È necessario aggiornare [!DNL Quality Patches Tool] per ottenere nuove patch singole:

```bash
composer update magento/quality-patches
```

Visualizzare le patch aggiunte:

>[!TIP]
>
>Le nuove patch di aggiunta vengono visualizzate nella parte inferiore della tabella.

```bash
./vendor/bin/magento-patches status
```

## Riapplicare le patch dopo un aggiornamento {#re-apply-patches-after-an-upgrade}

Quando esegui l’aggiornamento a una nuova versione di Adobe Commerce, devi riapplicare le patch se non sono incluse nella nuova versione.

Per riapplicare le patch:

1. Aggiorna [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Aprire l&#39;elenco delle patch applicate in precedenza, consigliato in [Applicare singole patch](#apply-individual-patches).

1. Applicare le patch:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   La best practice prevede l’applicazione di patch una alla volta.

1. Pulisci la cache:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Quando si esegue il comando `status`, le patch incluse nella nuova versione non vengono più visualizzate nella tabella delle patch disponibili.

## Registrazione

[!DNL Quality Patches Tool] registra tutte le operazioni nel file `<Magento_root>/var/log/patch.log`.
