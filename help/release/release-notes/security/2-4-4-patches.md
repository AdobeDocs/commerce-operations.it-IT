---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.4
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 770986607b550d876a7afdf371a340ebae11eb99
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.4

{{$include /help/_includes/release-notes/security-patch-intro.md}}

>[!NOTE]
>
>Le patch di sicurezza per il supporto esteso per la versione 2.4.4 sono disponibili solo per i clienti Adobe Commerce. Queste patch non sono disponibili per la base di codice di Magento Open Source. Consulta [Supporto esteso](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).

## 2.4.4-p15

Adobe Commerce 2.4.4-p15 è una versione di sicurezza del supporto esteso che fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4. È disponibile solo per i clienti Adobe Commerce.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.4-p14

Adobe Commerce 2.4.4-p14 è una versione di sicurezza del supporto esteso che fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4. È disponibile solo per i clienti Adobe Commerce.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

* **Miglioramento delle prestazioni API**—Risolve il peggioramento delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la precedente patch di sicurezza.<!-- AC-14078 -->

* **Correzione accesso a CMS Blocks**—Risolve un problema che impediva agli utenti amministratori con autorizzazioni limitate (ad esempio l&#39;accesso solo merchandising) di visualizzare la pagina dell&#39;elenco [!UICONTROL CMS Blocks].

  In precedenza, questi utenti avevano riscontrato un errore a causa di parametri di configurazione mancanti dopo l&#39;installazione delle patch di sicurezza precedenti.<!-- AC-14087 -->

* **Compatibilità limite cookie**—Risolve una modifica incompatibile con le versioni precedenti che coinvolge la costante `MAX_NUM_COOKIES` nel framework. Questo aggiornamento ripristina il comportamento previsto e garantisce la compatibilità per le estensioni o personalizzazioni che interagiscono con i limiti dei cookie.<!-- AC-14475 -->

* **Operazioni asincrone**—Operazioni asincrone limitate per l&#39;override degli ordini dei clienti precedenti.<!-- AC-13917 -->

## 2.4.4-p13

La versione di sicurezza Adobe Commerce 2.4.4-p13 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-26](https://helpx.adobe.com/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

La versione di sicurezza di Adobe Commerce 2.4.4-p12 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-08](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

La versione di sicurezza Adobe Commerce 2.4.4-p11 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

La versione di sicurezza Adobe Commerce 2.4.4-p10 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-61](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

La versione di sicurezza Adobe Commerce 2.4.4-p9 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Applica hotfix per CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Aggiornamenti della piattaforma

* **Supporto di MariaDB 10.5**. Questa versione patch introduce la compatibilità con MariaDB versione 10.5. Adobe Commerce è ancora compatibile con MariaDB versione 10.4, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.4-p9 e tutte le prossime versioni delle patch di sicurezza 2.4.4 solo con MariaDB versione 10.5 perché la manutenzione di MariaDB 10.4 termina il 18 giugno 2024. <!--AC-11530-->

### In evidenza

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

La versione di sicurezza Adobe Commerce 2.4.4-p8 fornisce correzioni di bug di sicurezza per la distribuzione Adobe Commerce 2.4.4. Questi aggiornamenti correggono le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

La versione di sicurezza di Adobe Commerce 2.4.4-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### In evidenza

Questa versione introduce due miglioramenti significativi per la sicurezza:

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi di direttiva del modello o i metodi `setCacheKey` o `setData`.
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_). <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare la nuova opzione di configurazione **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per controllare questo nuovo limite. <!-- AC-8753 -->

## 2.4.4-p6

La versione di sicurezza Adobe Commerce 2.4.4-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

### In evidenza

Questa versione introduce una nuova impostazione di configurazione della cache di pagina intera che consente di attenuare i rischi associati all&#39;endpoint `{BASE-URL}/page_cache/block/esi HTTP`. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. La nuova impostazione di configurazione **[!UICONTROL Handles Param]** imposta il valore del parametro `handles` di questo endpoint, che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. I commercianti possono modificare questo valore dall&#39;amministratore (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problemi noti

**Problema**: Adobe Commerce visualizza un errore **checksum non corretto** durante il download da `repo.magento.com` da parte di Composer e il download del pacchetto è stato interrotto. Questo problema può verificarsi durante il download dei pacchetti di rilascio resi disponibili durante la versione prerelease ed è causato da un repackaging del pacchetto `magento/module-page-cache`.

**Soluzione**: i commercianti che visualizzano questo errore durante il download possono effettuare i seguenti passaggi:

1) Eliminare la directory `/vendor` all&#39;interno del progetto, se presente.
2) Eseguire il comando `bin/magento composer update magento/module-page-cache`. Questo comando aggiorna solo il pacchetto `page cache`.

Se il problema di checksum persiste, rimuovere il file `composer.lock` prima di eseguire nuovamente il comando `bin/magento composer update` per aggiornare ogni pacchetto.

## 2.4.4-p5

La versione di sicurezza Adobe Commerce 2.4.4-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Applica hotfix per CVE-2022-31160

La libreria `jQuery-UI` versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e Magento Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella correzione della vulnerabilità di sicurezza dell&#39;interfaccia utente [jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) dell&#39;articolo della Knowledge Base.

## 2.4.4-p4

La versione di sicurezza Adobe Commerce 2.4.4-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti della sicurezza e aggiornamenti della piattaforma per migliorare la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Applica hotfix per CVE-2022-31160

La libreria `jQuery-UI` versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e Magento Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella correzione della vulnerabilità di sicurezza dell&#39;interfaccia utente [jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) dell&#39;articolo della Knowledge Base.

### In evidenza

Il comportamento predefinito della query GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) e dell&#39;endpoint REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) è stato modificato. Per impostazione predefinita, l&#39;API ora restituisce sempre `true`. I commercianti possono abilitare il comportamento originale, che restituisce `true` se l&#39;e-mail non esiste nel database e `false` se esiste. <!-- AC-6695 -->

### Aggiornamenti della piattaforma

Gli aggiornamenti della piattaforma per questa versione migliorano la conformità alle best practice di sicurezza più recenti.

* **Supporto cache di vernice 7.3**. Questa versione è compatibile con la versione più recente di Varnish Cache 7.3. La compatibilità rimane con le versioni 6.0.x e 7u.2.x, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.4-p4 solo con Vernice Cache versione 7.3 o 6.0 LTS.

* Supporto di **RabbitMQ 3.11**. Questa versione è compatibile con l’ultima versione di RabbitMQ 3.11. La compatibilità rimane con RabbitMQ 3.9, che è supportato fino ad agosto 2023, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.4-p4 solo con RabbitMQ 3.11.

* **Librerie JavaScript**. Le librerie JavaScript obsolete sono state aggiornate alle versioni secondarie o patch più recenti, tra cui la libreria `moment.js` (v2.29.4), la libreria `jQuery UI` (v1.13.2) e la libreria del plug-in di convalida `jQuery` (v1.19.5).

## 2.4.4-p3

La versione di sicurezza Adobe Commerce 2.4.4-p3 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

La versione di sicurezza di Adobe Commerce 2.4.4-p2 fornisce correzioni per le vulnerabilità identificate nelle versioni precedenti. Una correzione include la creazione di una nuova impostazione di configurazione. L&#39;impostazione di configurazione [!UICONTROL **Richiedi conferma e-mail se l&#39;indirizzo e-mail è stato modificato**] consente agli amministratori di richiedere conferma e-mail quando un utente amministratore modifica il proprio indirizzo e-mail. <!-- AC-6292-->

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Applica AC-3022.patch per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` al più presto per continuare a offrire DHL come vettore di spedizione. Per informazioni sul download e l&#39;installazione della patch, vedere l&#39;articolo della Knowledge Base [Applica una patch per continuare a offrire DHL come corriere](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481).

## 2.4.4-p1

La versione di sicurezza Adobe Commerce 2.4.4-p1 fornisce correzioni per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, consulta [Bollettino sulla sicurezza di Adobe](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Applica `AC-3022.patch` per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` al più presto per continuare a offrire DHL come vettore di spedizione. Per informazioni sul download e l&#39;installazione della patch, vedere l&#39;articolo della Knowledge Base [Applica una patch per continuare a offrire DHL come corriere](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### In evidenza

Miglioramenti di sicurezza per questa versione migliorano la conformità con le best practice più recenti, tra cui:

* Le risorse ACL sono state aggiunte al magazzino.
* La sicurezza del modello di inventario è stata migliorata.

### Problemi noti

**Problema**: l&#39;API Web e i test di integrazione visualizzano questo errore quando vengono eseguiti sul pacchetto 2.4.4-p1: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Soluzione**: installare la versione precedente di Monolog eseguendo il comando `require monolog/monolog:2.6.0`. <!-- AC-3651-->

**Problema**: i commercianti possono notare avvisi di downgrade della versione del pacchetto durante un aggiornamento da Adobe Commerce 2.4.4 a Adobe Commerce 2.4.4-p1. Questi messaggi possono essere ignorati. La discrepanza nelle versioni dei pacchetti deriva da anomalie durante la generazione dei pacchetti. Nessuna funzionalità del prodotto interessata. Per informazioni sugli scenari interessati e sulle soluzioni alternative, vedere l&#39;articolo della Knowledge Base [Pacchetti sottoposti a downgrade dopo l&#39;aggiornamento da 2.4.4 a 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949).

<!-- Last updated from includes: 2025-07-24 10:48:00 -->
