---
title: Cancellazione della cache con vernice
description: Scopri come funziona il clearing della cache con l’acceleratore di web-caching di Varnish per Adobe Commerce. Scopri le tecniche di gestione e ottimizzazione della cache.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T22:18:33.462Z'
TQID: 'https://experienceleague.adobe.com/ePhbVWjx-hX99p8OKiKqzT-w2KZu-XjS1XieuStKqc4'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 405
ht-degree: 0%

---

# Cancellazione della cache con vernice

Questo argomento illustra le nozioni di base sull’utilizzo di Varnish come acceleratore di web-caching per Adobe Commerce.

{{varnish-config-cloud}}

## Spurgatura vernice

Secondo la [documentazione di Varnish](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;Una *eliminazione* è ciò che accade quando si preleva un oggetto dalla cache e lo si elimina insieme alle relative varianti&quot;. Un&#39;eliminazione di vernice è simile a un comando di pulizia della cache (o a un clic su **Svuota cache di Magento** nell&#39;amministratore).

In effetti, quando si pulisce, svuota o aggiorna la cache di Commerce, anche la vernice si svuota.

Dopo aver installato e configurato Vernice per funzionare con Commerce, le seguenti azioni possono causare un&#39;eliminazione di vernice:

- Gestione di un sito Web.

  Ad esempio, tutte le operazioni eseguite nell’amministratore in:

   - **ARCHIVI** > **Impostazioni** > **Configurazione** > GENERALE > **Generale**
   - **ARCHIVI** > **Impostazioni** > **Configurazione** > GENERALE > **Impostazione valuta**
   - **ARCHIVI** > **Impostazioni** > **Configurazione** > GENERALE > **Indirizzi e-mail archivio**

  Quando Commerce rileva tale modifica, viene visualizzato un messaggio che ti informa di aggiornare la cache.

- Gestione di un negozio (ad esempio, aggiunta o modifica di categorie, prezzi, prodotti e regole di prezzo promozionali).

  La vernice viene eliminata automaticamente quando si esegue una di queste operazioni.

- Gestione del codice sorgente.

  È necessario aggiornare la cache ed eliminare periodicamente tutti gli elementi nelle directory `generated/code` e `generated/metadata`. Per informazioni sull’aggiornamento della cache, consulta la sezione successiva.

## Configura Commerce per eliminare la vernice

Commerce elimina gli host Varnish dopo aver configurato gli host Varnish utilizzando il comando [`magento setup:config:set`](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#setupconfigset).

È possibile utilizzare il parametro facoltativo `--http-cache-hosts` per specificare un elenco separato da virgole di host e porte di ascolto di Microsoft. Configurare tutti gli host Vernice, indipendentemente dal fatto che ne siano presenti uno o più. (Non separare gli host con uno spazio).

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

È quindi possibile eliminare gli host Varnish quando si aggiorna la cache di Commerce (detta anche *pulizia* della cache) nell&#39;Admin o utilizzando la riga di comando.

Per aggiornare la cache utilizzando l&#39;amministratore, fare clic su **[!UICONTROL SYSTEM]** > Strumenti > **Gestione cache**, quindi fare clic su **Svuota cache Magento** nella parte superiore della pagina. (Puoi anche aggiornare singoli tipi di cache).

Per aggiornare la cache utilizzando la riga di comando, in genere si utilizza il comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) come [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
