---
title: Riferimento per i percorsi di configurazione dei servizi
description: Vedi un elenco dei valori di configurazione dei servizi.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# Riferimento per i percorsi di configurazione dei servizi

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Servizi**.

La [`magento app:config:dump` command](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che dovrebbe essere nel controllo della sorgente. Per ignorare facoltativamente le impostazioni di configurazione o per impostare le impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento _not_ elenco [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi API Web per Commerce

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Servizi** > **API web**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Charset di risposta predefinito | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti accesso anonimo agli ospiti | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi OAuth

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Servizi** > **OAuth**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Durata del token del cliente (ore) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata del token amministratore (ore) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilità di pulizia | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credenziali del consumatore OAuth HTTP Post maxredirects | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout del servizio HTTP Post per le credenziali del consumatore OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
