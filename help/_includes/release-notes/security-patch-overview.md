---
source-git-commit: 52c330f62d722a4cae7f7f360ca61eca0f04b961
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---
# Informazioni sulle versioni delle patch di sicurezza di Adobe Commerce

**Correzione bug di sicurezza**: modifica del codice software che risolve un problema di sicurezza identificato e fornisce i risultati previsti in un&#39;area di prodotto interessata. Queste correzioni sono generalmente compatibili con le versioni precedenti.

**Miglioramento della sicurezza**: miglioramento del software o modifica della configurazione per migliorare la sicurezza in modo proattivo all&#39;interno dell&#39;applicazione. Questi miglioramenti di sicurezza aiutano a risolvere i rischi di sicurezza che influiscono sulla postura di sicurezza dell’applicazione Adobe Commerce, ma che possono essere incompatibili con le versioni precedenti.

Con le versioni delle patch di sicurezza, è possibile proteggere il sito in modo più efficiente senza applicare ulteriori correzioni di qualità e miglioramenti contenuti in una versione completa delle patch. Alle versioni delle patch di sicurezza viene aggiunto &#39;-pN&#39;, dove N è la versione della patch incrementale che inizia con 1 (ad esempio, 2.3.5-p1). Le versioni delle patch di sicurezza possono includere anche gli hotfix necessari per risolvere i problemi critici che interessano l’applicazione Adobe Commerce.

Le versioni delle patch di sicurezza possono includere anche le modifiche relative alla conformità necessarie per garantire che l’applicazione Adobe Commerce soddisfi i requisiti di conformità. Queste modifiche possono introdurre modifiche non compatibili con le versioni precedenti e sono necessarie per garantire che tutte le linee di rilascio supportate rimangano conformi.

Ogni versione di patch di sicurezza si basa sulla versione completa precedente della patch. Contiene le correzioni di qualità e sicurezza della versione patch precedente e le correzioni di sicurezza create tra la versione patch completa precedente e la versione patch di sicurezza.

Per istruzioni su come scaricare e applicare le patch di sicurezza, vedere [Come ottenere e applicare le patch di sicurezza](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches) nella _Adobe Commerce Knowledgebase_.

>[!NOTE]
>
>Le patch di sicurezza per il supporto esteso sono disponibili solo per i clienti Adobe Commerce e non per la base di codice Magento Open Source. Consulta [Supporto esteso](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy#extended-support).

## File patch di sicurezza isolato

I file di patch di sicurezza isolati sono file di patch indipendenti e non cumulativi che includono correzioni per una o più vulnerabilità di sicurezza, senza ulteriori aggiornamenti delle funzioni o modifiche non di sicurezza. Queste patch vengono rilasciate in modo indipendente per consentire una correzione più rapida e vengono incorporate nella successiva patch di sicurezza completa. I dettagli sulle vulnerabilità sono forniti nel bollettino sulla sicurezza associato, che si collega a un articolo della Knowledge Base (KB) con istruzioni per l’applicazione della patch e informazioni aggiuntive.

Per applicare un file di patch di sicurezza isolato, i clienti devono utilizzare l&#39;ultima versione di patch di sicurezza (l&#39;ultima versione -p) per la propria riga di rilascio supportata, in quanto i file di patch di sicurezza isolati vengono testati esclusivamente in base a tale versione.

Per trovare gli ultimi aggiornamenti per la sicurezza disponibili per Adobe Commerce, visita il [Centro sicurezza PC](https://helpx.adobe.com/security/products/magento.html).

