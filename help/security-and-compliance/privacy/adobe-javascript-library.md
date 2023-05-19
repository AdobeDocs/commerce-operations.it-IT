---
title: Libreria JavaScript di Adobe Privacy
description: Scopri come utilizzare gli strumenti personalizzati per accedere ed eliminare le informazioni personali dei clienti raccolte da Adobe Commerce e Magenti Open Source.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Libreria JavaScript di Adobe Privacy

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

Il [Libreria JavaScript di Adobe Privacy](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) è un insieme di strumenti che facilitano la creazione di un processo per l’accesso e l’eliminazione di dati privati.

I servizi Adobe Commerce e di tracciamento dei dati di Magento Open Source possono memorizzare informazioni private applicabili alle normative sulla privacy come [Regolamento generale sulla protezione dei dati (RGPD)](gdpr.md) e [California Consumer Privacy Act (CCPA)](ccpa.md).

Questa libreria fornisce un set unificato di funzioni per creare richieste di dati sulla privacy, inviarle alle implementazioni di ciascun prodotto e raccogliere le risposte. Utilizza questa libreria per recuperare e rimuovere i dati memorizzati nel browser da questi servizi di tracciamento dei dati.

## Installazione

Per scaricare il file di libreria, utilizza uno dei metodi seguenti:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Una volta ottenuto il file, dovrai aggiungerlo a un modulo personalizzato o a un tema installato nell’istanza Adobe Commerce e di Magento Open Source. Seguire le istruzioni descritte nella [Usa JavaScript personalizzato](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) per eseguire questa attività.

## Utilizzo

La libreria JS di AdobePrivacy fornisce diverse funzioni per gestire i dati di identità memorizzati nel browser.

`retrieveIdentities()`
: restituisce un array di identità da un servizio insieme a un array di identità non trovate nel servizio

`removeIdentities()`
: rimuove le identità dal browser e restituisce un array di oggetti identità con un `isDeleteClientSide` proprietà booleana per indicare se i dati sono stati eliminati.

`retrieveThenRemoveIdentities()`
: questa funzione è simile a `removeIdentities()` in quanto recupera un array di identità e lo rimuove dal browser.

Per ulteriori informazioni ed esempi sull&#39;utilizzo di queste funzioni, vedere [documentazione ufficiale della libreria](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Inizializzazione

Crea un&#39;istanza di un nuovo `AdobePrivacy` oggetto per utilizzare la libreria JS di AdobePrivacy nel codice di implementazione.

```js
var adobePrivacy = new AdobePrivacy({});
```

Il costruttore accetta un oggetto di configurazione con parametri durante la creazione dell&#39;istanza.
Consulta la sezione [documentazione ufficiale della libreria](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) per un elenco di questi parametri di configurazione.
