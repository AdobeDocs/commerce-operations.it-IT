---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.6
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: e625670e741c0669050ab758d4f87c5ca06fe3df
workflow-type: tm+mt
source-wordcount: '1598'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.6

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p13

La versione di sicurezza Adobe Commerce 2.4.6-p13 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-94](https://helpx.adobe.com/it/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

{{oct-2025-backports}}

### Problemi noti

#### Pacchetto del programma di installazione del Compositore inventario mancante

Questa versione non include il pacchetto `magento/inventory-composer-installer`, necessario per un aggiornamento senza problemi da versioni precedenti non compatibili con le versioni precedenti.

Se si esegue l&#39;aggiornamento da 2.3 a 2.4.6-p13, eseguire il comando seguente per installare il pacchetto `magento/inventory-composer-installer` prima dell&#39;aggiornamento:

```bash
composer require magento/inventory-composer-installer
```

#### Impossibile caricare static.min.js e mixins.min.js nella pagina di estrazione

{{checkout-page-fails-to-load-static-min-js-and-mixins-min-js}}

## 2.4.6-p12

La versione di sicurezza di Adobe Commerce 2.4.6-p12 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-71](https://helpx.adobe.com/it/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.6-p11

La versione di sicurezza Adobe Commerce 2.4.6-p11 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-50](https://helpx.adobe.com/it/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

* **Supporto MariaDB** - Aggiunto supporto per MariaDB 10.11.

* **Miglioramento delle prestazioni API**—Risolve il peggioramento delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la precedente patch di sicurezza.<!-- AC-14078 -->

* **Correzione accesso a CMS Blocks**—Risolve un problema che impediva agli utenti amministratori con autorizzazioni limitate (ad esempio l&#39;accesso solo merchandising) di visualizzare la pagina dell&#39;elenco [!UICONTROL CMS Blocks].

  In precedenza, questi utenti avevano riscontrato un errore a causa di parametri di configurazione mancanti dopo l&#39;installazione delle patch di sicurezza precedenti.<!-- AC-14087 -->

* **Compatibilità limite cookie**—Risolve una modifica incompatibile con le versioni precedenti che coinvolge la costante `MAX_NUM_COOKIES` nel framework. Questo aggiornamento ripristina il comportamento previsto e garantisce la compatibilità per le estensioni o personalizzazioni che interagiscono con i limiti dei cookie.<!-- AC-14475 -->

* **Operazioni asincrone**—Operazioni asincrone limitate per l&#39;override degli ordini dei clienti precedenti.<!-- AC-13917 -->

## 2.4.6-p10

La versione di sicurezza Adobe Commerce 2.4.6-p10 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-26](https://helpx.adobe.com/it/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

La versione di sicurezza Adobe Commerce 2.4.6-p9 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-08](https://helpx.adobe.com/it/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

La versione di sicurezza di Adobe Commerce 2.4.6-p8 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-73](https://helpx.adobe.com/it/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2,4,6-p7

La versione di sicurezza di Adobe Commerce 2.4.6-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-61](https://helpx.adobe.com/it/security/products/magento/apsb24-61.html).

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2,4,6-p6

La versione di sicurezza Adobe Commerce 2.4.6-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-40](https://helpx.adobe.com/it/security/products/magento/apsb24-40.html).

Per la compatibilità con Commerce versione 2.4.6-p6, i commercianti con estensione Adobe Commerce B2B devono eseguire l&#39;aggiornamento alla versione [B2B versione 1.4.2-p1](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Applica hotfix per CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Per la compatibilità con Commerce versione 2.4.6-p6, i commercianti con estensione Adobe Commerce B2B devono eseguire l&#39;aggiornamento alla versione [B2B versione 1.4.2-p1](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### In evidenza

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2,4,6-p5

La versione di sicurezza Adobe Commerce 2.4.6-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.6.

Per informazioni aggiornate su queste correzioni, vedere [Adobe Security Bulletin APSB24-18](https://helpx.adobe.com/it/security/products/magento/apsb24-18.html).

## 2,4,6-p4

La versione di sicurezza Adobe Commerce 2.4.6-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-03](https://helpx.adobe.com/it/security/products/magento/apsb24-03.html).

### In evidenza

Questa versione introduce due miglioramenti significativi per la sicurezza:

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi di direttiva del modello o i metodi `setCacheKey` o `setData`.
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_). <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare la nuova opzione di configurazione **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per controllare questo nuovo limite. <!-- AC-8753 -->

## 2.4.6-p3

La versione di sicurezza Adobe Commerce 2.4.6-p3 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni di sicurezza, vedere [Adobe Security Bulletin APSB23-50](https://helpx.adobe.com/it/security/products/magento/apsb23-50.html).

### In evidenza

Questa versione introduce una nuova impostazione di configurazione della cache di pagina intera che consente di attenuare i rischi associati all&#39;endpoint `{BASE-URL}/page_cache/block/esi HTTP`. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. La nuova impostazione di configurazione **[!UICONTROL Handles Param]** imposta il valore del parametro `handles` di questo endpoint, che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. I commercianti possono modificare questo valore dall&#39;amministratore (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Hotfix inclusi in questa versione

Adobe Commerce 2.4.6-p3 include la risoluzione del degrado delle prestazioni risolto dalla patch ACSD-51892. I commercianti non sono interessati dal problema risolto da questa patch, descritto nell&#39;articolo [ACSD-51892: Problema di prestazioni in cui i file di configurazione vengono caricati più volte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=it) della Knowledge Base.

### Problemi noti

**Problema**: Adobe Commerce visualizza un errore `wrong checksum` durante il download da parte del Compositore da `repo.magento.com` e il download del pacchetto è stato interrotto. Questo problema può verificarsi durante il download dei pacchetti di rilascio resi disponibili durante il periodo di prerelease ed è causato da un repackaging del pacchetto `magento/module-page-cache`.

**Soluzione**: i commercianti che visualizzano questo errore durante il download possono effettuare i seguenti passaggi:

1) Eliminare la directory `/vendor` all&#39;interno del progetto, se presente.
2) Eseguire il comando `bin/magento composer update magento/module-page-cache`. Questo comando aggiorna solo il pacchetto `page cache`.

Se il problema di checksum persiste, rimuovere il file `composer.lock` prima di eseguire nuovamente il comando `bin/magento composer update` per aggiornare ogni pacchetto.

## 2.4.6-p2

La versione di sicurezza Adobe Commerce 2.4.6-p2 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione offre inoltre miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-42](https://helpx.adobe.com/it/security/products/magento/apsb23-42.html).

### Applica hotfix per CVE-2022-31160

La libreria `jQuery-UI` versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e Magento Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella correzione della vulnerabilità di sicurezza dell&#39;interfaccia utente [jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=it) dell&#39;articolo della Knowledge Base.

### In evidenza

Il valore di `fastcgi_pass` nel file `nginx.sample` è stato restituito al precedente valore di `fastcgi_backend` (precedente alla 2.4.6-p1). Questo valore è stato inavvertitamente modificato in `php-fpm:9000` in Adobe Commerce 2.4.6-p1.

### Hotfix inclusi in questa versione

Adobe Commerce 2.4.6-p2 include la risoluzione del degrado delle prestazioni risolto dalla patch ACSD-51892. I commercianti non sono interessati dal problema risolto da questa patch, descritto nell&#39;articolo [ACSD-51892: Problema di prestazioni in cui i file di configurazione vengono caricati più volte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=it) della Knowledge Base.

## 2.4.6-p1

La versione di sicurezza Adobe Commerce 2.4.6-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti. Questa versione include anche miglioramenti della sicurezza e aggiornamenti della piattaforma per migliorare la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-35](https://helpx.adobe.com/it/security/products/magento/apsb23-35.html).

### Applica hotfix per CVE-2022-31160

La libreria `jQuery-UI` versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e Magento Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella correzione della vulnerabilità di sicurezza dell&#39;interfaccia utente di query CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6[&#x200B; dell&#39;articolo della Knowledge Base.](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=it)

#### Evidenzia

Il comportamento predefinito della query GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) e dell&#39;endpoint REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) è stato modificato. Per impostazione predefinita, l&#39;API ora restituisce sempre `true`. I commercianti possono abilitare il comportamento originale, che restituisce `true` se l&#39;e-mail non esiste nel database e `false` se esiste. <!-- AC-6695 -->

### Aggiornamenti della piattaforma

Gli aggiornamenti della piattaforma per questa versione migliorano la conformità alle best practice di sicurezza più recenti.

* **Supporto cache di vernice 7.3**. Questa versione è compatibile con la versione più recente di Varnish Cache 7.3. La compatibilità rimane con le versioni 6.0.x e 7.2.x, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.6-p1 solo con Vernice Cache versione 7.3 o 6.0 LTS.

* Supporto di **RabbitMQ 3.11**. Questa versione è compatibile con l’ultima versione di RabbitMQ 3.11. La compatibilità rimane con RabbitMQ 3.9, che è supportato fino ad agosto 2023, ma Adobe ha consigliato di utilizzare Adobe Commerce 2.4.6-p1 solo con RabbitMQ 3.11.

* **Librerie JavaScript**. Le librerie JavaScript obsolete sono state aggiornate alle versioni secondarie o patch più recenti, tra cui la libreria `moment.js` (v2.29.4), la libreria `jQuery UI` (v1.13.2) e la libreria del plug-in di convalida `jQuery` (v1.19.5).

### Problemi noti

* Il file `nginx.sample` è stato inavvertitamente aggiornato con una modifica che modifica il valore di `fastcgi_pass` da `fastcgi_backend` a `php-fpm:9000`. Questa modifica può essere ripristinata o ignorata senza problemi. <!-- AC-8992 -->

* Le dipendenze mancanti per il pacchetto di sicurezza B2B causano il seguente errore di installazione durante l’installazione o l’aggiornamento dell’estensione B2B alla versione 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Questo problema può essere risolto aggiungendo dipendenze manuali per il pacchetto di sicurezza B2B con un [tag di stabilità](https://getcomposer.org/doc/04-schema.md#package-links). Per informazioni dettagliate, consulta le [note sulla versione B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=it#known-issue).

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
