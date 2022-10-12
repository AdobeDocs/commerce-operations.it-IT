---
title: Adobe Libreria JavaScript per la privacy
description: Scopri come utilizzare strumenti personalizzati per accedere ed eliminare le informazioni personali dei clienti raccolte da Adobe Commerce e Magenti Open Source.
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Adobe Libreria JavaScript per la privacy

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

La [Adobe Libreria JavaScript per la privacy](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) è un insieme di strumenti che facilitano la creazione di un processo per l’accesso e l’eliminazione di dati privati.

Adobe Commerce e i servizi di tracciamento dei dati di Magento Open Source possono memorizzare informazioni private applicabili alle normative sulla privacy come [Regolamento generale sulla protezione dei dati (RGPD)](gdpr.md) e [California Consumer Privacy Act (CCPA)](ccpa.md).

Questa libreria fornisce un set unificato di funzioni per la creazione di richieste di dati sulla privacy, l’invio di tali richieste alle implementazioni di ogni prodotto e la raccolta delle risposte. Utilizza questa libreria per recuperare e rimuovere i dati memorizzati nel browser da questi servizi di tracciamento dei dati.

## Installazione

Utilizza uno dei metodi seguenti per scaricare il file della libreria:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Dopo aver ottenuto il file, dovrai aggiungerlo a un modulo o a un tema personalizzato installato nella tua istanza Adobe Commerce e Magenti Open Source. Segui le istruzioni descritte nella sezione [Usa JavaScript personalizzato](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) argomento per eseguire questa attività.

## Utilizzo

La libreria JS di Adobe Privacy fornisce varie funzioni per gestire i dati di identità memorizzati nel browser.

`retrieveIdentities()`
: Restituisce una matrice di identità da un servizio insieme a una matrice di identità non trovata nel servizio

`removeIdentities()`
: Rimuove le identità dal browser e restituisce un array di oggetti Identity con un `isDeleteClientSide` proprietà booleana per indicare se i dati sono stati eliminati.

`retrieveThenRemoveIdentities()`
: Questa funzione è simile a `removeIdentities()` in quanto recupera un array di identità e le rimuove dal browser.

Per ulteriori informazioni ed esempi sull’utilizzo di queste funzioni, consulta la sezione [documentazione ufficiale della biblioteca](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Inizializzazione

Creare una nuova istanza `AdobePrivacy` per utilizzare la libreria JS di AdobePrivacy nel codice di implementazione.

```js
var adobePrivacy = new AdobePrivacy({});
```

Il costruttore accetta un oggetto di configurazione con parametri durante la creazione dell&#39;istanza.
Fai riferimento a [documentazione ufficiale della biblioteca](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) per un elenco di questi parametri di configurazione.
