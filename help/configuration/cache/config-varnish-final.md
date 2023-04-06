---
title: Verifica finale
description: Verifica che la configurazione di Varnish sia configurata correttamente per funzionare con l’applicazione Adobe Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---


# Verifica finale della configurazione della vernice

Ora che utilizzi il `default.vcl` generato per te da Commerce, puoi eseguire alcune verifiche finali per assicurarti che Varnish funzioni.

## Verificare le intestazioni di risposta HTTP

Utilizzo `curl` o un&#39;altra utilità per visualizzare le intestazioni di risposta HTTP quando si visita una pagina Commerce in un browser web.

In primo luogo, assicurati di utilizzare [modalità sviluppatore](../cli/set-mode.md#change-to-developer-mode); in caso contrario, le intestazioni non verranno visualizzate.

Ad esempio:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Intestazioni importanti:

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Questo valore è accettabile anche: `X-Magento-Cache-Debug: HIT`.

## Controlla i tempi di caricamento delle pagine

Se Varnish funziona, qualsiasi pagina Commerce con blocchi memorizzabili nella cache deve essere caricata in meno di 150 ms. Esempi di tali pagine sono le pagine della categoria portello anteriore e vetrina.

Utilizzare un ispettore del browser per misurare i tempi di caricamento delle pagine.

Ad esempio, per utilizzare la finestra di ispezione Chrome:

1. Accedi a qualsiasi pagina Commerce memorizzabile nella cache in Chrome.
1. Fai clic con il pulsante destro del mouse in un punto qualsiasi della pagina.
1. Dal menu a comparsa, fai clic su **[!UICONTROL Inspect Element]**
1. Nel riquadro di ispezione fare clic sul pulsante **[!UICONTROL Network]** scheda .
1. Aggiorna la pagina.
1. Scorri fino alla parte superiore del riquadro di ispezione per visualizzare l’URL della pagina che stai visualizzando.

   La figura seguente mostra un esempio di caricamento del `magento2` pagina indice.

   ![Fai clic sulla pagina che stai visualizzando](../../assets/configuration/varnish-inspector.png)

   Il tempo di caricamento della pagina viene visualizzato accanto all’URL della pagina. In questo caso, il tempo di caricamento è di 5 ms. Questo consente di confermare che la pagina è stata memorizzata nella cache da Varnish.

1. Per visualizzare le intestazioni di risposta HTTP, fai clic sull’URL della pagina (nella colonna Nome ).

   Puoi visualizzare le intestazioni HTTP, descritte più dettagliatamente nella sezione Verifica intestazioni di risposta HTTP .

## Verificare la cache Commerce

Assicurati che `<magento_root>/var/page_cache` directory vuota:

1. Accedi al tuo server Commerce o passa al proprietario del file system.
1. Immetti il seguente comando:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Accedi a una o più pagine Commerce memorizzabili nella cache.
1. Controlla la `var/page_cache/` directory.

   Se la directory è vuota, congratulazioni! Hai configurato correttamente Varnish e Commerce per lavorare insieme!

1. Se hai cancellato la `var/page_cache/` riavvia Varnish.

>[!TIP]
>
>Se si verificano errori 503 (Recupero backend non riuscito), vedi [Risoluzione dei problemi relativi agli errori 503 (Servizio non disponibile)](https://support.magento.com/hc/en-us/articles/360034631211) in _Centro assistenza Adobe Commerce_.
