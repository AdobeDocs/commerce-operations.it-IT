---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.57'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.57.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 82b8d22438107680cdf47057e0db3e15bf819599
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.57

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.57.

QPT v1.1.57 include le seguenti patch:

1. **ACSD-57570**: è stato risolto il problema che impediva a un utente amministratore con restrizioni di accedere a un particolare archivio di visualizzare sempre tutti i cataloghi condivisi a cui sono assegnati i prodotti o a clienti che non potevano salvare, con conseguenti incongruenze nel sistema.
1. **ACSD-58325**: è stato risolto il problema per cui il pulsante [!UICONTROL Import] è disponibile anche dopo un errore di convalida.
1. **ACSD-59083**: è stato risolto il problema che causava la mancata individuazione di _Tabella o visualizzazione di base_ se l&#39;aggiornamento di [!DNL mview] è in esecuzione contemporaneamente.
1. **ACSD-61622**: è stato risolto il problema che causava la mancanza di [!DNL FedEx] tariffe specifiche dell&#39;account nella risposta. ACSD-61622 sostituisce la correzione documentata nella migrazione dell&#39;integrazione del metodo di spedizione [[!DNL FedEx] da [!DNL SOAP] a [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api).
1. **ACSD-61895**: è stato corretto il problema per cui la query delle categorie [!DNL GraphQL] restituisce categorie con autorizzazione *allow* anche se la categoria radice non dispone dell&#39;autorizzazione *allow*.
1. **ACSD-62212**: è stato risolto il problema che impediva la traduzione del contenuto dell&#39;e-mail [!UICONTROL Forgot Password] nella lingua della visualizzazione archivio.
1. **ACSD-62481**: è stato risolto il problema che causava lo svuotamento del carrello del cliente anche se [!UICONTROL Persistence] era abilitato.
1. **ACSD-62629**: è stato corretto il problema per cui un elenco di prodotti utilizzato in [!UICONTROL Widgets] non rispetta la condizione della categoria.
1. **ACSD-62635**: è stato risolto il problema che impediva la corretta visualizzazione dei prodotti correlati a più store nella query di prodotto [!DNL GraphQL].
1. **ACSD-62671**: è stato risolto il problema che impediva alla richiesta [!DNL GraphQL] di restituire informazioni aggiornate sull&#39;indirizzo al primo tentativo.
1. **ACSD-62689**: è stato risolto il problema che impediva al cliente di aggiungere categorie in [!UICONTROL Related Product Rules] e [!UICONTROL Widgets] dopo la profondità 4.
1. **ACSD-62708**: è stato risolto il problema che causava la visualizzazione di [!UICONTROL px] e non di [!UICONTROL pt] del tipo di carattere dell&#39;editor [!DNL TinyMCE] 7 dopo l&#39;applicazione della correzione da [!UICONTROL ACP2E-3430]. Ora è anche possibile impostare la dimensione del carattere in [!UICONTROL px] invece di [!UICONTROL pt].
1. **ACSD-62758**: è stato risolto il problema che impediva il corretto rendering dei video dei prodotti nella pagina dei dettagli [!UICONTROL Configurable Product] se l&#39;URL contiene opzioni selezionate.
1. **ACSD-62951**: è stato corretto il problema per cui l&#39;e-mail [!UICONTROL Credit Memo] viene inviata senza includere elementi e totali.
1. **ACSD-62965**: è stato corretto il problema per cui un messaggio *LocalizedException* non è incluso nel posizionamento dell&#39;ordine [!DNL GraphQL response].
1. **ACSD-63286**: risolve il problema per cui i prodotti assegnati a un catalogo condiviso tramite API non vengono visualizzati nella vetrina finché non viene eseguita una reindicizzazione manuale.
1. **ACSD-63326**: è stato risolto il problema che causava il reindirizzamento dell&#39;amministratore a una pagina interrotta dopo l&#39;invio di un ordine dal backend.


Utilizza il menu a sinistra per passare a una pagina patch specifica.
