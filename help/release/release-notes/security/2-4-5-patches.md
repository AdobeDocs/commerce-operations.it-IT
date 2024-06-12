---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.5
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.5

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

La versione di sicurezza di Adobe Commerce 2.4.5-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aggiornamenti della piattaforma

* **Supporto di MariaDB 10.5**. Questa versione patch introduce la compatibilità con MariaDB versione 10.5. Adobe Commerce è ancora compatibile con MariaDB versione 10.4, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.5-p8 e tutte le prossime versioni delle patch di sicurezza 2.4.5 solo con MariaDB versione 10.5 perché la manutenzione di MariaDB 10.4 termina il 18 giugno 2024. <!--AC-11530-->

### Ulteriori miglioramenti della sicurezza

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

La versione di sicurezza di Adobe Commerce 2.4.5-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

La versione di sicurezza Adobe Commerce 2.4.5-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Elementi di rilievo sulla sicurezza

Questa versione introduce due miglioramenti significativi per la sicurezza:

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi della direttiva del modello o `setCacheKey` o `setData` metodi.)
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_).  <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare il nuovo **[!UICONTROL Code Quantity Limit]** opzione di configurazione (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per controllare questo nuovo limite. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

La versione di sicurezza Adobe Commerce 2.4.5-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Evidenziazione sicurezza

Questa versione introduce una nuova impostazione di configurazione della cache di pagina intera che consente di mitigare i rischi associati all&#39;azione `{BASE-URL}/page_cache/block/esi HTTP` endpoint. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. Il nuovo **[!UICONTROL Handles Param]** L&#39;impostazione di configurazione imposta il valore dell&#39;endpoint `handles` , che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. Gli esercenti possono modificare questo valore da Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema noto

**Problema**: Adobe Commerce mostra una **checksum errato** errore durante il download per Compositore da `repo.magento.com`e il download del pacchetto viene interrotto. Questo problema può verificarsi durante il download dei pacchetti di rilascio resi disponibili durante la versione prerelease ed è causato da un repackaging dei `magento/module-page-cache` pacchetto.

**Soluzione alternativa**: i commercianti che visualizzano questo errore durante il download possono effettuare le seguenti operazioni:

1) Elimina `/vendor` all’interno del progetto, se presente.
2) Esegui il `bin/magento composer update magento/module-page-cache` comando. Questo comando aggiorna solo il `page cache` pacchetto.

Se il problema del checksum persiste, rimuovere `composer.lock` prima di eseguire di nuovo `bin/magento composer update` per aggiornare ogni pacchetto.

## Adobe Commerce 2.4.5-p4

La versione di sicurezza Adobe Commerce 2.4.5-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Applica la patch per risolvere la vulnerabilità di sicurezza CVE-2022-31160 nella libreria jQuery-UI

`jQuery-UI` la libreria versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e dei Magenti Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella [Correzione della vulnerabilità di sicurezza dell’interfaccia utente jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Articolo della Knowledge Base.

## Adobe Commerce 2.4.5-p3

La versione di sicurezza Adobe Commerce 2.4.5-p3 fornisce correzioni di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza degli Adobi](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Applica la patch per risolvere la vulnerabilità di sicurezza CVE-2022-31160 nella libreria jQuery-UI

`jQuery-UI` la libreria versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e dei Magenti Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella [Correzione di vulnerabilità di sicurezza dell’interfaccia utente Query CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Articolo della Knowledge Base.

### Evidenziazione sicurezza

Il comportamento predefinito del [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) query GraphQL e ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)a) L&#39;endpoint REST è stato modificato. Per impostazione predefinita, l’API ora restituisce sempre `true`. I commercianti possono abilitare il comportamento originale, che consiste nel `true` se l’e-mail non esiste nel database e `false` se esiste. <!-- AC-6695 -->

### Aggiornamenti della piattaforma

Gli aggiornamenti della piattaforma per questa versione migliorano la conformità alle best practice di sicurezza più recenti.

* **Supporto per la cache di vernice 7.3**. Questa versione è compatibile con la versione più recente di Varnish Cache 7.3. La compatibilità rimane con le versioni 6.0.x e 7.2.x, ma abbiamo consigliato di utilizzare Adobe Commerce 2.4.5-p3 solo con Vernice Cache versione 7.3 o 6.0 LTS.

* **Supporto di RabbitMQ 3.11**. Questa versione è compatibile con l’ultima versione di RabbitMQ 3.11. La compatibilità rimane con RabbitMQ 3.9, che è supportato fino ad agosto 2023, ma è consigliabile utilizzare Adobe Commerce 2.4.5-p3 solo con RabbitMQ 3.11.

* **Librerie JavaScript**. Le librerie JavaScript obsolete sono state aggiornate alle versioni secondarie o patch più recenti, tra cui `moment.js` libreria (v2.29.4), `jQuery UI` libreria (v1.13.2) e `jQuery` libreria del plug-in di convalida (v1.19.5).

## Note sulla versione di Adobe Commerce 2.4.5-p2

La versione di sicurezza di Adobe Commerce 2.4.5-p2 fornisce tre correzioni di sicurezza per le vulnerabilità identificate nelle versioni precedenti.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

La versione di sicurezza Adobe Commerce 2.4.5-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nella versione precedente (Adobe Commerce 2.4.5 e Magento Open Source 2.4.5).

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Una delle correzioni di bug di sicurezza includeva la creazione di una nuova impostazione di configurazione. Il **Richiedi conferma e-mail se l’e-mail è stata modificata** L’impostazione di configurazione consente agli amministratori di richiedere una conferma e-mail quando un utente amministratore modifica il proprio indirizzo e-mail. <!-- AC-6292-->
