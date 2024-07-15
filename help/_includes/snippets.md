---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# Snippet

## Solo Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool] è disponibile solo per le istanze di Adobe Commerce.

<!-- Configuration guide snippets -->

## Proprietario file system {#file-system-owner}

>[!WARNING]
>
>Tutti i comandi CLI di Magento devono essere eseguiti dal [proprietario del file system](/help/configuration/cli/config-cli.md#prerequisites).

## Comandi di backup {#tip-backup-command}

>[!TIP]
>
>Il comando `support:backup` è _non_ lo stesso backup del codice eseguito dal comando `setup:backup`. Il comando `support:backup` ha lo scopo di eseguire il backup del codice per l&#39;esame da parte del supporto Adobe Commerce.

## Solo Adobe Commerce {#ee-only}

>[!NOTE]
>
>Questa funzione è disponibile solo per le istanze di Adobe Commerce.

## Dividi database obsoleto {#deprecate-split-db}

>[!IMPORTANT]
>
>La funzionalità del database diviso era [obsoleta](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) nella versione 2.4.2 di Adobe Commerce. Vedere [Ripristino da un database diviso a un singolo database](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Modifiche non compatibili con le versioni precedenti {#bics}

>[!NOTE]
>
>Le versioni di Adobe Commerce possono contenere modifiche non compatibili con le versioni precedenti (BIC). Per rivedere le modifiche non compatibili con le versioni precedenti, vedere [Riferimento BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). I principali problemi non compatibili con le versioni precedenti sono descritti in [Elementi di rilievo BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Non tutte le versioni introducono i principali BIC.

## Avviso CVE {#cve-notice}

>[!NOTE]
>
>A partire dalla versione 2.3.2, assegneremo e pubblicheremo i numeri CVE (Common Vulnerabilities and Exposures) indicizzati con ogni bug di sicurezza segnalato da parti esterne. Questo consente agli utenti di identificare più facilmente le vulnerabilità non risolte nella loro distribuzione. Ulteriori informazioni sugli identificatori CVE sono disponibili in [CVE](https://cve.mitre.org/).

## Altre informazioni sulla versione {#other-release-info}

>[!NOTE]
>
>Anche se il codice per i miglioramenti e le correzioni di bug descritti in queste note sulla versione è fornito in bundle con Adobe Commerce, molti di questi progetti (ad esempio, B2B, Page Builder e Progressive Web Application (PWA) Studio) vengono rilasciati in modo indipendente. Le correzioni di bug per questi progetti sono documentate nelle informazioni sulla versione specifiche per il progetto, disponibili nella documentazione di ciascun progetto. Consulta la [panoramica sulla versione del prodotto](/help/release/release-notes/overview.md).

## Controllo processo PHP {#php-process-control}

Prima di poter eseguire gli indicizzatori in modalità parallela, è necessario attivare il supporto Controllo processo (`pcntl`) in PHP. Vedi [Installazione](https://www.php.net/manual/en/pcntl.installation.php) nella documentazione di PHP.
