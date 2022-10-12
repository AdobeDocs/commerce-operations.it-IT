---
title: "[!DNL Dashboard]"
description: Scopri le [!DNL Dashboard] nella scheda [!DNL Site-Wide Analysis Tool], gli elementi, i tempi di utilizzo, i vantaggi e le best practice.
source-git-commit: d176b6a82fbea2f3c611be0fbea85814086feed9
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

La [!UICONTROL Dashboard] mostra a colpo d&#39;occhio [!DNL widgets] che forniscono un &quot;singolo riquadro di visualizzazione del vetro&quot; dello stato di salute e dello stato attuale del sito web Adobe Commerce. Tali [!DNL widgets] ciascuna contiene un collegamento di accesso alla pagina di ciascuna funzione, a ogni strumento stesso o ai rapporti (a seconda della [!DNL widget]).
Esiste anche un elenco di [!UICONTROL External Resources] collegamenti per Adobe Commerce, compresi i [Knowledge Base del supporto di Adobe Commerce Help Center (Centro assistenza)](https://support.magento.com/), [Documentazione per gli sviluppatori di Adobe Commerce (DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}, [Centro sicurezza PC](https://magento.com/security)e [Osservazione per Adobe Commerce (OAC)](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).

## Elementi

* **[!UICONTROL Recommendations]**: Visualizza raccomandazioni sulle best practice per il sito. Recommendations (problemi rilevati e raccomandazioni da risolvere) sono ordinati per priorità: da P0 (critico) a P4 (notifica).
Recommendations include descrizione, raccomandazione, impatto del sito, causa principale, scenari/condizioni preliminari e strumenti utilizzati.

* **[!UICONTROL Upgrade Compatibility Tool]**: Controlla un&#39;istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice core installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce. Identifica anche i potenziali problemi che devono essere risolti nel codice prima di tentare di eseguire l&#39;aggiornamento a una versione più recente di Adobe Commerce.
La [!UICONTROL Upgrade Compatibility Tool] consente di identificare quando sono state apportate modifiche al codice di base alle funzionalità personalizzate.

* **[!UICONTROL Security Scan Tool]**: Monitora i siti Adobe Commerce per rischi di sicurezza. È in grado di rilevare in modo proattivo ed efficiente il malware sui negozi di merchant e avvisare i commercianti in caso di rischi per la sicurezza, malware o minacce, e può identificare le patch e gli aggiornamenti mancanti di Adobe Commerce.

* **[!UICONTROL Extensions]**: Visualizza le estensioni attualmente installate nell&#39;istanza di Adobe Commerce. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) se disponibili, vengono fornite informazioni per le estensioni ivi elencate.

* **[!UICONTROL Alerts]**: Visualizza le ultime [!DNL New Relic Managed Alerts] per l’istanza Adobe Commerce. Ulteriori informazioni [Avvisi gestiti per Adobe Commerce](https://support.magento.com/hc/en-us/articles/360045806832) e come [Accesso a nuovi servizi relativi alle relazioni](https://support.magento.com/hc/en-us/articles/360039127712) nella Knowledge Base del supporto Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: Visualizza il software non consigliato attualmente in uso nell’istanza di Adobe Commerce, in base alla versione Adobe Commerce in uso. Il software non consigliato è elencato da [!UICONTROL Name], [!UICONTROL Installed Version]e [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Visualizza un breve elenco delle patch consigliate in base alle patch eventualmente già installate e alla versione Adobe Commerce. L’elenco completo delle patch consigliate si trova nella pagina **[!UICONTROL Patches]** scheda funzionalità, che si trova anche all’interno di [!DNL Site-Wide Analysis Tool]. Le patch sono fornite dal [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}. Tutte le patch elencate sono compatibili con l’istanza corrente di Adobe Commerce.
Se non vi sono patch consigliate da visualizzare per la tua istanza Adobe Commerce, questo [!DNL widget] visualizzerà, **[!UICONTROL No Recommended Patches]**.

## Quando utilizzare

La **[!UICONTROL Dashboard]** la pagina è il tuo centro di comando a colpo d&#39;occhio nel [!DNL Site-Wide Analysis Tool] per visualizzare non solo facilmente il &quot;quadro generale&quot; dello stato di salute del sito, ma è anche possibile visualizzare e accedere a strumenti, raccomandazioni e rapporti specifici per il sito web Adobe Commerce attraverso ogni [!DNL widget].

## Vantaggi

* La [!DNL widgets] per [!UICONTROL Recommendations], [!UICONTROL Extensions]e [!UICONTROL Security Scan] tutti utilizzano grafici circolari interattivi con codice a colori, di facile lettura, con legende a grafici laterali e conteggia totali al centro per indicare quanti [!UICONTROL Recommendations], [!UICONTROL Extensions]e [!UICONTROL Security Scan Tool] elementi di ciascuna feature. [!UICONTROL Recommendations] e [!UICONTROL Security Scan Tool] i grafici sono separati dalla gravità. [!UICONTROL Extensions] sono suddivise in quattro classificazioni: versione corrente, versione precedente, disabilitata e sconosciuta.

* [!DNL New Relic Alerts] sono elencati con l’avviso più recente in cima, inclusa una breve descrizione e da quanto tempo si è verificato l’avviso.

* La [!UICONTROL Recommendations] e [!UICONTROL Extensions] [!DNL widgets] accedere alla pagina completa dei dati per ciascuna funzionalità facendo clic su **[!UICONTROL View All]**.

* La [!UICONTROL Security Scan Tool] ha **[!UICONTROL View Report]** nel collegamento [!DNL widget] finestra che ti porta al [!UICONTROL Recommendations] pagina.

* La [!DNL Upgrade Compatibility Tool] ha **[!UICONTROL Run Upgrade Scan]** nel [!DNL widget] finestra.

## Best practice per l’utilizzo di [!UICONTROL Dashboard]

* Fai clic su ciascuno [!DNL widget] per accedere ai dati dettagliati forniti, è possibile ottenere informazioni approfondite e comprendere lo stato di salute, i consigli e le best practice del sito web al fine di migliorarlo.

* Vai a [!UICONTROL Security Scan Tool] [!DNL widget] e fai clic su [!UICONTROL View Report] per visualizzare un [!UICONTROL Recommendations] per il sito.

* Utilizza la [!DNL External Resources] collegamenti per ulteriori informazioni, mantenere aggiornato le patch di sicurezza, gli aggiornamenti e le best practice, oppure sfruttare le informazioni approfondite [Knowledge Base del supporto di Adobe Commerce Help Center (Centro assistenza)](https://support.magento.com/), [Documentazione per gli sviluppatori di Adobe Commerce (DevDocs)](https://devdocs.magento.com/), [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}, [Centro sicurezza PC](https://helpx.adobe.com/security.html)e [Osservazione per Adobe Commerce (OAC)](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).
