---
title: '[!DNL Dashboard]'
description: Scopri di più su [!DNL Dashboard] scheda in [!DNL Site-Wide Analysis Tool], elementi, quando utilizzare, vantaggi e best practice.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Il [!UICONTROL Dashboard] La pagina mostra immediatamente [!DNL widgets] che forniscono un &quot;singolo pannello di visualizzazione in vetro&quot; dello stato di salute e dello stato corrente del sito web Adobe Commerce. Ogni [!DNL widget] contiene un collegamento di accesso alla pagina di ogni funzione, a ogni strumento stesso o ai rapporti (a seconda [!DNL widget]).
È inoltre disponibile un elenco di [!UICONTROL External Resources] collegamenti per Adobe Commerce, incluso [Knowledge Base di supporto del Centro assistenza Adobe Commerce (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentazione per gli sviluppatori di Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro sicurezza](https://helpx.adobe.com/security.html), e [Osservatorio per Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementi

* **[!UICONTROL Recommendations]**: visualizza i consigli sulle best practice per il sito. I Recommendations (problemi rilevati e raccomandazioni da correggere) sono ordinati in base alla priorità, da P0 (Critico) a P4 (Notifica).
Recommendations include descrizione, consigli, impatto sul sito, causa principale, scenari/condizioni preliminari e strumenti utilizzati.

* **[!UICONTROL Upgrade Compatibility Tool]**: confronta un’istanza personalizzata di Adobe Commerce con una versione specifica analizzando tutti i moduli e il codice core installati in essa. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima dell’aggiornamento alla versione più recente di Adobe Commerce. Inoltre, identifica potenziali problemi che devono essere risolti nel codice prima di tentare l’aggiornamento a una versione più recente di Adobe Commerce.
Il [!UICONTROL Upgrade Compatibility Tool] consente di identificare quando sono state apportate modifiche al codice principale alle funzioni personalizzate.

* **[!UICONTROL Security Center Widget]**: visualizza informazioni sulla sicurezza del sito.
Le informazioni di protezione visualizzate includono [Tecnico [!DNL Stack] Conformità della versione con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Best Practice Per La Sicurezza Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
Il [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) monitora i siti Adobe Commerce per individuare eventuali rischi per la sicurezza. È in grado di rilevare in modo proattivo ed efficiente il malware nei negozi commerciali e avvisare i commercianti in caso di rischi per la sicurezza, malware o minacce, nonché di identificare patch e aggiornamenti mancanti di Adobe Commerce.

* **[!UICONTROL Extensions]**: visualizza le estensioni attualmente installate nell’istanza Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) vengono fornite informazioni, se disponibili, per le estensioni elencate.

* **[!UICONTROL Alerts]**: visualizza la versione più recente [!DNL New Relic Managed Alerts] per l’istanza di Adobe Commerce. Ulteriori informazioni su [Avvisi gestiti per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) e come [Accedere ai servizi New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) nella Knowledge Base di supporto di Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: visualizza il software non consigliato attualmente in uso dall’istanza di Adobe Commerce, in base alla versione di Adobe Commerce. Il software non consigliato è elencato da [!UICONTROL Name], [!UICONTROL Installed Version], e [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: visualizza un breve elenco di eventuali patch consigliate basate su entrambe le patch che potrebbero essere già state installate e sulla versione Adobe Commerce in uso. L&#39;elenco completo delle patch consigliate si trova sul **[!UICONTROL Patches]** della funzionalità, che si trova anche all&#39;interno del [!DNL Site-Wide Analysis Tool]. Le patch vengono fornite da [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Tutte le patch elencate sono compatibili con l’istanza Adobe Commerce corrente.
Se non sono presenti patch consigliate da visualizzare per l’istanza Adobe Commerce, [!DNL widget] verrà visualizzato, **[!UICONTROL No Recommended Patches]**.

## Quando utilizzare

Il **[!UICONTROL Dashboard]** è il centro di comando immediato in [!DNL Site-Wide Analysis Tool] non solo puoi visualizzare facilmente il &quot;quadro generale&quot; dello stato di salute del tuo sito, ma puoi anche visualizzare e accedere a strumenti specifici, consigli e rapporti per il tuo sito web Adobe Commerce tramite ciascuno di essi [!DNL widget].

## Vantaggi

* Il [!DNL widgets] per [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], e [!UICONTROL Security Scan] tutti utilizzano grafici circolari interattivi codificati con colori facili da leggere con legende di grafico laterali e contano i totali al centro per indicare quanti [!UICONTROL Recommendations], [!UICONTROL Extensions], e [!UICONTROL Security Scan Tool] elementi di ogni funzione. [!UICONTROL Recommendations] e [!UICONTROL Security Scan Tool] i grafici sono separati per gravità. [!UICONTROL Extensions] sono suddivise in quattro classificazioni: versione corrente, versione precedente, disabilitata e sconosciuta.

* [!DNL New Relic Alerts] sono elencate con l’avviso più recente, inclusa una breve descrizione e da quanto tempo si è verificato l’avviso.

* Il [!UICONTROL Recommendations] e [!UICONTROL Extensions] [!DNL widgets] accedere alla pagina completa dei dati di ciascuna funzione facendo clic su **[!UICONTROL View All]**.

* Il [!UICONTROL Security Scan Tool] ha un **[!UICONTROL View Report]** collegamento in [!DNL widget] finestra che consente di visualizzare [!UICONTROL Recommendations] pagina.

* Il [!DNL Upgrade Compatibility Tool] ha un **[!UICONTROL Run Upgrade Scan]** pulsante in [!DNL widget] finestra.

## Best practice per l’utilizzo di [!UICONTROL Dashboard]

* Fai clic su ciascuno [!DNL widget] per accedere ai dati dettagliati che fornisce, è possibile ottenere informazioni approfondite e comprendere la sicurezza, lo stato di salute, le raccomandazioni e le best practice del sito web per migliorarlo.

* Vai a [!UICONTROL Security Scan Tool] [!DNL widget] e fai clic su [!UICONTROL View Report] per visualizzare un [!UICONTROL Recommendations] report per il sito.

* Utilizza il [!DNL External Resources] collegamenti per ulteriori informazioni, aggiornamenti e best practice per l&#39;aggiornamento delle patch di sicurezza o per sfruttare le informazioni [Knowledge Base di supporto del Centro assistenza Adobe Commerce (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Documentazione per gli sviluppatori di Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Centro sicurezza](https://helpx.adobe.com/security.html), e [Osservatorio per Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
