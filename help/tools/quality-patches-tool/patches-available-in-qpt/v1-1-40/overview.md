---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.40'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.40.
feature: Tools and External Services
role: Admin, Developer
exl-id: fd0caa46-834a-4553-bb59-e4c968c59c15
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
source-wordcount: '301'
ht-degree: 0%
---
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.40

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.40.

QPT v1.1.40 include le seguenti patch:

1. **ACSD-54680**: è stato risolto il problema che impediva l&#39;elaborazione di un preventivo B2B inviato per un prodotto con più origini assegnate.
1. **ACSD-54040**: è stato corretto il problema per cui il campo *[!UICONTROL Created]* è vuoto nei dettagli dell&#39;ordine quando i moduli B2B sono abilitati.
1. **ACSD-54319**: è stato risolto il problema che causava la visualizzazione dello zero del prezzo del prodotto nel report *[!UICONTROL Product in Cart]*.
1. **ACSD-53378**: migliora il tempo di caricamento delle pagine di estrazione per i clienti che dispongono di rubriche di grandi dimensioni.
1. **ACSD-52657**: è stato risolto il problema che impediva l&#39;aggiornamento del minicart nello storeview secondario, che utilizza un sottodominio.
1. **ACSD-53414**: è stato corretto il problema per cui un utente amministratore con restrizioni può visualizzare le pagine CMS al di fuori del proprio ambito di autorizzazioni.
1. **ACSD-54472**: risolve il problema che consente ai clienti di una società rifiutata di autenticarsi e ai clienti di una società bloccata o rifiutata di effettuare ordini. La patch aggiunge una convalida aggiuntiva per gli endpoint di GraphQL.
1. **ACSD-52801**: aggiunge l&#39;opzione per effettuare una corrispondenza parziale durante la ricerca di prodotti in GraphQL.
1. **ACSD-55004**: è stato risolto il problema relativo agli arresti anomali della convalida durante il caricamento di un file di importazione di dimensioni superiori al valore configurato in `php.ini`.
1. **ACSD-54989**: è stato risolto il problema che impediva all&#39;amministratore della società di effettuare un ordine quando *[!UICONTROL Enable Purchase Orders]* è impostato su *[!UICONTROL Yes]* e *[!UICONTROL Purchase Order]* è impostato su *[!UICONTROL No]*.
1. **ACSD-54007**: è stato corretto l&#39;errore *&quot;Chiave di matrice non definita &quot;_scope&quot;&quot;* durante l&#39;importazione dei dati del cliente.
1. **ACSD-55031**: corregge l&#39;errore *Tipo &quot;misto&quot; che non può ammettere valori Null* durante la compilazione.
1. **ACSD-54961**: è stato risolto il problema che impediva a un utente amministratore con restrizioni di aggiornare in massa lo stato *Revisione prodotto*.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
