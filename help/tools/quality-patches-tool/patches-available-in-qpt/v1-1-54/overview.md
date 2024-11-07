---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4f5ce23584cdb3bc52b8375717ba96c24364423c
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.54

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.54.

QPT v1.1.54 include le seguenti patch:

1. **ACSD-60267**: risolve il problema relativo alla corretta applicazione di FPT (Fixed Product Tax) quando si aggiungono prodotti semplici con FPT direttamente al carrello, ma non riesce quando si selezionano questi prodotti tramite opzioni di prodotto configurabili.
1. **ACSD-61103**: è stato corretto il problema per cui il conteggio degli errori nella tabella `customer_entity` non viene reimpostato su zero dopo che un cliente ha effettuato correttamente l&#39;accesso tramite gli endpoint API.
1. **ACSD-61134**: è stato risolto il problema relativo alla deselezione automatica del metodo di pagamento [!DNL Braintree Vault] nel flusso di lavoro di pagamento quando un acquirente aggiorna il proprio indirizzo di fatturazione deselezionando la casella di controllo *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199**: è stato risolto il problema che impediva alla scheda Gerarchia pagine di CMS di visualizzare una struttura ad albero corretta durante la modifica di una pagina di CMS con una gerarchia esistente.
1. **ACSD-61200**: è stato risolto il problema che causava discrepanze nei dati dell&#39;ordine di vendita nei calcoli per *[!UICONTROL Total Amount]* e *[!UICONTROL Total Amount Actual]* nelle vendite e nei calcoli per *[!UICONTROL Discount Tax Compensation Amount]* e *[!UICONTROL Shipping Discount Tax Compensation Amount]*.
1. **ACSD-61522**: è stato risolto il problema che impediva l&#39;immissione di indirizzi e-mail nei campi *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* del cliente ospite e l&#39;invio di e-mail di conferma dell&#39;ordine non valide.
1. **ACSD-61756**: migliora le prestazioni di `AdvancedSalesRule` filtri.
1. **ACSD-61799**: risolve il problema che causa il calcolo errato dello sconto totale quando più regole del carrello con sconti fissi vengono applicate al preventivo.
1. **ACSD-61845**: è stato corretto l&#39;errore che si verifica quando viene inviata una richiesta con solo *testo/html* intestazione di accettazione.
1. **ACSD-62056**: è stato risolto il problema che impediva il caricamento dell&#39;immagine per un prodotto configurabile se MSI era installato.
1. **ACSD-62485**: è stato risolto il problema che causava l&#39;interruzione del funzionamento del consumer `async.operations.all` durante la creazione di un&#39;azienda.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
