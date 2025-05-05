---
source-git-commit: 9eeb0e3a1c75b25cc70b092d23f02ebfe355d6bd
workflow-type: tm+mt
source-wordcount: '377'
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

## Patch B2B {#b2b-patches}

>[!NOTE]
>
>Dopo aver installato questa patch di sicurezza, i commercianti B2B di Adobe Commerce devono effettuare l’aggiornamento alla versione più recente della patch di sicurezza B2B compatibile. Consulta le [note sulla versione B2B](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/release-notes).

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
>Le versioni di Adobe Commerce possono contenere modifiche non compatibili con le versioni precedenti (BIC). Per rivedere le modifiche non compatibili con le versioni precedenti, vedere [Riferimento BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). I principali problemi non compatibili con le versioni precedenti sono descritti in [Elementi di rilievo BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Non tutte le versioni introducono i principali BIC.

## Dichiarazione di non responsabilità Beta {#beta}

>[!IMPORTANT]
>
>I rilasci di Beta possono contenere difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (dai servizi di supporto Adobe o da qualsiasi altro servizio) le versioni beta. I clienti devono usare cautela e non fare affidamento in alcun modo sul corretto funzionamento o sulle prestazioni delle versioni beta e/o di qualsiasi documentazione o materiale di accompagnamento. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

## Avviso CVE {#cve-notice}

>[!NOTE]
>
>A partire dalla versione 2.3.2, assegneremo e pubblicheremo i numeri CVE (Common Vulnerabilities and Exposures) indicizzati con ogni bug di sicurezza segnalato da parti esterne. Questo consente agli utenti di identificare più facilmente le vulnerabilità non risolte nella loro distribuzione. Ulteriori informazioni sugli identificatori CVE sono disponibili in [CVE](https://cve.mitre.org/).

## Altre informazioni sulla versione {#other-release-info}

>[!NOTE]
>
>Anche se il codice per i miglioramenti e le correzioni di bug descritti in queste note sulla versione è fornito in bundle con Adobe Commerce, molti di questi progetti (ad esempio, B2B, Page Builder e Progressive Web Applications (PWA) Studio) vengono rilasciati in modo indipendente. Le correzioni di bug per questi progetti sono documentate nelle informazioni sulla versione specifiche per il progetto, disponibili nella documentazione di ciascun progetto. Consulta la [panoramica sulla versione del prodotto](/help/release/release-notes/overview.md).

## Controllo processo PHP {#php-process-control}

Prima di poter eseguire gli indicizzatori in modalità parallela, è necessario attivare il supporto Controllo processo (`pcntl`) in PHP. Vedi [Installazione](https://www.php.net/manual/en/pcntl.installation.php) nella documentazione di PHP.
