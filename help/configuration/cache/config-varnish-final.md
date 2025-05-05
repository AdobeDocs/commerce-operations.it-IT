---
title: Verifica finale
description: Verifica che la configurazione di Vernice sia configurata correttamente per l’utilizzo con l’applicazione Adobe Commerce.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Verifica finale della configurazione vernice

Ora che si sta utilizzando `default.vcl` generato per l&#39;utente da Commerce, è possibile eseguire alcune verifiche finali per verificare che Vernice funzioni.

## Verificare le intestazioni di risposta HTTP

Utilizza `curl` o un&#39;altra utility per visualizzare le intestazioni di risposta HTTP quando visiti una pagina Commerce in un browser Web.

Innanzitutto, assicurati di utilizzare la [modalità sviluppatore](../cli/set-mode.md#change-to-developer-mode); in caso contrario, le intestazioni non verranno visualizzate.

Ad esempio:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Intestazioni importanti:

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Questo valore è accettabile anche: `X-Magento-Cache-Debug: HIT`.

## Controllare i tempi di caricamento delle pagine

Se Vernice funziona, qualsiasi pagina Commerce con blocchi memorizzabili in cache deve essere caricata in meno di 150 ms. Esempi di tali pagine sono le pagine della porta d’ingresso e della categoria della vetrina.

Utilizza un controllo del browser per misurare i tempi di caricamento delle pagine.

Ad esempio, per utilizzare la finestra di ispezione Chrome:

1. Accedi a qualsiasi pagina di Commerce memorizzabile in cache in Chrome.
1. Fare clic con il pulsante destro del mouse in un punto qualsiasi della pagina.
1. Dal menu popup, fare clic su **[!UICONTROL Inspect Element]**
1. Nel riquadro del controllo fare clic sulla scheda **[!UICONTROL Network]**.
1. Aggiorna la pagina.
1. Scorrere fino alla parte superiore del riquadro del controllo per visualizzare l&#39;URL della pagina visualizzata.

   Nella figura seguente viene illustrato un esempio di caricamento della pagina indice `magento2`.

   ![Fare clic sulla pagina visualizzata](../../assets/configuration/varnish-inspector.png)

   Il tempo di caricamento della pagina viene visualizzato accanto all’URL della pagina. In questo caso, il tempo di caricamento è di 5 ms. Questo aiuta a confermare che Vernice ha memorizzato nella cache la pagina.

1. Per visualizzare le intestazioni di risposta HTTP, fai clic sull’URL della pagina (nella colonna Nome).

   Puoi visualizzare le intestazioni HTTP, descritte più dettagliatamente nella sezione Verifica intestazioni di risposta HTTP.

## Verificare la cache di Commerce

Assicurarsi che la directory `<magento_root>/var/page_cache` sia vuota:

1. Accedi al server Commerce o passa al proprietario del file system.
1. Immetti il comando seguente:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Accedi a una o più pagine Commerce memorizzabili nella cache.
1. Controllare la directory `var/page_cache/`.

   Se la directory è vuota, congratulazioni! Hai configurato correttamente Varnish e Commerce per lavorare insieme.

1. Se la directory `var/page_cache/` è stata cancellata, riavviare Varnish.

>[!TIP]
>
>Se si verificano 503 errori (recupero back-end non riuscito), vedere [Risoluzione dei problemi relativi agli errori 503 (servizio non disponibile)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html?lang=it) nel _Centro assistenza Adobe Commerce_.
