---
title: Cache del contenuto statico
description: Comprendi la firma di contenuti statici e come abilitare o disabilitare la funzione.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Cache del contenuto statico

Per migliorare le prestazioni, Commerce imposta le intestazioni `Expires` per le risorse statiche, ad esempio immagini, JavaScript e file CSS.
L&#39;impostazione dell&#39;intestazione `Expires` su una risorsa statica indica al browser di memorizzare la risorsa nella cache in corrispondenza di tale URL e di distribuire la versione memorizzata nella cache fino alla scadenza.
Si tratta di una [best practice](https://developer.yahoo.com/performance/rules.html#expires=) comune per memorizzare nella cache risorse statiche.

Quando il browser memorizza in cache una risorsa statica che cambia sul server, è necessario cancellare la cache del browser in modo che possa scaricare la nuova versione.
La cancellazione manuale della cache del browser funziona se sei un amministratore del sito web, ma questa non è una richiesta appropriata da effettuare da parte degli utenti quando desideri che scarichino nuove versioni di una risorsa statica.

## Firma del contenuto statico

La firma di contenuti statici è una funzione di Commerce che consente di annullare la validità della cache del browser per le risorse statiche.
Commerce esegue questa operazione aggiungendo una versione di distribuzione all’URL dei file statici.

Di seguito è riportato un esempio di URL firmato con una versione:

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Quando si esegue il comando [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) per distribuire il contenuto statico, Commerce modifica automaticamente la versione della distribuzione.
In questo modo viene modificato l’URL dei file statici e viene forzato il browser a caricare la nuova versione dei file.

Commerce abilita questa funzione per impostazione predefinita; Adobe consiglia di mantenerla abilitata per evitare problemi relativi ai browser che utilizzano vecchie risorse statiche.

La configurazione per la firma del contenuto statico è in [**[!UICONTROL Stores]**> Impostazioni > Configurazione >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures).

- **Solo locale**: questa configurazione è disponibile se il sito è **non** in [Modalità di produzione](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html?lang=it#production-mode).
- **Cloud**: questa configurazione è nascosta perché la modalità di produzione è rigorosamente applicata; è quindi necessario utilizzare la riga di comando come illustrato di seguito.

![Impostazioni file statici](../../assets/configuration/static-files-settings.png)

Determinare lo stato:

```bash
bin/magento config:show dev/static/sign
```

Attiva o disattiva la firma di contenuto statico:

```bash
bin/magento config:set dev/static/sign <value>
```

Dove `<value>` è 1 (abilitato) o 0 (disabilitato).

## Firme delle versioni

Commerce aggiunge la firma della versione come componente percorso direttamente dopo l’URL di base dei file di visualizzazione statica per preservare l’integrità degli URL relativi nelle risorse statiche.
Questo costringe anche il browser a risolvere un URL relativo alla sorgente firmata corretta mantenendo il suo contenuto indipendente dalla presenza/assenza del valore della firma.

Quando un browser richiede un’origine firmata dal server, quest’ultimo utilizza le riscritture URL per rimuovere il componente firma dall’URL.

## Utilizzo durante le distribuzioni

Dopo aver aggiornato o modificato le risorse statiche, è necessario eseguire il comando `setup:static-content:deploy` per distribuire la versione e aggiornare il contenuto statico, forzando il browser a caricare le risorse aggiornate.

Se si distribuisce il codice in un server separato e lo si sposta in produzione utilizzando un repository di codice per ridurre i tempi di inattività, è necessario aggiungere anche il file `pub/static/deployed_version.txt` all&#39;archivio.
Questo file contiene la nuova versione per il contenuto statico distribuito.
