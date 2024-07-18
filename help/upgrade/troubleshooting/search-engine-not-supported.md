---
title: Motore di ricerca corrente non supportato
description: Risolvi i problemi relativi all’aggiornamento di Adobe Commerce dopo aver riscontrato un errore relativo a un motore di ricerca non supportato.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Motore di ricerca corrente non supportato

Il seguente messaggio di errore indica che la versione di Adobe Commerce da cui stai eseguendo l’aggiornamento è configurata per l’utilizzo di un motore di ricerca catalogo non supportato nella versione a cui stai effettuando l’aggiornamento:

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Questo errore indica che una delle seguenti condizioni è vera nella versione di livello inferiore di Adobe Commerce:

- Il motore di ricerca è impostato su MySQL.
- Il motore di ricerca è impostato su una versione di Elasticsearch non più supportata.

Utilizza il seguente comando per controllare il motore di ricerca corrente:

```bash
bin/magento config:show catalog/search/engine
```

L&#39;errore si verifica se il valore restituito è `mysql`, `elasticsearch` o `elasticsearch6`.

>[!WARNING]
>
>Se hai ricevuto questo errore, l&#39;installazione è in uno stato incoerente e non puoi accedere all&#39;amministratore. Mentre risolvi questo errore, ti consigliamo di ripristinare la versione precedente. A tale scopo, eseguire uno dei comandi seguenti:
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Dove `<version>` è la versione del Magento in cui si stava eseguendo **prima** dell&#39;aggiornamento. Ad esempio, `2.3.5`.

Seguire le linee guida descritte nelle sezioni seguenti per eseguire il ripristino da uno stato incoerente.

## Se il motore di ricerca è `mysql`

Prima della versione 2.4, MySQL era il motore di ricerca del catalogo predefinito, ma MySQL non è più supportato in questa capacità. Ora è necessario installare e configurare Elasticsearch o OpenSearch come motore di ricerca prima di eseguire l’aggiornamento alla versione 2.4.

Utilizza le risorse seguenti per aiutarti a seguire questo processo:

- [Installare e configurare il motore di ricerca](../../configuration/search/overview-search.md)
- [Configurazione del motore di ricerca](../../configuration/search/configure-search-engine.md)

Dopo aver configurato il motore di ricerca e la reindicizzazione, sei pronto per l’aggiornamento alla versione 2.4.

## Se il motore di ricerca è `elasticsearch`

Elasticsearch 6 e versioni precedenti non sono più supportati.

Il valore `elasticsearch` indica che la versione di Adobe Commerce di livello inferiore è configurata per l&#39;utilizzo di Elasticsearch 2.x. Questa versione di Elasticsearch non è più supportata.

Prima di eseguire l’aggiornamento a 2.4, è necessario eseguire le seguenti attività:

1. Aggiornamento a una versione di Elasticsearch supportata da Commerce. Consulta l&#39;[Elasticsearch sull&#39;aggiornamento](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) per istruzioni complete sul backup dei dati, l&#39;individuazione di potenziali problemi di migrazione e il test degli aggiornamenti prima della distribuzione in produzione. A seconda della versione corrente dell&#39;Elasticsearch, potrebbe essere necessario o meno un riavvio completo del cluster.

   >[!NOTE]
   >
   >Elasticsearch richiede JDK 1.8 o versione successiva. Consulta [Installare Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) per verificare quale versione di JDK è installata.

1. [Configurare Elasticsearch](../../configuration/search/configure-search-engine.md) e reindicizzare.

Dopo aver configurato il motore di ricerca e la reindicizzazione, sei pronto per l’aggiornamento alla versione 2.4.
