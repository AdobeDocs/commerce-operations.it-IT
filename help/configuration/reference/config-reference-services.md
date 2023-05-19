---
title: Riferimento percorsi di configurazione servizi
description: Consulta un elenco di valori di configurazione dei servizi.
exl-id: 77818c54-21ae-4a66-81bf-468bd7d09cda
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# Riferimento percorsi di configurazione servizi

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Servizi**.

Il [`magento app:config:dump` comando](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente. Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento fa _non_ list [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi API Web Commerce

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Servizi** > **API web**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Charset di risposta predefinito | `webapi/soap/charset` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti accesso anonimo come ospite | `webapi/webapisecurity/allow_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi OAuth

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Servizi** > **OAuth**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Durata token cliente (ore) | `oauth/access_token_lifetime/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata token di amministrazione (ore) | `oauth/access_token_lifetime/admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Probabilità pulizia | `oauth/cleanup/cleanup_probability` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza | `oauth/cleanup/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza | `oauth/consumer/expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Credenziali consumer OAuth HTTP Post maxredirect | `oauth/consumer/post_maxredirects` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout post HTTP delle credenziali del consumatore OAuth | `oauth/consumer/post_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
