---
title: Libreria JavaScript per la privacy
description: Scopri come utilizzare strumenti personalizzati per accedere ed eliminare le informazioni personali dei clienti raccolte da Adobe Commerce e Magenti Open Source.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Libreria JavaScript per la privacy

La Libreria JavaScript per la privacy è un insieme di strumenti che facilitano la creazione di un processo per l’accesso e l’eliminazione dei dati privati raccolti da Adobe Commerce e Magenti Open Source.

I servizi di tracciamento dei dati Commerce possono memorizzare informazioni private applicabili alle normative sulla privacy come [Regolamento generale sulla protezione dei dati (RGPD)](gdpr.md) e [California Consumer Privacy Act (CCPA)](ccpa.md).

Questa libreria fornisce un set di funzioni per la creazione di richieste di dati sulla privacy e la raccolta delle relative risposte. Utilizza questa libreria per recuperare e rimuovere i dati memorizzati nel browser da Adobe Commerce e dai servizi di tracciamento dei dati di Magento Open Source.

>[!NOTE]
>
>Se [Modalità di restrizione dei cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) , Commerce non raccoglie dati comportamentali finché l’acquirente non acconsente. Se [!UICONTROL **Modalità di restrizione dei cookie**] è disattivato, Commerce raccoglie dati comportamentali per impostazione predefinita.

## Installazione

La libreria JavaScript per la privacy è disponibile nel seguente percorso CDN: `commerce.adobe.net/magentoprivacy.js`

Dopo aver ottenuto il file, dovrai aggiungerlo a un modulo o a un tema personalizzato installato nella tua istanza Adobe Commerce o Magenti Open Source. Segui le istruzioni descritte nella sezione [Usa JavaScript personalizzato](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) argomento per eseguire questa attività.

### Inizializzazione

Importare e creare un&#39;istanza nuova `MagentoPrivacy` o utilizzare `window` per accedere alle funzioni JavaScript di Privacy.

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

La Libreria JS per la privacy fornisce varie funzioni per gestire i dati di identità memorizzati nel browser.

`retrieveIdentity()`
: Restituisce una promessa JavaScript per un oggetto identity proveniente da un servizio nel browser.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Rimuove i dati di identità da un servizio nel browser.
Questa funzione restituisce una promessa JavaScript per un oggetto identity con un `isDeleted` proprietà booleana per indicare se i dati sono stati eliminati.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
