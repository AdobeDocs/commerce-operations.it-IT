---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cb39f5a778ee8af49823f45704d0bb68a13fbf08
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.75

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.75.

QPT v1.1.75 include le seguenti patch:
1. **ACSD-68289**: è stato corretto un problema a causa del quale la ricerca full-text ora restituisce prodotti corrispondenti se la condizione di corrispondenza minima viene soddisfatta collettivamente in tutti i campi ricercabili, anziché richiedere che la condizione venga soddisfatta da un singolo campo.
1. **ACSD-68359**: è stato corretto un problema a causa del quale la selezione di un archivio durante l&#39;estrazione tramite **[!UICONTROL Pick in Store]** non ha più esito negativo a causa di URL lunghi quando nel carrello sono presenti molti prodotti. Precedentemente, questo causava un errore 414 causato da URL eccessivamente lunghi generati durante una vendita in un negozio.
1. **ACSD-68451**: risolve un problema per più siti Web in cui un amministratore di società effettua l&#39;accesso a un sito Web, crea una società non correlata in un altro sito Web, ma è erroneamente collegato a tale società non correlata.
1. **ACSD-68490**: è stato risolto il problema per cui il pulsante **[!UICONTROL Add New Attribute]** è visibile per un utente amministratore con restrizioni durante la creazione di un prodotto configurabile.
1. **ACSD-68517**: è stato corretto un errore di reinvio del modulo nelle pagine di ricerca catalogo e catalogo.
1. **ACSD-68573**: è stato risolto il problema che impediva la corretta applicazione delle autorizzazioni di categoria agli elementi della lista dei desideri del cliente. Dopo la correzione, le voci dell’elenco dei desideri vengono visualizzate e impaginate correttamente sia nel web che in GraphQL.
1. **ACSD-68615**: è stato risolto il problema che causava la visualizzazione di un&#39;eccezione da parte di CLI della compensazione della prenotazione di magazzino se la combinazione elaborata aveva un ID ordine mancante.
1. **ACSD-68793**: è stato corretto un problema a causa del quale prodotti validi venivano rifiutati in modo errato durante l&#39;assegnazione a un catalogo condiviso.
1. **ACSD-68925**: è stato corretto un problema a causa del quale le risposte per le richieste GraphQL ora sono allineate con le specifiche GraphQL su HTTP. Viene restituito un codice di risposta 4XX quando la richiesta non può essere analizzata, non è autorizzata o riscontra un problema generale se la richiesta viene analizzata.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
