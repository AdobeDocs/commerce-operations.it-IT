---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
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
# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.75

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.75.

QPT v1.1.75 include le seguenti patch:
1. **ACSD-68289**: è stato corretto un problema a causa del quale la ricerca full-text ora restituisce prodotti corrispondenti se la condizione di corrispondenza minima viene soddisfatta collettivamente in tutti i campi ricercabili, anziché richiedere che la condizione venga soddisfatta da un singolo campo.
1. **ACSD-68359**: è stato corretto l&#39;errore *414* durante la selezione di **[!UICONTROL Pick in Store]** con carrelli di grandi dimensioni.
1. **ACSD-68451**: risolve un problema per più siti Web in cui un amministratore di società effettua l&#39;accesso a un sito Web, crea una società non correlata in un altro sito Web, ma è erroneamente collegato a tale società non correlata.
1. **ACSD-68517**: è stato corretto un errore di reinvio del modulo in **[!UICONTROL Catalog]** e **[!UICONTROL Catalog Search]** pagine.
1. **ACSD-68490**: pulsante **[!UICONTROL Add New Attribute]** visibile all&#39;amministratore con restrizioni durante la creazione del prodotto configurabile.
1. **ACSD-68573**: le autorizzazioni per le categorie non sono state applicate agli elementi della lista dei desideri del cliente. La visualizzazione e l&#39;impaginazione nella vetrina Web e in [!DNL GraphQL] non sono corrette.
1. **ACSD-68615**: è stato risolto il problema che causava la visualizzazione di un&#39;eccezione da parte di CLI della compensazione della prenotazione di magazzino se la combinazione elaborata aveva un ID ordine mancante.
1. **ACSD-68793**: è stato corretto un problema a causa del quale prodotti validi venivano rifiutati in modo errato durante l&#39;assegnazione a un catalogo condiviso.
1. **ACSD-68925**: è stato corretto un problema a causa del quale le risposte per le richieste GraphQL ora sono allineate con le specifiche GraphQL su HTTP. Viene restituito un codice di risposta 4XX quando la richiesta non può essere analizzata, non è autorizzata o riscontra un problema generale se la richiesta viene analizzata.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
