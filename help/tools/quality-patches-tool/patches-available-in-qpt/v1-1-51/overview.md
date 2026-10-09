---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.51'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.51.
feature: Tools and External Services
role: Admin, Developer
exl-id: 277b6301-944b-4913-84a3-bbcca2c92ce1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.51

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.51.

QPT v1.1.51 include le seguenti patch:

1. **ACSD-59786**: è stato risolto il problema che causava la restituzione da parte di GraphQL di un errore interno del server durante il tentativo di ottenere un ID preventivo per un preventivo scaduto.
1. **ACSD-60234**: è stato risolto il problema che causava la visualizzazione di un importo errato in [!DNL PayPal] quando lo sconto veniva applicato tramite il metodo di pagamento.
1. **ACSD-59967**: è stato risolto il problema che impediva a [!DNL Google Maps] di eseguire correttamente il rendering.
1. **ACSD-60326**: è stato corretto il problema che si verificava durante la query GraphQL per lo stato di restituzione del cliente.
1. **ACSD-60538**: è stato risolto il problema per cui se un prodotto è disabilitato in *[!UICONTROL All Store Views]* e abilitato solo in ambiti di visualizzazione specifici dell&#39;archivio, gli attributi del prodotto non vengono visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto.
1. **ACSD-60631**: è stato corretto il problema per cui GraphQL restituisce un errore se lo stesso prodotto semplice viene assegnato a più prodotti configurabili.
1. **ACSD-60632**: risolve il problema relativo al salvataggio di un nuovo indirizzo ogni volta che si tenta di inserire un ordine, indipendentemente dal fatto che l&#39;ordine sia stato creato correttamente o meno.
1. **ACSD-60816**: è stato risolto il problema che impediva l&#39;esecuzione degli script [!DNL New Relic Browser Monitoring] inseriti dall&#39;agente APM non conformi ai criteri CSP (Content Security Policy).
1. **ACSD-61195**: è stato risolto il problema che impediva la restituzione di elementi del carrello nell&#39;ultima pagina della richiesta GraphQL del carrello.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
