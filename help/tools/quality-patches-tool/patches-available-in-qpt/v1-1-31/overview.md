---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.31'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.31.
feature: Tools and External Services
role: Admin
exl-id: d37c7f05-1bf5-495b-9b9e-ac9dd117a3ab
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
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.31

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.31.

QPT v1.1.31 include le seguenti patch:

1. **ACSD-50817**: ottimizza l&#39;esecuzione più rapida del processo cron `sales_clean_quotes` aggiungendo un indice composito nelle colonne `store_id` e `updated_at` della tabella delle virgolette.
1. **ACSD-50345**: è stato risolto il problema per cui: [!DNL Google reCAPTCHA v2] non viene ricaricato dopo l&#39;invio di un pagamento non riuscito, [!DNL Google reCAPTCHA v3 Invisible] non sta lavorando all&#39;estrazione e non è possibile effettuare l&#39;ordine e l&#39;evento [!UICONTROL PlaceOrder] non è stato attivato.
1. **ACSD-49392**: risolve il problema se lo stato dell&#39;ordine diventa chiuso dopo un rimborso parziale per un prodotto nel pacchetto.
1. **ACSD-51036**: è stato risolto il problema che causava la sovrascrittura delle informazioni sullo stato di spedizione nella tabella [!UICONTROL Items Ordered] durante le chiamate API REST simultanee.
1. **ACSD-50858**: è stato risolto il problema relativo all&#39;utilizzo errato di un coupon dopo un pagamento non riuscito con carta.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
