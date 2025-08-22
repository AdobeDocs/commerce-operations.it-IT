---
title: Note sulla versione della patch di sicurezza di Adobe Commerce 2.4.8
description: Scopri le correzioni di bug di sicurezza, i miglioramenti della sicurezza e altri aggiornamenti relativi alla sicurezza inclusi nelle versioni delle patch di sicurezza per Adobe Commerce 2.4.7.
exl-id: 5f8866ed-9215-4b2e-9c77-b2d474f6c1f9
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Note sulla versione per le patch di sicurezza di Adobe Commerce 2.4.8

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.8-p2

La versione di sicurezza Adobe Commerce 2.4.8-p2 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.8.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2,4,8-p1

La versione di sicurezza Adobe Commerce 2.4.8-p1 fornisce correzioni di bug di sicurezza per le vulnerabilità identificate nelle versioni precedenti della versione 2.4.8.

Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB25-50](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### In evidenza

Questa versione include i seguenti elementi di rilievo:

* **Miglioramento delle prestazioni API**—Risolve il peggioramento delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la precedente patch di sicurezza.<!-- AC-14078 -->

* **Correzione accesso a CMS Blocks**—Risolve un problema che impediva agli utenti amministratori con autorizzazioni limitate (ad esempio l&#39;accesso solo merchandising) di visualizzare la pagina dell&#39;elenco [!UICONTROL CMS Blocks].

  In precedenza, questi utenti avevano riscontrato un errore a causa di parametri di configurazione mancanti dopo l&#39;installazione delle patch di sicurezza precedenti.<!-- AC-14087 -->

* **Compatibilità limite cookie**—Risolve una modifica incompatibile con le versioni precedenti che coinvolge la costante `MAX_NUM_COOKIES` nel framework. Questo aggiornamento ripristina il comportamento previsto e garantisce la compatibilità per le estensioni o personalizzazioni che interagiscono con i limiti dei cookie.<!-- AC-14475 -->

* **Operazioni asincrone**—Operazioni asincrone limitate per l&#39;override degli ordini dei clienti precedenti.<!-- AC-13917 -->

* **Correzione per CVE-2025-47110**—Risolve una vulnerabilità dei modelli e-mail.<!-- AC-14695 -->

* **Correzione per VULN-31547**—Risolve una vulnerabilità di collegamento canonico di categoria.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Le correzioni per CVE-2025-47110 e VULN-31547 sono disponibili anche come patch isolata. Per ulteriori informazioni, vedere l&#39;[articolo della Knowledge Base](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]

<!-- Last updated from includes: 2025-05-28 17:01:56 -->
