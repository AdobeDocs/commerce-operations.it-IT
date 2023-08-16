---
title: Libreria JavaScript per la privacy
description: Scopri come utilizzare gli strumenti personalizzati per accedere ed eliminare le informazioni personali dei clienti raccolte da Adobe Commerce e Magento Open Source.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Libreria JavaScript per la privacy

La libreria JavaScript per la privacy è un insieme di strumenti che facilitano la creazione di un processo per accedere ed eliminare i dati privati raccolti da Adobe Commerce e Magento Open Source.

I servizi di tracciamento dei dati commerciali possono memorizzare informazioni private applicabili alle normative sulla privacy come [Regolamento generale sulla protezione dei dati (RGPD)](gdpr.md) e [California Consumer Privacy Act (CCPA)](ccpa.md).

Questa libreria fornisce un set di funzioni per creare richieste di dati sulla privacy e raccogliere le loro risposte. Utilizza questa libreria per recuperare e rimuovere i dati memorizzati nel browser da Adobe Commerce e dai servizi di tracciamento dei dati di Magento Open Source.

>[!NOTE]
>
>Se [Modalità di restrizione cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) è abilitato, Commerce non raccoglie dati comportamentali fino al consenso dell’acquirente. Se [!UICONTROL **Modalità di restrizione cookie**] è disabilitato, Commerce raccoglie i dati comportamentali per impostazione predefinita.

## Installazione

La libreria JavaScript per la privacy è disponibile nel seguente percorso CDN: `commerce.adobe.net/magentoprivacy.js`

Una volta ottenuto il file, dovrai aggiungerlo a un modulo personalizzato o a un tema installato nell’istanza Adobe Commerce o di Magento Open Source. Seguire le istruzioni descritte nella [Usa JavaScript personalizzato](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) per eseguire questa attività.

### Inizializzazione

Importa e crea un&#39;istanza di un nuovo `MagentoPrivacy` o utilizzare il `window` per accedere alle funzioni JavaScript per la privacy.

Esempio di utilizzo `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Esempio di utilizzo `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Utilizzo

La libreria JS per la privacy fornisce diverse funzioni per gestire i dati di identità memorizzati nel browser.

`retrieveIdentity()`
: restituisce una promessa JavaScript per un oggetto identità da un servizio nel browser.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: rimuove i dati di identità da un servizio nel browser.
Questa funzione restituisce una promessa JavaScript per un oggetto identità con una `isDeleted` proprietà booleana per indicare se i dati sono stati eliminati.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
