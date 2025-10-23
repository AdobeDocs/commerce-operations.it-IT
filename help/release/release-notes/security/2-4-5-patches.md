---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.5
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 4cf6f81ce43ddcccf20db12b8735f29a151d420d
workflow-type: tm+mt
source-wordcount: '1482'
ht-degree: 0%

---


# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.5

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-p15

La versione di sicurezza di Adobe Commerce 2.4.5-p15 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-94](https://helpx.adobe.com/it/security/products/magento/apsb25-94.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}

>[!NOTE]
>
>Le patch di sicurezza per il supporto esteso per la versione 2.4.5 sono disponibili solo per i clienti Adobe Commerce. Queste patch non sono disponibili per la base di codice di Magento Open Source. Consulta [Supporto esteso](https://experienceleague.adobe.com/it/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).


## 2.4.5-p14

La versione di sicurezza di Adobe Commerce 2.4.5-p14 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-71](https://helpx.adobe.com/it/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.5-p13

La versione di sicurezza Adobe Commerce 2.4.5-p13 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-50](https://helpx.adobe.com/it/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

* **Miglioramento delle prestazioni API**—Risolve il peggioramento delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la precedente patch di sicurezza.<!-- AC-14078 -->

* **Correzione accesso a CMS Blocks**—Risolve un problema che impediva agli utenti amministratori con autorizzazioni limitate (ad esempio l&#39;accesso solo merchandising) di visualizzare la pagina dell&#39;elenco [!UICONTROL CMS Blocks].

  In precedenza, questi utenti avevano riscontrato un errore a causa di parametri di configurazione mancanti dopo l&#39;installazione delle patch di sicurezza precedenti.<!-- AC-14087 -->

* **Compatibilità limite cookie**—Risolve una modifica incompatibile con le versioni precedenti che coinvolge la costante `MAX_NUM_COOKIES` nel framework. Questo aggiornamento ripristina il comportamento previsto e garantisce la compatibilità per le estensioni o personalizzazioni che interagiscono con i limiti dei cookie.<!-- AC-14475 -->

* **Operazioni asincrone**—Operazioni asincrone limitate per l&#39;override degli ordini dei clienti precedenti.<!-- AC-13917 -->

## 2.4.5-p12

La versione di sicurezza di Adobe Commerce 2.4.5-p12 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-26](https://helpx.adobe.com/it/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.5-p11

La versione di sicurezza Adobe Commerce 2.4.5-p11 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-08](https://helpx.adobe.com/it/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-p10

La versione di sicurezza Adobe Commerce 2.4.5-p10 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-73](https://helpx.adobe.com/it/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2,4,5-p9

La versione di sicurezza Adobe Commerce 2.4.5-p9 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-61](https://helpx.adobe.com/it/security/products/magento/apsb24-61.html).

### In evidenza

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfix inclusi in questa versione

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.5-p8

La versione di sicurezza di Adobe Commerce 2.4.5-p8 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-40](https://helpx.adobe.com/it/security/products/magento/apsb24-40.html).

### Applica hotfix per CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Aggiornamenti della piattaforma

* **Supporto di MariaDB 10.5**. Questa versione patch introduce la compatibilità con MariaDB versione 10.5. Adobe Commerce è ancora compatibile con MariaDB versione 10.4, ma Adobe consiglia di utilizzare Adobe Commerce 2.4.5-p8 e tutte le prossime versioni delle patch di sicurezza 2.4.5 solo con MariaDB versione 10.5 perché la manutenzione di MariaDB 10.4 termina il 18 giugno 2024. <!--AC-11530-->

### In evidenza

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2,4,5-p7

La versione di sicurezza di Adobe Commerce 2.4.5-p7 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-18](https://helpx.adobe.com/it/security/products/magento/apsb24-18.html).

## 2,4,5-p6

La versione di sicurezza Adobe Commerce 2.4.5-p6 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-03](https://helpx.adobe.com/it/security/products/magento/apsb24-03.html).

### In evidenza

Questa versione introduce due miglioramenti significativi per la sicurezza:

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi di direttiva del modello o i metodi `setCacheKey` o `setData`.
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_). <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare la nuova opzione di configurazione **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per controllare questo nuovo limite. <!-- AC-8753 -->

## 2,4,5-p5

La versione di sicurezza Adobe Commerce 2.4.5-p5 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5. Questa versione include anche miglioramenti di sicurezza per migliorare la conformità alle più recenti best practice in materia di sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-50](https://helpx.adobe.com/it/security/products/magento/apsb23-50.html).

### In evidenza

Questa versione introduce una nuova impostazione di configurazione della cache di pagina intera che consente di attenuare i rischi associati all&#39;endpoint `{BASE-URL}/page_cache/block/esi HTTP`. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. La nuova impostazione di configurazione **[!UICONTROL Handles Param]** imposta il valore del parametro `handles` di questo endpoint, che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. I commercianti possono modificare questo valore dall&#39;amministratore (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problemi noti

**Problema**: Adobe Commerce visualizza un errore **checksum non corretto** durante il download da `repo.magento.com` da parte di Composer e il download del pacchetto è stato interrotto. Questo problema può verificarsi durante il download dei pacchetti di rilascio resi disponibili durante la versione prerelease ed è causato da un repackaging del pacchetto `magento/module-page-cache`.

**Soluzione**: i commercianti che visualizzano questo errore durante il download possono effettuare i seguenti passaggi:

1) Eliminare la directory `/vendor` all&#39;interno del progetto, se presente.
2) Eseguire il comando `bin/magento composer update magento/module-page-cache`. Questo comando aggiorna solo il pacchetto `page cache`.

Se il problema di checksum persiste, rimuovere il file `composer.lock` prima di eseguire nuovamente il comando `bin/magento composer update` per aggiornare ogni pacchetto.

## 2,4,5-p4

La versione di sicurezza Adobe Commerce 2.4.5-p4 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-42](https://helpx.adobe.com/it/security/products/magento/apsb23-42.html).

### Applica hotfix per CVE-2022-31160

La libreria `jQuery-UI` versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e Magento Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella correzione della vulnerabilità di sicurezza dell&#39;interfaccia utente [jQuery CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) dell&#39;articolo della Knowledge Base.

## 2.4.5-p3

La versione di sicurezza di Adobe Commerce 2.4.5-p3 fornisce correzioni di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5. Questa versione include anche miglioramenti di sicurezza che migliorano la conformità alle più recenti best practice per la sicurezza.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, consulta [Bollettino sulla sicurezza di Adobe](https://helpx.adobe.com/it/security/products/magento/apsb23-35.html).

### Applica hotfix per CVE-2022-31160

La libreria `jQuery-UI` versione 1.13.1 presenta una vulnerabilità di sicurezza nota (CVE-2022-31160) che interessa più versioni di Adobe Commerce e Magento Open Source. Questa libreria è una dipendenza di Adobe Commerce e Magento Open Source 2.4.4, 2.4.5 e 2.4.6. I commercianti che eseguono distribuzioni interessate devono applicare la patch specificata nella correzione della vulnerabilità di sicurezza dell&#39;interfaccia utente di query CVE-2022-31160 per le versioni 2.4.4, 2.4.5 e 2.4.6[&#x200B; dell&#39;articolo della Knowledge Base.](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6)

### In evidenza

Il comportamento predefinito della query GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) e dell&#39;endpoint REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) è stato modificato. Per impostazione predefinita, l&#39;API ora restituisce sempre `true`. I commercianti possono abilitare il comportamento originale, che restituisce `true` se l&#39;e-mail non esiste nel database e `false` se esiste. <!-- AC-6695 -->

### Aggiornamenti della piattaforma

Gli aggiornamenti della piattaforma per questa versione migliorano la conformità alle best practice di sicurezza più recenti.

* **Supporto cache di vernice 7.3**. Questa versione è compatibile con la versione più recente di Varnish Cache 7.3. La compatibilità rimane con le versioni 6.0.x e 7.2.x, ma abbiamo consigliato di utilizzare Adobe Commerce 2.4.5-p3 solo con Vernice Cache versione 7.3 o 6.0 LTS.

* Supporto di **RabbitMQ 3.11**. Questa versione è compatibile con l’ultima versione di RabbitMQ 3.11. La compatibilità rimane con RabbitMQ 3.9, supportato fino ad agosto 2023, ma abbiamo consigliato di utilizzare Adobe Commerce 2.4.5-p3 solo con RabbitMQ 3.11.

* **Librerie JavaScript**. Le librerie JavaScript obsolete sono state aggiornate alle versioni secondarie o patch più recenti, tra cui la libreria `moment.js` (v2.29.4), la libreria `jQuery UI` (v1.13.2) e la libreria del plug-in di convalida `jQuery` (v1.19.5).

## 2.4.5-p2

La versione di sicurezza di Adobe Commerce 2.4.5-p2 fornisce tre correzioni di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB23-17](https://helpx.adobe.com/it/security/products/magento/apsb23-17.html).

## 2,4,5-p1

La versione di sicurezza Adobe Commerce 2.4.5-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.5.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB22-48](https://helpx.adobe.com/it/security/products/magento/apsb22-48.html).

Una delle correzioni di bug di sicurezza includeva la creazione di una nuova impostazione di configurazione. L&#39;impostazione di configurazione [!UICONTROL **Richiedi conferma e-mail se l&#39;indirizzo e-mail è stato modificato**] consente agli amministratori di richiedere conferma e-mail quando un utente amministratore modifica il proprio indirizzo e-mail. <!-- AC-6292-->

<!-- Last updated from includes: 2025-10-22 11:16:25 -->
