---
title: Cache del contenuto statico
description: Comprendi la firma dei contenuti statici e come abilitare o disabilitare la funzione.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Cache del contenuto statico

Per migliorare le prestazioni, Commerce imposta le `Expires` intestazioni per risorse statiche, ad esempio immagini, file JavaScript e CSS.
Impostazione della `Expires` l’intestazione di una risorsa statica indica al browser di memorizzare nella cache la risorsa in corrispondenza di tale URL e di elaborare la versione cache fino alla scadenza.
Questo è un comune [best practice](https://developer.yahoo.com/performance/rules.html#expires=) per la memorizzazione in cache di risorse statiche.

Quando il browser memorizza in cache una risorsa statica e tale risorsa viene modificata sul server, devi cancellare la cache del browser in modo che possa scaricare la nuova versione.
La cancellazione manuale della cache del browser funziona se sei un amministratore del sito web, ma questa non è una richiesta appropriata da fare agli utenti quando desideri che scaricino nuove versioni di una risorsa statica.

## Firma del contenuto statico

La firma dei contenuti statici è una funzione Commerce che consente di annullare la validità della cache del browser per le risorse statiche.
Commerce esegue questa operazione aggiungendo una versione di distribuzione all’URL dei file statici.

Di seguito è riportato un esempio di URL firmato con una versione:

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Quando si esegue il comando [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) per distribuire contenuto statico, Commerce modifica automaticamente la versione di distribuzione.
Questo modifica l’URL dei file statici e forza il browser a caricare la nuova versione dei file.

Commerce abilita questa funzione per impostazione predefinita e Adobe consiglia di mantenere questa funzione abilitata per evitare problemi relativi ai browser che distribuiscono vecchie risorse statiche.

Puoi trovare la configurazione di questa funzione in [**[!UICONTROL Stores]**> Impostazioni > Configurazione >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![Impostazioni dei file statici](../../assets/configuration/static-files-settings.png)

Determina lo stato:

```bash
bin/magento config:show dev/static/sign
```

Abilita o disabilita la firma dei contenuti statici:

```bash
bin/magento config:set dev/static/sign <value>
```

Dove `<value>` è 1 (abilitato) o 0 (disattivato).

## Firme versione

Commerce aggiunge la firma della versione come componente del percorso direttamente dopo l’URL di base dei file di visualizzazione statica per preservare l’integrità degli URL relativi nelle risorse statiche.
In questo modo, inoltre, il browser risolve un URL relativo all’origine firmata corretta mantenendo il contenuto indipendente dalla presenza/assenza del valore della firma.

Quando un browser richiede un’origine firmata dal server, il server utilizza l’URL per riscrivere il componente firma dall’URL.

## Utilizzo durante le distribuzioni

Dopo aver aggiornato o modificato le risorse statiche, devi eseguire la `setup:static-content:deploy` per distribuire la versione e aggiornare il contenuto statico, che forza il caricamento delle risorse aggiornate da parte del browser.

Se distribuisci il codice su un server separato e lo trasferisci in produzione utilizzando un archivio di codice per ridurre i tempi di inattività, devi anche aggiungere il file `pub/static/deployed_version.txt` al repository.
Questo file contiene la nuova versione per il contenuto statico distribuito.
