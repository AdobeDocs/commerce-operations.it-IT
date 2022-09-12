---
title: Motore di ricerca corrente non supportato
description: Risolvere i problemi relativi all’aggiornamento di Adobe Commerce o Magento Open Source dopo un errore relativo a un motore di ricerca non supportato.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# Motore di ricerca corrente non supportato

Il seguente messaggio di errore indica che la versione di Adobe Commerce o Magento Open Source da cui si esegue l’aggiornamento è configurata per l’utilizzo di un motore di ricerca del catalogo non supportato nella versione in cui si esegue l’aggiornamento:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Questo errore significa che una delle seguenti condizioni è vera sulla versione di livello inferiore di Adobe Commerce o del Magento Open Source:

- Il motore di ricerca è impostato su MySQL.
- Il motore di ricerca è impostato su una versione di Elasticsearch non più supportata.

Utilizzare il comando seguente per controllare il motore di ricerca corrente:

```bash
bin/magento config:show catalog/search/engine
```

L&#39;errore si verifica se il valore restituito è `mysql` o `elasticsearch`.

>[!WARNING]
>
>Se hai ricevuto questo errore, l&#39;installazione è in uno stato incoerente e non puoi accedere all&#39;amministratore. È consigliabile ripristinare la versione precedente durante la risoluzione dell’errore. A questo scopo, esegui uno dei seguenti comandi:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Dove `<version>` è la versione del Magento in esecuzione **prima** l&#39;aggiornamento. Ad esempio, `2.3.5`.

Seguire le linee guida descritte nelle sezioni seguenti per eseguire il ripristino da uno stato incoerente.

## Se il motore di ricerca è `mysql`

Prima della versione 2.4, MySQL era il motore di ricerca del catalogo predefinito, ma MySQL non è più supportato in questa capacità. Ora è necessario installare e configurare Elasticsearch o OpenSearch come motore di ricerca prima di eseguire l’aggiornamento alla versione 2.4.

Utilizza le risorse seguenti per guidarti in questo processo:

- [Installare e configurare Elasticsearch](../../configuration/search/overview-search.md)
- [Installazione di Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Configurare Elasticsearch con cui lavorare [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) o [Apache](../../installation/prerequisites/search-engine/configure-apache.md)
- [Configura Elasticsearch](../../configuration/search/configure-search-engine.md)

Dopo aver configurato il motore di ricerca e reindicizzato, è possibile effettuare l&#39;aggiornamento alla versione 2.4.

## Se il motore di ricerca è `elasticsearch`

Un valore di `elasticsearch` indica che la versione di Adobe Commerce o Magenti Open Source di livello inferiore è configurata per l’utilizzo di Elasticsearch 2.x. Questa versione di Elasticsearch non è più supportata.

Prima di eseguire l&#39;aggiornamento alla versione 2.4, è necessario eseguire le seguenti operazioni:

1. Aggiornamento a una versione di Elasticsearch supportata da Commerce. Fai riferimento a [Aggiornamento dell’Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) per istruzioni complete su come eseguire il backup dei dati, rilevare potenziali problemi di migrazione e testare gli aggiornamenti prima dell’implementazione in produzione. A seconda della versione corrente dell&#39;Elasticsearch, potrebbe essere necessario o meno un riavvio completo del cluster.

   >[!NOTE]
   >
   >Elasticsearch richiede JDK 1.8 o versione successiva. Vedi [Installare il Java Software Development Kit (JDK)](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) per verificare quale versione di JDK è installata.

1. [Configura Elasticsearch](../../configuration/search/configure-search-engine.md) e reindicizzare.

Dopo aver configurato il motore di ricerca e reindicizzato, è possibile effettuare l&#39;aggiornamento alla versione 2.4.
