---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.77'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.77.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 98ccb5c357ebcb3bc2a7bb48e61b8557a65049f9
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.77

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.77.

QPT v1.1.77 include le seguenti patch:

1. **[ACSD-63687](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-63687.md)**: è stato corretto un problema a causa del quale venivano visualizzati prezzi non corretti. Impossibile pulire la cache di [!DNL Redis].
1. **[ACSD-68341](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68341.md)**: è stato corretto un problema a causa del quale il cookie `X-Magento-Vary` viene impostato più volte durante il caricamento di PDP, quando vengono creati più segmenti di clienti nell&#39;archivio.
1. **[ACSD-68537](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68537.md)**: è stato risolto un problema che comprometteva le prestazioni dell&#39;estrazione a causa dell&#39;aumento del numero di segmenti cliente.
1. **[ACSD-68664](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68664.md)**: è stato risolto un problema che causava l&#39;interruzione dell&#39;anteprima dell&#39;aggiornamento pianificato durante il tentativo di visualizzare l&#39;anteprima del contenuto per gli archivi con domini personalizzati.
1. **[ACSD-68759](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68759.md)**: è stato risolto un problema che impediva la creazione di un account cliente quando si utilizzavano le impostazioni locali arabe e l&#39;attributo Data di nascita (DOB) era impostato per la visualizzazione nella vetrina.
1. **[ACSD-68892](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-68892.md)**: è stato corretto un problema a causa del quale le pagine memorizzabili nella cache non venivano memorizzate o servite correttamente dalla cache [!DNL Fastly], causando un comportamento di caching incoerente e prestazioni ridotte.
1. **[ACSD-69016](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69016.md)**: è stato risolto un problema che impediva l&#39;applicazione del prezzo speciale per i siti Web creati con fusi orari diversi.
1. **[ACSD-69020](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69020.md)**: è stato risolto un problema che causava l&#39;inclusione automatica di un prodotto configurabile negli elenchi carosello di [!DNL Page Builder] se uno dei suoi prodotti secondari soddisfaceva le condizioni di filtro.
1. **[ACSD-69237](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69237.md)**: è stato corretto un problema a causa del quale il numero di voci che è possibile elaborare e inserire tramite i processi cron `sales_*_async_insert` è limitato a *100* per esecuzione.
1. **[ACSD-69311](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69311.md)**: è stato risolto un problema relativo al calcolo dell&#39;imposta errato nelle note di accredito durante la creazione di un rimborso parziale da una fattura, se è stata creata una nota di accredito precedente dalla pagina di visualizzazione dell&#39;ordine.
1. **[ACSD-69351](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69351.md)**: è stato corretto un problema a causa del quale i saldi gift card e le date di scadenza non vengono visualizzati in base all&#39;ambito del sito Web assegnato.
1. **[ACSD-69494](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-77/acsd-69494.md)**: è stato risolto un problema relativo alle operazioni di rimborso asincrono in cui le richieste di rimborso con il parametro `is_online` non vengono elaborate correttamente.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
