---
source-git-commit: cbf41054a2a8ffefa38049e1bf6e4a2f09e06ce1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Punti salienti delle patch di sicurezza di giugno 2025

Questa versione include i seguenti elementi di rilievo:

* **Miglioramento delle prestazioni API**—Risolve il peggioramento delle prestazioni negli endpoint API Web asincroni in blocco introdotti dopo la precedente patch di sicurezza.<!-- AC-14078 -->

* **Correzione accesso a CMS Blocks**—Risolve un problema che impediva agli utenti amministratori con autorizzazioni limitate (ad esempio l&#39;accesso solo merchandising) di visualizzare la pagina dell&#39;elenco [!UICONTROL CMS Blocks].

  In precedenza, questi utenti avevano riscontrato un errore a causa di parametri di configurazione mancanti dopo l&#39;installazione delle patch di sicurezza precedenti.<!-- AC-14087 -->

* **Compatibilità limite cookie**—Risolve una modifica incompatibile con le versioni precedenti che coinvolge la costante `MAX_NUM_COOKIES` nel framework. Questo aggiornamento ripristina il comportamento previsto e garantisce la compatibilità per le estensioni o personalizzazioni che interagiscono con i limiti dei cookie.<!-- AC-14475 -->

* **Correzione per CVE-2024-34104**—Risolve una vulnerabilità di autorizzazione non corretta.<!-- AC-13917 -->

* **Correzione per CVE-2025-47110**—Risolve una vulnerabilità dei modelli e-mail.<!-- AC-14695 -->

>[!BEGINSHADEBOX]

La correzione per CVE-2025-47110 è disponibile anche come patch isolata. Per ulteriori informazioni, vedere l&#39;[articolo della Knowledge Base](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50).

>[!ENDSHADEBOX]
