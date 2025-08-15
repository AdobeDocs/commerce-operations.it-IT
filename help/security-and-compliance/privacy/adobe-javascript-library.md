---
title: Libreria JavaScript di Adobe Privacy
description: Scopri come utilizzare gli strumenti personalizzati per accedere ed eliminare le informazioni personali dei clienti raccolte da Adobe Commerce.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Libreria JavaScript di Adobe Privacy

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

La [libreria JavaScript di Adobe Privacy](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=it) è un insieme di strumenti che facilitano la creazione di un processo per l&#39;accesso e l&#39;eliminazione di dati privati.

I servizi di tracciamento dati di Adobe Commerce possono memorizzare informazioni private applicabili alle normative sulla privacy, come il [Regolamento generale sulla protezione dei dati (RGPD)](gdpr.md) e il [California Consumer Privacy Act (CCPA)](ccpa.md).

Questa libreria fornisce un set unificato di funzioni per creare richieste di dati sulla privacy, inviarle alle implementazioni di ciascun prodotto e raccogliere le risposte. Utilizza questa libreria per recuperare e rimuovere i dati memorizzati nel browser da questi servizi di tracciamento dei dati.

## Installazione

Per scaricare il file di libreria, utilizza uno dei metodi seguenti:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Dopo aver installato il file, dovrai aggiungerlo a un modulo personalizzato o a un tema nell’istanza di Adobe Commerce. Segui le istruzioni descritte nell&#39;argomento [Utilizza JavaScript](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) personalizzato per eseguire questa attività.

## Utilizzo

La libreria JS di AdobePrivacy fornisce diverse funzioni per gestire i dati di identità memorizzati nel browser.

`retrieveIdentities()`
: restituisce un array di identità da un servizio insieme a un array di identità non trovate nel servizio

`removeIdentities()`
: rimuove le identità dal browser e restituisce un array di oggetti identità con una proprietà booleana `isDeleteClientSide` per indicare se i dati sono stati eliminati.

`retrieveThenRemoveIdentities()`
: questa funzione è simile a `removeIdentities()` in quanto recupera un array di identità e lo rimuove dal browser.

Per ulteriori informazioni ed esempi sull&#39;utilizzo di queste funzioni, vedere la [documentazione ufficiale della libreria](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=it).

### Inizializzazione

Crea un&#39;istanza di un nuovo oggetto `AdobePrivacy` per utilizzare la libreria JS di AdobePrivacy nel codice di implementazione.

```js
var adobePrivacy = new AdobePrivacy({});
```

Il costruttore accetta un oggetto di configurazione con parametri durante la creazione dell&#39;istanza.
Per un elenco di questi parametri di configurazione, consulta la [documentazione ufficiale della libreria](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html?lang=it).
