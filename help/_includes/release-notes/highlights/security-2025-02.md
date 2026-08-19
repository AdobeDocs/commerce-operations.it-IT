---
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---
# Punti salienti delle patch di sicurezza di febbraio 2025

Questa versione include i seguenti elementi di rilievo:

* **Gestione delle chiavi di crittografia e ricrittografia dei dati**—Riprogettazione della gestione delle chiavi di crittografia per migliorarne l&#39;usabilità ed eliminare limitazioni e bug precedenti.<!-- AC-12679 -->

  Sono ora disponibili nuovi comandi CLI per [modificare](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/encryption-key) chiavi e [ricrittografare](https://developer.adobe.com/commerce/php/development/security/data-encryption) determinati dati di configurazione di sistema, pagamento e campi personalizzati. La modifica delle chiavi nell’interfaccia utente di amministrazione non è più supportata in questa versione. Utilizzare i comandi CLI.

* **Correzione per [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)**—Risolve una vulnerabilità di autorizzazione.

  Questa correzione è disponibile anche come patch isolata. Per ulteriori informazioni, vedere l&#39;[articolo della Knowledge Base](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-27149).<!-- AC-12755 -->

* **Downgrade versione TinyMCE**: la dipendenza TinyMCE è stata ridotta dalla versione 7 alla versione 6.8.5 per risolvere i problemi di compatibilità delle licenze.

  Questa modifica garantisce la conformità continua durante la valutazione da parte di Adobe di un editor WYSIWYG open source alternativo.
