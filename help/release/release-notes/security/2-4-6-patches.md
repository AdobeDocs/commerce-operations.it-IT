---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.6
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.6

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

La versione di sicurezza Adobe Commerce 2.4.6-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Ulteriori miglioramenti della sicurezza

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.6-p5

La versione di sicurezza Adobe Commerce 2.4.6-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate su queste correzioni, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

La versione di sicurezza Adobe Commerce 2.4.6-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Elementi di rilievo sulla sicurezza

Questa versione introduce due miglioramenti significativi per la sicurezza:

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi della direttiva del modello o `setCacheKey` o `setData` metodi.)
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_).  <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare il nuovo **[!UICONTROL Code Quantity Limit]** opzione di configurazione (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per controllare questo nuovo limite. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

La versione di sicurezza Adobe Commerce 2.4.6-p3 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Elementi di rilievo sulla sicurezza

Questa versione introduce una nuova impostazione di configurazione della cache di pagina intera che consente di mitigare i rischi associati all&#39;azione `{BASE-URL}/page_cache/block/esi HTTP` endpoint. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. Il nuovo **[!UICONTROL Handles Param]** L&#39;impostazione di configurazione imposta il valore dell&#39;endpoint `handles` , che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. Gli esercenti possono modificare questo valore da Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Hotfix inclusi in questa versione

Adobe Commerce 2.4.6-p3 include la risoluzione del degrado delle prestazioni risolto dalla patch ACSD-51892. I commercianti non sono interessati dal problema risolto da questa patch, descritto nella [ACSD-51892: problema di prestazioni in cui i file di configurazione vengono caricati più volte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Articolo della Knowledge Base.

### Problema noto

**Problema**: Adobe Commerce mostra una `wrong checksum` errore durante il download per Compositore da `repo.magento.com`e il download del pacchetto viene interrotto. Questo problema può verificarsi durante il download dei pacchetti di rilascio resi disponibili durante il periodo di prerelease ed è causato da un repackaging dei `magento/module-page-cache` pacchetto.

**Soluzione alternativa**: i commercianti che visualizzano questo errore durante il download possono effettuare le seguenti operazioni:

1) Elimina `/vendor` all’interno del progetto, se presente.
2) Esegui il `bin/magento composer update magento/module-page-cache` comando. Questo comando aggiorna solo il `page cache` pacchetto.

Se il problema del checksum persiste, rimuovere `composer.lock` prima di eseguire di nuovo `bin/magento composer update` per aggiornare ogni pacchetto.

## 2.4.6-p2

La versione di sicurezza Adobe Commerce 2.4.6-p2 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione offre inoltre miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Applica la patch per risolvere la vulnerabilità di sicurezza CVE-2022-31160 nella libreria jQuery-UI

`jQuery-UI` la libreria versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e dei Magenti Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella [Correzione della vulnerabilità di sicurezza dell’interfaccia utente jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Articolo della Knowledge Base.

### Evidenziazione sicurezza

Il valore di `fastcgi_pass` nel `nginx.sample` il file è stato restituito al valore precedente (precedente alla versione 2.4.6-p1) di `fastcgi_backend`. Questo valore è stato inavvertitamente modificato in `php-fpm:9000` in Adobe Commerce 2.4.6-p1.

### Hotfix inclusi in questa versione

Adobe Commerce 2.4.6-p2 include la risoluzione del degrado delle prestazioni risolto dalla patch ACSD-51892. I commercianti non sono interessati dal problema risolto da questa patch, descritto nella [ACSD-51892: problema di prestazioni in cui i file di configurazione vengono caricati più volte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Articolo della Knowledge Base.

## Adobe Commerce 2.4.6-p1

La versione di sicurezza Adobe Commerce 2.4.6-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti della sicurezza e aggiornamenti della piattaforma per migliorare la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni di bug di sicurezza, consulta [Bollettino sulla sicurezza dell’Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Applica la patch per risolvere la vulnerabilità di sicurezza CVE-2022-31160 nella libreria jQuery-UI

`jQuery-UI` la libreria versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e dei Magenti Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella [Correzione di vulnerabilità di sicurezza dell’interfaccia utente Query CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Articolo della Knowledge Base.

#### Evidenziazione sicurezza

Il comportamento predefinito del [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) query GraphQL e ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)a) L&#39;endpoint REST è stato modificato. Per impostazione predefinita, l’API ora restituisce sempre `true`. I commercianti possono abilitare il comportamento originale, che consiste nel `true` se l’e-mail non esiste nel database e `false` se esiste. <!-- AC-6695 -->

### Aggiornamenti della piattaforma

Gli aggiornamenti della piattaforma per questa versione migliorano la conformità alle best practice di sicurezza più recenti.

* **Supporto per la cache di vernice 7.3**. Questa versione è compatibile con la versione più recente di Varnish Cache 7.3. La compatibilità rimane con le versioni 6.0.x e 7.2.x, ma l&#39;Adobe consigliato utilizzando Adobe Commerce 2.4.6-p1 solo con Vernice Cache versione 7.3 o 6.0 LTS.

* **Supporto di RabbitMQ 3.11**. Questa versione è compatibile con l’ultima versione di RabbitMQ 3.11. La compatibilità rimane con RabbitMQ 3.9, che è supportato fino ad agosto 2023, ma l’Adobe consigliato è l’utilizzo di Adobe Commerce 2.4.6-p1 solo con RabbitMQ 3.11.

* **Librerie JavaScript**. Le librerie JavaScript obsolete sono state aggiornate alle versioni secondarie o patch più recenti, tra cui `moment.js` libreria (v2.29.4), `jQuery UI` libreria (v1.13.2) e `jQuery` libreria del plug-in di convalida (v1.19.5).

### Problemi noti

* Il `nginx.sample` è stato inavvertitamente aggiornato con una modifica che modifica il valore di `fastcgi_pass` da `fastcgi_backend` a `php-fpm:9000`. Questa modifica può essere ripristinata o ignorata senza problemi. <!-- AC-8992 -->

* Le dipendenze mancanti per il pacchetto di sicurezza B2B causano il seguente errore di installazione durante l’installazione o l’aggiornamento dell’estensione B2B alla versione 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Questo problema può essere risolto aggiungendo dipendenze manuali per il pacchetto di sicurezza B2B con un [tag di stabilità](https://getcomposer.org/doc/04-schema.md#package-links). Per ulteriori informazioni, vedere [Note sulla versione B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
