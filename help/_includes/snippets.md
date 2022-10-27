---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# Frammenti

## Solo Commerce {#commerce-only}

>[!NOTE]
>
>La [!DNL Upgrade Compatibility Tool] è disponibile solo per le istanze Adobe Commerce.

<!-- Configuration guide snippets -->

## Proprietario del file system {#file-system-owner}

>[!WARNING]
>
>Tutti i comandi CLI del Magento devono essere eseguiti dal [proprietario del file system](/help/configuration/cli/config-cli.md#prerequisites).

## Comandi di backup {#tip-backup-command}

>[!TIP]
>
>La `support:backup` comando _not_ lo stesso backup del codice eseguito da `setup:backup` comando. La `support:backup` Il comando è destinato a eseguire il backup del codice per l&#39;esame da parte del supporto Adobe Commerce.

## Solo Adobe Commerce {#ee-only}

>[!NOTE]
>
>Questa funzione è disponibile solo per le istanze Adobe Commerce.

## Dividi database obsoleto {#deprecate-split-db}

>[!IMPORTANT]
>
>La funzionalità del database diviso era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) nella versione 2.4.2 di Adobe Commerce. Vedi [Ripristino da un database diviso a un singolo database](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifiche incompatibili con le versioni precedenti {#bics}

>[!NOTE]
>
>Le versioni Adobe Commerce e Magenti Open Source possono contenere modifiche non compatibili con le versioni precedenti (BIC). Per esaminare le modifiche incompatibili con le versioni precedenti, consulta [Riferimento BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). I principali problemi con le versioni precedenti sono descritti in [Elementi di rilievo del BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Non tutte le versioni introducono BIC importanti.

## Avviso CVE {#cve-notice}

>[!NOTE]
>
>A partire dalla versione 2.3.2, assegneremo e pubblicheremo i numeri CVE (Common Vulnerability and Exposure) indicizzati con ogni bug di sicurezza segnalato da soggetti esterni. Questo consente agli utenti di identificare più facilmente le vulnerabilità non risolte nella loro distribuzione. Per ulteriori informazioni sugli identificatori CVE, visita [CVE](https://cve.mitre.org/).
