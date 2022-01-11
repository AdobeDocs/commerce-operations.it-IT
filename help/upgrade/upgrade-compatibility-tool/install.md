---
title: Installare lo strumento di compatibilità per l’aggiornamento
description: Per installare lo strumento di compatibilità per l’aggiornamento del progetto Adobe Commerce, effettua le seguenti operazioni.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Installare lo strumento di compatibilità per l’aggiornamento

Lo strumento di compatibilità per l’aggiornamento è uno strumento a riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce.

## Flusso di lavoro

Il diagramma seguente mostra il flusso di lavoro previsto durante l’esecuzione dello strumento di compatibilità per l’aggiornamento:

![Diagramma dello strumento di compatibilità dell’aggiornamento](../../assets/upgrade-guide/mvp-diagram-v3.png)

## A chi appartiene lo strumento di compatibilità per l’aggiornamento?

Il seguente caso d’uso descrive il processo tipico di un partner Adobe Commerce per aggiornare l’istanza di un client:

1. Il software engineer di un partner scarica il pacchetto dello strumento di compatibilità per l’aggiornamento dal [Archivio Adobe Commerce](https://repo.magento.com/) e lo esegue durante la fase beta della versione più recente di Adobe Commerce. Consulta la sezione [Scarica lo strumento di compatibilità per l’aggiornamento](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) per ulteriori informazioni.
1. Il Software Engineer genera un’istanza di vaniglia per la versione specifica di Adobe Commerce attualmente installata. Consulta la sezione [Guida collaboratore](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) per ulteriori informazioni sull&#39;utilizzo di `instance` comando per generare un&#39;installazione di vaniglia.
1. L&#39;ingegnere software vede che ci sono diverse aree personalizzate interrotte nei moduli di inventario e catalogo e ottengono anche un punteggio di complessità di X. Vedi il [Sviluppatore](../upgrade-compatibility-tool/developer.md) guida per ulteriori informazioni sul punteggio di complessità.
1. Con queste informazioni, il tecnico del software è in grado di comprendere la complessità dell&#39;aggiornamento ed è in grado di inoltrare queste informazioni al responsabile dell&#39;account del partner.
1. L&#39;Account Manager crea una timeline e un costo per l&#39;aggiornamento di Adobe Commerce, che consente loro di ottenere l&#39;approvazione del proprio manager.
1. Con l&#39;approvazione del loro responsabile, il tecnico del software lavora sulle modifiche del codice richieste per correggere i moduli interrotti.
1. Il Software Engineer esegue lo strumento di compatibilità per l’aggiornamento ancora una volta con un pre-rilascio Adobe Commerce per garantire che non vi siano nuovi problemi e che le modifiche del codice apportate risolvano i problemi rilevati durante la fase beta.
1. Viene eseguito il Check-Out di tutto e il Software Engineer invia il codice a un ambiente di staging in cui i test di regressione confermano che tutti i test sono verdi, il che consente loro di rilasciare l’ultima versione di Adobe Commerce in produzione lo stesso giorno in cui viene rilasciato il pre-rilascio di Adobe Commerce.

   ![Pubblico dello strumento di compatibilità per l’aggiornamento](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Un’istanza di vaniglia è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica di rilascio.

## Prerequisiti

Vedi [prerequisiti](../upgrade-compatibility-tool/prerequisites.md) per ulteriori informazioni.

>[!NOTE]
>
>È possibile eseguire lo strumento di compatibilità per l&#39;aggiornamento in qualsiasi sistema operativo. Non è necessario eseguire lo strumento di compatibilità per l’aggiornamento in cui si trova l’istanza di Adobe Commerce. È necessario che lo strumento di compatibilità per l’aggiornamento abbia accesso al codice sorgente dell’istanza Adobe Commerce. Ad esempio, è possibile installare lo strumento su un server e puntarlo all&#39;installazione Adobe Commerce su un altro server.

Se si esegue lo strumento di compatibilità per l&#39;aggiornamento su un&#39;istanza di Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere una quantità elevata di RAM, almeno 2 GB di RAM.

### Azioni consigliate

Le best practice di Adobe Commerce consigliano di evitare di avere due moduli con lo stesso nome. In questo caso, lo strumento di compatibilità per l’aggiornamento mostra un errore di segmentazione.

Per evitare questo errore, si consiglia di eseguire il `bin` con l&#39;opzione aggiunta `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>La `<dir>` value è la directory in cui si trova l’istanza Adobe Commerce.

La `-m` L’opzione , che consente allo strumento di compatibilità per l’aggiornamento di analizzare ogni modulo specifico in modo indipendente, evita di incontrare due moduli con lo stesso nome nell’istanza Adobe Commerce.

Questa opzione di comando consente anche di analizzare una cartella contenente diversi moduli con lo strumento di compatibilità per l’aggiornamento:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Questa raccomandazione aiuta anche con i problemi di memoria che possono verificarsi durante l’esecuzione dello strumento di compatibilità per l’aggiornamento.

## Scarica lo strumento di compatibilità per l’aggiornamento

Per scaricare lo strumento di compatibilità per l’aggiornamento, esegui il seguente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installa

Per installare lo strumento di compatibilità per l’aggiornamento, è necessario installare i prerequisiti necessari:

* Chiavi di accesso Adobe Commerce
* Compositore
* Node.js

### Chiavi di accesso Adobe Commerce

Devi avere [Chiavi di accesso Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) per scaricare e utilizzare lo strumento di compatibilità per l’aggiornamento. Aggiungi le chiavi di accesso Adobe Commerce al tuo `auth.json` che si trova in `~/.composer` per impostazione predefinita.

>[!WARNING]
>
>Controlla il tuo **COMPOSER_HOME** variabile di ambiente per vedere dove `auth.json` il file si trova.

La **chiave pubblica** corrisponde a _username_ considerando che **chiave privata** è _password_:

### Esempio di chiavi di accesso Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Compositore

Clona l’archivio dello strumento di compatibilità per l’aggiornamento ed esegui `composer install` nel terminale per installare le dipendenze.

>[!WARNING]
>
>Se la **Chiavi di accesso Adobe Commerce** non sono configurati correttamente, lo strumento di compatibilità per l’aggiornamento non verrà installato e si verificheranno degli errori durante l’esecuzione del `composer install` comando.

### Node.js

Per installare Node.js, consulta Node.js [documentazione](https://nodejs.dev/learn/how-to-install-nodejs).

## Estensioni di terze parti

Adobe consiglia di contattare il fornitore dell&#39;estensione per determinare se l&#39;estensione è completamente compatibile con Adobe Commerce 2.4.x.

Vedi [Esegui lo strumento](../upgrade-compatibility-tool/run.md) per informazioni sull’esecuzione dello strumento di compatibilità per l’aggiornamento.
