---
title: Informazioni per gli sviluppatori dello strumento di compatibilità di aggiornamento
description: Personalizza lo strumento di compatibilità per l’aggiornamento utilizzando l’integrazione dell’indice API.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Aggiornare le informazioni per gli sviluppatori dello strumento di compatibilità

Questo argomento contiene informazioni per gli sviluppatori che lavorano a stretto contatto con il codice Adobe Commerce e desiderano ottenere informazioni dettagliate sullo strumento di compatibilità per l’aggiornamento. È possibile utilizzare questa conoscenza per personalizzare i componenti dello strumento.

## Integrazione dell’indice API di Adobe Commerce

L’integrazione dell’indice API di Adobe Commerce è una soluzione di integrazione interna che include un set di strumenti per esplorare le estensioni Adobe Commerce sviluppate da Adobe, Partner Adobe Commerce e fornitori di terze parti in base all’analisi del codice statico.

L’integrazione con l’indice API Adobe Commerce viene eseguita tramite:

`sut\Domain\MRay\MRayInterface`

È implementato tramite `config/services.yaml` file. Il suo valore decide dove la risposta dei metodi `api()` e `modules()` viene da.

Modifica questo file per personalizzare la risposta in base all&#39;installazione. Sostituisci il valore assegnato a `sut\Domain\MRay\MRayInterface`:

### Esempio di valore personalizzato

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

Nell’esempio precedente, lo strumento di compatibilità per l’aggiornamento utilizza `@sut_mray_mock` come `MRayInterface` implementazione. Le risposte della `api()` e `modules()` i metodi provengono dai file seguenti:

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>Quando si modifica la `services.yaml` file, elimina `var/cache/` per applicare correttamente le modifiche.

## Test di unità

Per eseguire i test di unità, eseguire uno dei seguenti comandi:

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Test di integrazione

Per eseguire i test di integrazione, esegui uno dei seguenti comandi:

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Test di accettazione

1. Prima di eseguire i test di accettazione, devi impostare l’URL di Adobe Commerce nel `phpunit` file di configurazione.
1. Copia il valore predefinito `tests/acceptance/phpunit.xml` (senza il suffisso .dist).
1. Modificare la `TESTS_BASE_URL` per puntare all’URL Adobe Commerce di cui desideri eseguire il test.
1. Per eseguire i test di accettazione, eseguire uno dei seguenti comandi:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## Test di unità GraphQL e analisi di codice ESLint

### Requisiti

>[!NOTE]
>
>È necessario avere Node.js sul sistema, vedi [Documentazione di Node.js](https://nodejs.dev/learn/how-to-install-nodejs).

Le seguenti istruzioni sono per i sistemi MacOS:

1. Apri un terminale e passa alla directory principale del progetto.
1. Installa le dipendenze del progetto:

   ```bash
   npm install
   ```

### Test di unità GraphQL

La [Jest](https://jestjs.io/docs/getting-started) è stato utilizzato il framework per creare questi unit test JS:

I test sono all&#39;interno `dev/tests/Js`.

Gli schemi di stringa per il test si trovano all’interno `dev/tests/Acceptance/_files/graphql_schemas`.

Eseguire prove di unità o `jest` come segue:

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### Analisi del codice ESLint

[ESLint](https://eslint.org/docs/user-guide/getting-started) è uno strumento di analisi del codice statico per identificare i pattern problematici presenti nel codice JavaScript, con l’obiettivo di rendere il codice più coerente ed evitare i bug.

Esegui `eslint` analisi del codice come segue:

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Punteggio di complessità

La **punteggio di complessità** è una figura che indica quanto potrebbe essere difficile un aggiornamento dalla versione corrente a quella nuova. Numeri inferiori indicano aggiornamenti più semplici.

>[!NOTE]
>
>I punteggi di complessità sono compresi tra 0 e∞.

Questo punteggio si basa sui risultati estratti dall’analisi:

- Numero di problemi individuati
- Gravità dei problemi individuati

Lo strumento di compatibilità per l’aggiornamento calcola questo punteggio in base alla formula di valutazione della complessità riportata di seguito.

### Formula del punteggio di complessità

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Sono valori assoluti.
