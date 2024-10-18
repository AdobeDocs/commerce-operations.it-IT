---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.53.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: e87723f395563b645d25bac6e6cb7887ce23f1ab
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.53

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.53.

QPT v1.1.53 include le seguenti patch:

1. **ACSD-48318**: è stato risolto il problema che impediva la nidificazione dell&#39;emulazione dell&#39;ambiente. Ora, l&#39;emulazione inizia durante la chiamata `send()` una volta che l&#39;emulazione si arresta durante la chiamata `getInfoBlockHtml()`.
1. **ACSD-59930**: migliora le prestazioni dei flussi *[!UICONTROL Create]*, *[!UICONTROL Save]* e *[!UICONTROL Delete]* della società.
1. **ACSD-60584**: è stato risolto il problema per cui un token di accesso creato per l&#39;utente in un sito Web può accedere o modificare le informazioni del cliente in altri siti Web.
1. **ACSD-60804**: è stato risolto il problema che causava l&#39;errore *Chiamata a una funzione membro `getSuperUserId()` su null* in seguito alla modifica di un cliente collegato a una società eliminata.
1. **ACSD-61133**: è stato risolto il problema che causava l&#39;eliminazione dei preventivi da parte del cron `sales_clean_quotes` da ordini di acquisto non approvati.
1. **ACSD-61528**: è stato risolto il problema che impediva il recupero dei ruoli da [!UICONTROL Admin] tramite GraphQL.
1. **ACSD-61553**: è stato corretto il problema a causa del quale gli sconti di *[!UICONTROL Cart Price Rule]* non vengono calcolati correttamente quando al prodotto vengono applicati più sconti con priorità diverse e *[!UICONTROL Maximum Qty Discount is Applied To]*.
1. **ACSD-61667**: migliora le prestazioni di inventario per la creazione della spedizione nel caso di molte origini con *Prelievo in-store*.
1. **ACSD-61969**: è stato risolto il problema per cui l&#39;utente deve digitare un codice coupon con distinzione tra maiuscole e minuscole che corrisponda esattamente al codice coupon configurato.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
