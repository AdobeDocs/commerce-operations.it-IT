---
source-git-commit: 1e3508e2e8e99d686dfa692415e2b4b41e8b80e8
workflow-type: tm+mt
source-wordcount: '726'
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
>Dopo aver installato questa patch di sicurezza, i commercianti B2B di Adobe Commerce devono effettuare l’aggiornamento alla versione più recente della patch di sicurezza B2B compatibile. Consulta le [note sulla versione B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes).

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

## Dichiarazione di non responsabilità Alpha {#alpha}

>[!IMPORTANT]
>
>[Le versioni di Alpha](/help/release/versioning-policy.md#alpha-patch-release) potrebbero essere incomplete e potrebbero contenere difetti. Vengono fornite &quot;COSÌ COM’È&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni di Alpha. I clienti non devono fare affidamento sul corretto funzionamento o sulle prestazioni delle versioni di Alpha o di qualsiasi documentazione o materiale ad esse allegato. L’utilizzo delle versioni di Alpha è interamente a rischio del cliente.

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

## Patch personalizzate {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe non supporta l’applicazione di patch ufficiali fornite da Adobe utilizzando questo metodo. Utilizza il seguente metodo a proprio rischio e pericolo. Per applicare patch ufficiali, utilizzare [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Eseguire sempre test completi prima di distribuire qualsiasi patch personalizzata.

## Backport delle patch di sicurezza di ottobre 2025 {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **Migra da TinyMCE a Hugerte.org**

  A causa della fine del supporto per TinyMCE 5 e 6 e delle incompatibilità di licenza con TinyMCE 7, l&#39;implementazione corrente dell&#39;editor WYSIWYG di Adobe Commerce è stata migrata da TinyMCE all&#39;editor [HugeRTE open-source](https://hugerte.org/).

  Questa migrazione garantisce che Adobe Commerce rimanga conforme alle licenze open source, evita le vulnerabilità TinyMCE 6 note e offre un’esperienza di modifica moderna e supportata per commercianti e sviluppatori.

* **Aggiunto supporto per il protocollo Apache ActiveMQ Artemis STOMP**

  È stato aggiunto il supporto per il gestore di messaggi open source ActiveMQ Artemis tramite il protocollo STOMP (Simple Text Oriented Messaging Protocol). Fornisce un sistema di messaggistica affidabile e scalabile, offrendo flessibilità per le integrazioni basate su STOMP. Vedi [Apache ActiveMQ Artemis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp) nella *Guida alla configurazione di Commerce*.

## Impossibile caricare static.min.js e mixins.min.js nella pagina di estrazione {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

Dopo le recenti modifiche CSP/SRI, la pagina di pagamento non carica static.min.js e mixins.min.js quando le funzioni di bundling e minimizzazione di JavaScript sono entrambe abilitate in modalità di produzione. Di conseguenza, i mixin RequireJS non vengono eseguiti e i modelli di estrazione non vengono risolti (ad esempio, `"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`).

**Soluzione alternativa**:

* Disattivare il bundling JavaScript; o
* Se mantieni abilitato il bundling di JavaScript, disabilita la minimizzazione di JavaScript.

>[!IMPORTANT]
>
>Non disabilitare i CSP o rimuovere le protezioni SRI in produzione. Qualsiasi bypass a livello di plug-in deve essere utilizzato solo come ultima risorsa per un hotfix e deve essere rivisto dal team di sicurezza.

**Hotfix**:

È disponibile un hotfix. Vedere [Estrazione non riuscita quando la minimizzazione JS e il bundling sono abilitati](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27997) nella Knowledge Base per i dettagli della patch.
