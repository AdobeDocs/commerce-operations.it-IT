---
title: Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.4
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.4

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.4-p9

La versione di sicurezza Adobe Commerce 2.4.4-p9 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.4.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aggiornamenti della piattaforma

* **Supporto di MariaDB 10.5**. Questa versione patch introduce la compatibilità con MariaDB versione 10.5. Adobe Commerce è ancora compatibile con MariaDB versione 10.4, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.4-p9 e tutte le prossime versioni delle patch di sicurezza 2.4.4 solo con MariaDB versione 10.5 perché la manutenzione di MariaDB 10.4 termina il 18 giugno 2024. <!--AC-11530-->

### Ulteriori miglioramenti della sicurezza

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## 2.4.4-p8

La versione di sicurezza Adobe Commerce 2.4.4-p8 fornisce correzioni di bug di sicurezza per la distribuzione Adobe Commerce 2.4.4. Questi aggiornamenti correggono le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

La versione di sicurezza di Adobe Commerce 2.4.4-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Elementi di rilievo sulla sicurezza

Questa versione introduce due miglioramenti significativi per la sicurezza:

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi della direttiva del modello o `setCacheKey` o `setData` metodi.)
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_). <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare il nuovo **[!UICONTROL Code Quantity Limit]** opzione di configurazione (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per controllare questo nuovo limite. <!-- AC-8753 -->

## 2.4.4-p6

La versione di sicurezza Adobe Commerce 2.4.4-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

### Evidenziazione sicurezza

Questa versione introduce una nuova impostazione di configurazione della cache di pagina intera che consente di mitigare i rischi associati all&#39;azione `{BASE-URL}/page_cache/block/esi HTTP` endpoint. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. Il nuovo **[!UICONTROL Handles Param]** L&#39;impostazione di configurazione imposta il valore dell&#39;endpoint `handles` , che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. Gli esercenti possono modificare questo valore da Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema noto

**Problema**: Adobe Commerce mostra una **checksum errato** errore durante il download per Compositore da `repo.magento.com`e il download del pacchetto viene interrotto. Questo problema può verificarsi durante il download dei pacchetti di rilascio resi disponibili durante la versione prerelease ed è causato da un repackaging dei `magento/module-page-cache` pacchetto.

**Soluzione alternativa**: i commercianti che visualizzano questo errore durante il download possono effettuare le seguenti operazioni:

1) Elimina `/vendor` all’interno del progetto, se presente.
2) Esegui il `bin/magento composer update magento/module-page-cache` comando. Questo comando aggiorna solo il `page cache` pacchetto.

Se il problema del checksum persiste, rimuovere `composer.lock` prima di eseguire di nuovo `bin/magento composer update` per aggiornare ogni pacchetto.

## 2.4.4-p5

La versione di sicurezza Adobe Commerce 2.4.4-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Applica la patch per risolvere la vulnerabilità di sicurezza CVE-2022-31160 nella libreria jQuery-UI

`jQuery-UI` la libreria versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e dei Magenti Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella [Correzione della vulnerabilità di sicurezza dell’interfaccia utente jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Articolo della Knowledge Base.

## 2.4.4-p4

La versione di sicurezza Adobe Commerce 2.4.4-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti della sicurezza e aggiornamenti della piattaforma per migliorare la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Applica la patch per risolvere la vulnerabilità di sicurezza CVE-2022-31160 nella libreria jQuery-UI

`jQuery-UI` la libreria versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e dei Magenti Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella [Correzione della vulnerabilità di sicurezza dell’interfaccia utente jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Articolo della Knowledge Base.

### Evidenziazione sicurezza

Il comportamento predefinito del [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) query GraphQL e ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)a) L&#39;endpoint REST è stato modificato. Per impostazione predefinita, l’API ora restituisce sempre `true`. I commercianti possono abilitare il comportamento originale, che consiste nel `true` se l’e-mail non esiste nel database e `false` se esiste. <!-- AC-6695 -->

### Aggiornamenti della piattaforma

Gli aggiornamenti della piattaforma per questa versione migliorano la conformità alle best practice di sicurezza più recenti.

* **Supporto per la cache di vernice 7.3**. Questa versione è compatibile con la versione più recente di Varnish Cache 7.3. La compatibilità rimane con le versioni 6.0.x e 7u.2.x, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.4-p4 solo con Vernice Cache versione 7.3 o 6.0 LTS.

* **Supporto di RabbitMQ 3.11**. Questa versione è compatibile con l’ultima versione di RabbitMQ 3.11. La compatibilità rimane con RabbitMQ 3.9, che è supportato fino ad agosto 2023, ma l’Adobe consiglia di utilizzare Adobe Commerce 2.4.4-p4 solo con RabbitMQ 3.11.

* **Librerie JavaScript**. Le librerie JavaScript obsolete sono state aggiornate alle versioni secondarie o patch più recenti, tra cui `moment.js` libreria (v2.29.4), `jQuery UI` libreria (v1.13.2) e `jQuery` libreria del plug-in di convalida (v1.19.5).

## 2.4.4-p3

La versione di sicurezza Adobe Commerce 2.4.4-p3 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

La versione di sicurezza di Adobe Commerce 2.4.4-p2 fornisce correzioni per le vulnerabilità identificate nelle versioni precedenti. Una correzione include la creazione di una nuova impostazione di configurazione. Il **Richiedi conferma e-mail se l’e-mail è stata modificata** l’impostazione di configurazione consente agli amministratori di richiedere una conferma e-mail quando un utente amministratore modifica il proprio indirizzo e-mail. <!-- AC-6292-->

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Applica AC-3022.patch per continuare a offrire DHL come vettore di spedizione

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` non appena possibile, di continuare a offrire DHL come vettore marittimo. Consulta la [Applicare una patch per continuare a offrire DHL come vettore di spedizione](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Articolo della Knowledge Base per informazioni sul download e l&#39;installazione della patch.

## 2.4.4-p1

La versione di sicurezza Adobe Commerce 2.4.4-p1 fornisce correzioni per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza degli Adobi](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Applica `AC-3022.patch` continuare a offrire DHL come vettore marittimo

DHL ha introdotto lo schema versione 6.2 e dichiarerà obsoleto lo schema versione 6.0 nel prossimo futuro. Adobe Commerce 2.4.4 e versioni precedenti che supportano l’integrazione DHL supportano solo la versione 6.0. I commercianti che distribuiscono queste versioni devono applicare `AC-3022.patch` non appena possibile, di continuare a offrire DHL come vettore marittimo. Consulta la [Applicare una patch per continuare a offrire DHL come vettore di spedizione](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Articolo della Knowledge Base per informazioni sul download e l&#39;installazione della patch.

### Elementi di rilievo sulla sicurezza

Miglioramenti di sicurezza per questa versione migliorano la conformità con le best practice più recenti, tra cui:

* Le risorse ACL sono state aggiunte al magazzino.
* La sicurezza del modello di inventario è stata migliorata.

### Problemi noti

**Problema**: i test di integrazione e API web visualizzano questo errore quando vengono eseguiti sul pacchetto 2.4.4-p1: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Soluzione alternativa**: installa la versione precedente di Monolog eseguendo il comando `require monolog/monolog:2.6.0` comando. <!-- AC-3651-->

**Problema**: i commercianti possono notare avvisi di downgrade della versione del pacchetto durante un aggiornamento da Adobe Commerce 2.4.4 a Adobe Commerce 2.4.4-p1. Questi messaggi possono essere ignorati. La discrepanza nelle versioni dei pacchetti deriva da anomalie durante la generazione dei pacchetti. Nessuna funzionalità del prodotto interessata. Consulta la [Pacchetti declassati dopo l’aggiornamento da 2.4.4 a 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) Articolo della knowledge base per una discussione sugli scenari interessati e soluzioni alternative.
