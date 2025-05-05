---
title: '[!DNL Dashboard]'
description: Scopri la scheda  [!DNL Dashboard]  in  [!DNL Site-Wide Analysis Tool], gli elementi, quando utilizzare, i vantaggi e le best practice.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Nella pagina [!UICONTROL Dashboard] viene visualizzato [!DNL widgets] che fornisce un &quot;singolo riquadro di visualizzazione&quot; dello stato corrente e dell&#39;integrità del sito Web Adobe Commerce. Ogni [!DNL widget] contiene un collegamento di accesso alla pagina di ogni funzionalità, a ogni strumento stesso o ai report (a seconda di [!DNL widget]).
È inoltre disponibile un elenco di [!UICONTROL External Resources] collegamenti per Adobe Commerce, tra cui [Knowledge Base di supporto per Adobe Commerce Help Center (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=it), [Documentazione per gli sviluppatori Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it){target="_blank"}, [Centro sicurezza](https://helpx.adobe.com/it/security.html) e [Osservazione per Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=it).

## Elementi

* **[!UICONTROL Recommendations]**: visualizza i consigli sulle best practice per il sito. I Recommendations (problemi rilevati e raccomandazioni da correggere) sono ordinati in base alla priorità, da P0 (Critico) a P4 (Notifica).
Recommendations include descrizione, consigli, impatto sul sito, causa principale, scenari/condizioni preliminari e strumenti utilizzati.

* **[!UICONTROL Upgrade Compatibility Tool]**: consente di controllare un&#39;istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice di base installati. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima dell’aggiornamento alla versione più recente di Adobe Commerce. Inoltre, identifica potenziali problemi che devono essere risolti nel codice prima di tentare l’aggiornamento a una versione più recente di Adobe Commerce.
[!UICONTROL Upgrade Compatibility Tool] ti consente di identificare quando sono state apportate modifiche al codice di base alle funzioni personalizzate.

* **[!UICONTROL Security Center Widget]**: visualizza informazioni sulla sicurezza per il sito.
Le informazioni di protezione visualizzate includono [Tech [!DNL Stack] Conformità versione con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=it), [Adobe Security Bulletin](https://helpx.adobe.com/it/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=it), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=it).<br>
[[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=it) esegue il monitoraggio dei siti di Adobe Commerce per individuare eventuali rischi per la sicurezza. È in grado di rilevare in modo proattivo ed efficiente il malware nei negozi commerciali e avvisare i commercianti in caso di rischi per la sicurezza, malware o minacce, nonché di identificare patch e aggiornamenti mancanti di Adobe Commerce.

* **[!UICONTROL Extensions]**: visualizza le estensioni attualmente installate nell&#39;istanza Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) fornisce informazioni, se disponibili, per le estensioni elencate.

* **[!UICONTROL Alerts]**: visualizza l&#39;ultimo [!DNL New Relic Managed Alerts] per l&#39;istanza di Adobe Commerce. Ulteriori informazioni sugli [avvisi gestiti per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html?lang=it) e su come [accedere ai servizi New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=it) nella Knowledge Base del supporto Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: visualizza il software non consigliato attualmente in uso nell&#39;istanza di Adobe Commerce, in base alla versione di Adobe Commerce. Software non consigliato elencato da [!UICONTROL Name], [!UICONTROL Installed Version] e [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: visualizza un breve elenco delle patch consigliate in base alle patch eventualmente già installate e alla versione di Adobe Commerce in uso. L&#39;elenco completo delle patch consigliate si trova nella scheda delle funzionalità **[!UICONTROL Patches]**, anch&#39;essa all&#39;interno di [!DNL Site-Wide Analysis Tool]. Le patch sono fornite da [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it){target="_blank"}. Tutte le patch elencate sono compatibili con l’istanza Adobe Commerce corrente.
Se non sono presenti patch consigliate da visualizzare per l&#39;istanza Adobe Commerce, [!DNL widget] verrà visualizzato, **[!UICONTROL No Recommended Patches]**.

## Quando utilizzare

La pagina **[!UICONTROL Dashboard]** è il centro di comando immediato di [!DNL Site-Wide Analysis Tool] che consente non solo di visualizzare con facilità il &quot;quadro generale&quot; dello stato di salute del sito nel suo complesso, ma anche di visualizzare e accedere a strumenti, consigli e report specifici per il sito Web Adobe Commerce tramite ogni [!DNL widget].

## Vantaggi

* I [!DNL widgets] per [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] e [!UICONTROL Security Scan] utilizzano tutti grafici circolari interattivi codificati con colori di facile lettura con legende del grafico laterali e contano i totali al centro per indicare quanti [!UICONTROL Recommendations], [!UICONTROL Extensions] e [!UICONTROL Security Scan Tool] elementi ogni funzione ha. [!UICONTROL Recommendations] e [!UICONTROL Security Scan Tool] grafici sono separati per gravità. [!UICONTROL Extensions] sono separati in quattro classificazioni: versione corrente, versione precedente, disabilitata e sconosciuta.

* [!DNL New Relic Alerts] sono elencati con l&#39;avviso più recente in alto, inclusa una breve descrizione e quanto tempo fa si è verificato l&#39;avviso.

* [!UICONTROL Recommendations] e [!UICONTROL Extensions] [!DNL widgets] hanno accesso alla pagina completa dei dati per ogni funzionalità facendo clic su **[!UICONTROL View All]**.

* [!UICONTROL Security Scan Tool] ha un collegamento **[!UICONTROL View Report]** nella finestra [!DNL widget] che ti porta alla pagina [!UICONTROL Recommendations].

* [!DNL Upgrade Compatibility Tool] ha un pulsante **[!UICONTROL Run Upgrade Scan]** nella finestra [!DNL widget].

## Best practice per l&#39;utilizzo di [!UICONTROL Dashboard]

* Fai clic su ogni [!DNL widget] per accedere ai dati dettagliati forniti e ottenere informazioni approfondite e informazioni sulla sicurezza, l&#39;integrità, le raccomandazioni e le best practice del tuo sito web per migliorarlo.

* Vai a [!UICONTROL Security Scan Tool] [!DNL widget] e fai clic su [!UICONTROL View Report] per visualizzare un report [!UICONTROL Recommendations] per il tuo sito.

* Utilizza i collegamenti [!DNL External Resources] per ulteriori informazioni, essere sempre aggiornato sulle patch di sicurezza, gli aggiornamenti e le best practice, oppure approfitta delle informazioni della [Knowledge Base di supporto del Centro assistenza di Adobe Commerce (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=it), della [Documentazione per sviluppatori di Adobe Commerce (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it){target="_blank"}, del [Centro sicurezza](https://helpx.adobe.com/it/security.html) e della [Osservazione per Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=it).
