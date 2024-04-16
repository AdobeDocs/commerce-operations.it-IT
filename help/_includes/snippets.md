---
source-git-commit: f7db6b65d74c605976a3a338c98eebda2dc46a43
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# Snippet

## Solo Commerce {#commerce-only}

>[!NOTE]
>
>Il [!DNL Upgrade Compatibility Tool] è disponibile solo per le istanze di Adobe Commerce.

<!-- Configuration guide snippets -->

## Proprietario file system {#file-system-owner}

>[!WARNING]
>
>Tutti i comandi CLI di Magento devono essere eseguiti dal [proprietario del file system](/help/configuration/cli/config-cli.md#prerequisites).

## Comandi di backup {#tip-backup-command}

>[!TIP]
>
>Il `support:backup` il comando è _non_ lo stesso backup del codice eseguito da `setup:backup` comando. Il `support:backup` Il comando ha lo scopo di eseguire il backup del codice per l&#39;esame da parte del supporto Adobe Commerce.

## Solo Adobe Commerce {#ee-only}

>[!NOTE]
>
>Questa funzione è disponibile solo per le istanze di Adobe Commerce.

## Dividi database obsoleto {#deprecate-split-db}

>[!IMPORTANT]
>
>La funzionalità di suddivisione del database era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) nella versione 2.4.2 di Adobe Commerce. Consulta [Ripristino da un database diviso a un singolo database](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifiche non compatibili con le versioni precedenti {#bics}

>[!NOTE]
>
>Le versioni di Adobe Commerce possono contenere modifiche non compatibili con le versioni precedenti (BIC, back-incompatible changes). Per esaminare le modifiche non compatibili con le versioni precedenti, vedere [Riferimento BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). I principali problemi di incompatibilità con le versioni precedenti sono descritti in [Elementi di rilievo BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Non tutte le versioni introducono i principali BIC.

## Avviso CVE {#cve-notice}

>[!NOTE]
>
>A partire dalla versione 2.3.2, assegneremo e pubblicheremo i numeri CVE (Common Vulnerabilities and Exposures) indicizzati con ogni bug di sicurezza segnalato da parti esterne. Questo consente agli utenti di identificare più facilmente le vulnerabilità non risolte nella loro distribuzione. Per ulteriori informazioni sugli identificatori CVE, consulta [CVE](https://cve.mitre.org/).

## Altre informazioni sulla versione {#other-release-info}

>[!NOTE]
>
>Anche se il codice per i miglioramenti e le correzioni di bug descritti in queste note sulla versione è fornito in bundle con Adobe Commerce, molti di questi progetti (ad esempio, B2B, Page Builder e Progressive Web Application (PWA) Studio) vengono rilasciati in modo indipendente. Le correzioni di bug per questi progetti sono documentate nelle informazioni sulla versione specifiche per il progetto, disponibili nella documentazione di ciascun progetto. Consulta [panoramica sulla versione del prodotto](/help/release/release-notes/overview.md).

## Controllo processo PHP {#php-process-control}

Prima di poter eseguire gli indicizzatori in modalità parallela, è necessario attivare il supporto di Controllo processo (`pcntl`) in PHP. Consulta [Installazione](https://www.php.net/manual/en/pcntl.installation.php) nella documentazione PHP.
