---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.55'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 97b52220f3b254ee17705a22137693abc6008c72
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.55

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.55.

QPT v1.1.55 include le seguenti patch:

1. **ACSD-58383**: è stato risolto il problema che causava la creazione di note di credito duplicate quando si emetteva un rimborso tramite [!DNL REST API] con due richieste identiche eseguite contemporaneamente.
1. **ACSD-58471**: è stato risolto il problema che impediva il caricamento del contenuto dinamico nella pagina dei dettagli del prodotto quando venivano pianificate le regole del prezzo di catalogo associate.
1. **ACSD-58566**: è stato corretto il problema per cui [!DNL GraphQL] restituisce un errore interno del server durante la query del campo `created_at` nella mutazione `addPurchaseOrderComment`.
1. **ACSD-58685**: è stato risolto il problema per cui le e-mail di vendita avviate mentre la comunicazione e-mail è disabilitata vengono comunque inviate dopo la riattivazione della comunicazione e-mail.
1. **ACSD-58735**: è stato risolto il problema che impediva a un amministratore con restrizioni di visualizzare i carrelli acquisti abbandonati nella pagina dell&#39;account cliente in [!UICONTROL Admin] per un sito Web associato.
1. **ACSD-58828**: è stato risolto il problema per cui il messaggio di convalida lato server *address è obbligatorio* viene visualizzato se un campo obbligatorio viene lasciato vuoto, insieme al messaggio di convalida lato client. La convalida lato server non visualizza il messaggio per i campi obbligatori vuoti e la convalida lato client gestirà la notifica di errore, indicando: *Questo è un campo obbligatorio.*
1. **ACSD-60344**: è stato risolto il problema che causava l&#39;invio di e-mail di conferma dell&#39;ordine duplicate quando si utilizzava **[!UICONTROL Purchase Order]** con l&#39;approvazione automatica.
1. **ACSD-61348**: è stato corretto il problema per cui gli elementi della lista dei desideri sono visibili tramite [!DNL GraphQL], ma non nella vetrina in un ambiente con più siti Web.
1. **ACSD-61534**: è stato risolto il problema che impediva l&#39;impostazione della configurazione della progettazione con il comando `bin/magento config:set` e la modifica dei valori bloccati tramite la manipolazione del modulo. Non è possibile aggiornare i valori bloccati impostati da [!DNL CLI] con `--lock-env` o `--lock-conf`.
1. **ACSD-61785**: è stato risolto il problema che impediva l&#39;aggiornamento dell&#39;attributo `reward_warning_notification` tramite [!DNL GraphQL] mutazione e [!DNL REST API] chiamate, allineandone il comportamento con `reward_update_notification`.
1. **ACSD-62591**: è stato corretto il problema per cui il tema non viene cambiato correttamente quando **[!UICONTROL User Agent Rules]** è configurato.
1. **ACSD-62793**: è stato corretto il problema per cui gli attributi `datetime` nei dati esportati non includono il componente tempo. Inoltre, se *[!UICONTROL Fields Enclosure]* è *enabled*, i valori degli attributi nella colonna `additional_attributes` sono racchiusi tra virgolette.
1. **ACSD-62332**: è stato risolto il problema per cui la query dell&#39;elenco prodotti [!DNL GraphQL] è limitata a `total_count` di 10.000 prodotti. Corregge inoltre il problema per cui [!DNL Live Search] imposta la pagina corrente su *1* invece della pagina *2* nei criteri di ricerca quando viene eseguita una query tramite [!DNL GraphQL].

Utilizza il menu a sinistra per passare a una pagina patch specifica.
