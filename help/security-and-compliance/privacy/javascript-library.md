---
title: Libreria JavaScript per la privacy
description: Scopri come utilizzare gli strumenti personalizzati per accedere ed eliminare le informazioni personali dei clienti raccolte da Adobe Commerce.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Libreria JavaScript per la privacy

La Libreria JavaScript per la privacy è un insieme di strumenti che facilitano la creazione di un processo per l’accesso e l’eliminazione di dati privati raccolti da Adobe Commerce.

I servizi di tracciamento dati di Commerce possono memorizzare informazioni private applicabili alle normative sulla privacy, come il [Regolamento generale sulla protezione dei dati (RGPD)](gdpr.md) e il [California Consumer Privacy Act (CCPA)](ccpa.md).

Questa libreria fornisce un set di funzioni per creare richieste di dati sulla privacy e raccogliere le loro risposte. Utilizza questa libreria per recuperare e rimuovere i dati memorizzati nel browser dai servizi di tracciamento dati di Adobe Commerce.

>[!NOTE]
>
>Se la modalità di restrizione dei cookie [è abilitata](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html), Commerce non raccoglie i dati comportamentali fino al consenso dell&#39;acquirente. Se la modalità di restrizione dei cookie [!UICONTROL **Modalità**] è disabilitata, Commerce raccoglie i dati comportamentali per impostazione predefinita.

## Installazione

La libreria JavaScript per la privacy è disponibile nel percorso CDN seguente: `commerce.adobe.net/magentoprivacy.js`

Dopo aver installato il file, dovrai aggiungerlo a un modulo personalizzato o a un tema nell’istanza di Adobe Commerce. Segui le istruzioni descritte nell&#39;argomento [Utilizza JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) personalizzato per eseguire questa attività.

### Inizializzazione

Importare e creare un&#39;istanza di un nuovo oggetto `MagentoPrivacy` o utilizzare l&#39;oggetto `window` per accedere alle funzioni di Privacy JavaScript.

Esempio con `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Esempio con `window`:

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
Questa funzione restituisce una promessa JavaScript per un oggetto identità con una proprietà booleana `isDeleted` per indicare se i dati sono stati eliminati.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
