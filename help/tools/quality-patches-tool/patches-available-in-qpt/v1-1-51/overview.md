---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.51'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.51.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 670b0546f089bdbf572d06765af6a92f8ff5f233
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.51

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.51.

QPT v1.1.51 include le seguenti patch:

1. **ACSD-59786**: è stato risolto il problema che causava la restituzione da parte di GraphQL di un errore interno del server durante il tentativo di ottenere un ID preventivo per un preventivo scaduto.
1. **ACSD-60234**: è stato risolto il problema che causava la visualizzazione di un importo errato in [!DNL PayPal] quando lo sconto veniva applicato tramite il metodo di pagamento.
1. JavaScript **ACSD-59967**: è stato risolto il problema che impediva a [!DNL Google Maps] di eseguire correttamente il rendering.
1. **ACSD-60326**: è stato corretto il problema che si verificava durante la query GraphQL per lo stato di restituzione del cliente.
1. **ACSD-60538**: è stato risolto il problema per cui se un prodotto è disabilitato in *[!UICONTROL All Store Views]* e abilitato solo in ambiti di visualizzazione specifici dell&#39;archivio, gli attributi del prodotto non vengono visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto.
1. **ACSD-60631**: è stato corretto il problema per cui GraphQL restituisce un errore se lo stesso prodotto semplice viene assegnato a più prodotti configurabili.
1. **ACSD-60632**: risolve il problema relativo al salvataggio di un nuovo indirizzo ogni volta che si tenta di inserire un ordine, indipendentemente dal fatto che l&#39;ordine sia stato creato correttamente o meno.
1. **ACSD-60816**: è stato risolto il problema che impediva l&#39;esecuzione degli script [!DNL New Relic Browser Monitoring] inseriti dall&#39;agente APM non conformi ai criteri CSP (Content Security Policy).
1. **ACSD-61195**: è stato risolto il problema che impediva la restituzione di elementi del carrello nell&#39;ultima pagina della richiesta GraphQL del carrello.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
