---
title: Installa il [!DNL Upgrade Compatibility Tool]
description: Segui questi passaggi per installare [!DNL Upgrade Compatibility Tool] per il progetto Adobe Commerce.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# Installa il [!DNL Upgrade Compatibility Tool]

La [!DNL Upgrade Compatibility Tool] è uno strumento a riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce.

## Flusso di lavoro

Il diagramma seguente mostra il flusso di lavoro previsto durante l’esecuzione del [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramma](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Chi è il [!DNL Upgrade Compatibility Tool] per?

Il seguente caso d’uso descrive il processo tipico di un partner Adobe Commerce per aggiornare l’istanza di un client:

1. Il Software Engineer di un partner scarica il [!DNL Upgrade Compatibility Tool] dal pacchetto [Archivio Adobe Commerce](https://repo.magento.com/) e lo esegue durante la fase beta della versione più recente di Adobe Commerce. Consulta la sezione [Scarica la [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) per ulteriori informazioni.
1. Il Software Engineer genera un’istanza di vaniglia per la versione specifica di Adobe Commerce attualmente installata. Consulta la sezione [Guida collaboratore](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) per ulteriori informazioni sull&#39;utilizzo di `instance` comando per generare un&#39;installazione di vaniglia.
1. L&#39;ingegnere software vede che ci sono diverse aree personalizzate interrotte nei moduli di inventario e catalogo e ottengono anche un punteggio di complessità di X. Vedi il [Sviluppatore](../upgrade-compatibility-tool/developer.md) guida per ulteriori informazioni sul punteggio di complessità.
1. Con queste informazioni, il tecnico del software è in grado di comprendere la complessità dell&#39;aggiornamento ed è in grado di inoltrare queste informazioni al responsabile dell&#39;account del partner.
1. L&#39;Account Manager crea una timeline e un costo per l&#39;aggiornamento di Adobe Commerce, che consente loro di ottenere l&#39;approvazione del proprio manager.
1. Con l&#39;approvazione del loro responsabile, il tecnico del software lavora sulle modifiche del codice richieste per correggere i moduli interrotti.
1. Il tecnico del software esegue il [!DNL Upgrade Compatibility Tool] ancora una volta con un pre-rilascio Adobe Commerce per garantire che non ci siano nuovi problemi e che le modifiche al codice risolvano i problemi rilevati durante la fase beta.
1. Viene eseguito il Check-Out di tutto e il Software Engineer invia il codice a un ambiente di staging in cui i test di regressione confermano che tutti i test sono verdi, il che consente loro di rilasciare l’ultima versione di Adobe Commerce in produzione lo stesso giorno in cui viene rilasciato il pre-rilascio di Adobe Commerce.

   ![[!DNL Upgrade Compatibility Tool] pubblico](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Un’istanza di vaniglia è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica di rilascio.

## Prerequisiti

Vedi [prerequisiti](../upgrade-compatibility-tool/prerequisites.md) per ulteriori informazioni.

>[!NOTE]
>
>Puoi eseguire il [!DNL Upgrade Compatibility Tool] in qualsiasi sistema operativo. Non è necessario eseguire il [!DNL Upgrade Compatibility Tool] dove si trova l’istanza Adobe Commerce. È necessario per [!DNL Upgrade Compatibility Tool] per avere accesso al codice sorgente dell’istanza Adobe Commerce. Ad esempio, è possibile installare lo strumento su un server e puntarlo all&#39;installazione Adobe Commerce su un altro server.

Se esegui la [!DNL Upgrade Compatibility Tool] rispetto a un&#39;istanza Adobe Commerce con moduli e file di grandi dimensioni, lo strumento potrebbe richiedere una quantità elevata di RAM, almeno 2 GB di RAM.

### Azioni consigliate

Le best practice di Adobe Commerce consigliano di evitare di avere due moduli con lo stesso nome. In questo caso, la [!DNL Upgrade Compatibility Tool] mostra un errore di segmentazione.

Per evitare questo errore, si consiglia di eseguire il `bin` con l&#39;opzione aggiunta `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>La `<dir>` value è la directory in cui si trova l’istanza Adobe Commerce.

La `-m` consente di [!DNL Upgrade Compatibility Tool] per analizzare ogni modulo specifico in modo indipendente, in modo da evitare di incontrare due moduli con lo stesso nome nell’istanza Adobe Commerce.

Questa opzione di comando consente inoltre di [!DNL Upgrade Compatibility Tool] per analizzare una cartella contenente diversi moduli:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Questa raccomandazione aiuta anche con i problemi di memoria che possono verificarsi durante l&#39;esecuzione di [!DNL Upgrade Compatibility Tool].

## Scarica la [!DNL Upgrade Compatibility Tool]

Per scaricare i [!DNL Upgrade Compatibility Tool], esegui il seguente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installa

Per installare [!DNL Upgrade Compatibility Tool], è necessario installare i prerequisiti necessari:

* Chiavi di accesso Adobe Commerce
* Compositore
* Node.js

### Chiavi di accesso Adobe Commerce

Devi avere [Chiavi di accesso Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) per scaricare e utilizzare [!DNL Upgrade Compatibility Tool]. Aggiungi le chiavi di accesso Adobe Commerce al tuo `auth.json` che si trova in `~/.composer` per impostazione predefinita.

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

Clona il [!DNL Upgrade Compatibility Tool] archivio ed esecuzione `composer install` nel terminale per installare le dipendenze.

>[!WARNING]
>
>Se la **Chiavi di accesso Adobe Commerce** non sono configurati correttamente, [!DNL Upgrade Compatibility Tool] non verrà installato e si otterranno errori durante l&#39;esecuzione del `composer install` comando.

### Node.js

Per installare Node.js, consulta Node.js [documentazione](https://nodejs.dev/learn/how-to-install-nodejs).

## Estensioni di terze parti

Adobe consiglia di contattare il fornitore dell&#39;estensione per determinare se l&#39;estensione è completamente compatibile con Adobe Commerce 2.4.x.

Vedi [Esegui lo strumento](../upgrade-compatibility-tool/run.md) per informazioni sull&#39;esecuzione di [!DNL Upgrade Compatibility Tool].
