---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.79'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.79.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a8666ceccfe78536a624c67227692c98a521f555
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.79

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.79.

QPT v1.1.79 include le seguenti patch:
1. **ACP2E-4402**: è stato risolto il problema che impediva l&#39;aggiunta dei prodotti creati come disabilitati ai [!UICONTROL Target Rule] risultati correlati dopo l&#39;abilitazione.
1. **ACP2E-4505**: è stato risolto il problema che consentiva di salvare una categoria con dati non aggiornati da una scheda del browser duplicata, creando una dipendenza circolare.
1. **ACP2E-4531**: è stato corretto il problema per cui la modifica della chiave URL di una pagina CMS non comporta l&#39;aggiornamento dell&#39;URL gerarchico della pagina.
1. **ACP2E-4601**: è stato risolto il problema che poteva causare un funzionamento inefficiente dell&#39;elaborazione delle transazioni di pagamento in determinate condizioni.
1. **ACP2E-4603**: è stato risolto il problema che causava la mancata modifica delle righe dell&#39;indice delle autorizzazioni esistenti durante l&#39;esecuzione della reindicizzazione del prodotto [!UICONTROL Catalog Permissions], impedendo che le autorizzazioni per le categorie aggiornate si riflettessero in modo affidabile sui prodotti.
1. **ACP2E-4706**: è stato risolto il problema che causava il salto dei prodotti non abilitati nell&#39;ambito [!UICONTROL Admin] da parte dell&#39;indicizzatore [!UICONTROL Target Rule].
1. **ACP2E-4720**: è stato risolto il problema che impediva la corretta applicazione o rimozione della spedizione gratuita per i prodotti bundle con regole di sconto sul carrello.
1. **ACP2E-4411**: è stato risolto il problema che causava la visualizzazione del prezzo errato per un prodotto bundle nella pagina del carrello e nel mini-carrello per gli store a più valute.
1. **ACP2E-4475**: è stato risolto il problema che impediva alla pagina di elenco dei prodotti di filtrare e ordinare i prodotti del bundle esaurito in base al prezzo quando l&#39;opzione **[!UICONTROL Display Out of Stock Products]** è abilitata.
1. **ACP2E-4110**: è stato risolto il problema che causava la visualizzazione di importi non corretti in PDP e PLP in una valuta non predefinita da parte dei prodotti bundle con un prezzo speciale.
1. **AC-10698**: risolve il problema relativo all&#39;invio della valuta a livello di tutti gli ordini anziché associarla a singoli ordini. I prezzi e i totali delle transazioni vengono ora inviati per ordine a [!DNL Google Tag], migliorando la precisione del tracciamento dei dati di e-commerce.
1. **AC-10737**: è stato corretto un problema a causa del quale il comando `bin/magento setup:db:status` non riconosceva il tipo di dati JSON.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
