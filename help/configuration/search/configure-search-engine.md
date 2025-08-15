---
title: Configurazione del motore di ricerca
description: Configura un motore di ricerca per le distribuzioni locali di Adobe Commerce.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Configurazione del motore di ricerca

Questa sezione descrive le impostazioni minime che è necessario scegliere per testare Elasticsearch o OpenSearch con le distribuzioni locali di Adobe Commerce.

>[!TIP]
>
>Nelle versioni 2.4.4 e 2.4.3-p2, tutti i campi con etichetta **Elasticsearch** si applicano anche a OpenSearch.
>&#x200B;>Quando è stato introdotto il supporto per Elasticsearch 8.x nella versione 2.4.6, sono state create nuove etichette per distinguere tra le configurazioni di Elasticsearch e OpenSearch.

Per ulteriori dettagli sulla configurazione del motore di ricerca, consulta la [Guida utente](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html?lang=it).

## Configurare il motore di ricerca dall’amministratore

>[!TIP]
>
>Per istruzioni sull&#39;aggiornamento a una nuova versione del motore di ricerca, vedere [prerequisiti di aggiornamento](../../upgrade/prepare/prerequisites.md).

Per configurare il sistema per l&#39;utilizzo di Elasticsearch o OpenSearch:

1. Accedi all’amministratore come amministratore.
1. Fare clic su **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Dall&#39;elenco **[!UICONTROL Search Engine]**, selezionare la versione corrispondente del motore di ricerca.

   Nella tabella seguente sono elencate le opzioni necessarie per configurare e testare la connessione con Commerce. A meno che non siano state modificate le impostazioni del server del motore di ricerca, le impostazioni predefinite dovrebbero funzionare. Passa al passaggio successivo.

   | Opzione | Descrizione |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Immettere il nome host completo o l&#39;indirizzo IP del computer che esegue Elasticsearch o OpenSearch.<br>Adobe Commerce sull&#39;infrastruttura cloud: ottieni questo valore dal tuo sistema di integrazione. |
   | **[!UICONTROL Server Port]** | Immettere la porta proxy del server Web. Il valore predefinito è 9200<br>Adobe Commerce sull&#39;infrastruttura cloud: ottieni questo valore dal sistema di integrazione. |
   | **[!UICONTROL Index Prefix]** | Immetti il prefisso dell’indice del motore di ricerca. Se si utilizza una singola istanza per più installazioni di Commerce (ambienti di staging e produzione), è necessario specificare un prefisso univoco per ogni installazione. In caso contrario, è possibile utilizzare il prefisso predefinito magento2. |
   | **[!UICONTROL Enable HTTP Auth]** | Fare clic su **[!UICONTROL Yes]** solo se è stata abilitata l&#39;autenticazione per il server del motore di ricerca. In tal caso, fornisci un nome utente e una password nei campi forniti. |
   | **[!UICONTROL Server Timeout]** | Immetti il tempo di attesa (in secondi) durante il tentativo di stabilire una connessione al server Elasticsearch o OpenSearch. |

1. Fare clic su **[!UICONTROL Test Connection]**.

   Risposta di esempio:

   ![operazione completata](../../assets/configuration/elastic_test-success.png)

   Continua con:

   - [Configurare Apache per il motore di ricerca](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Configurare nginx per il motore di ricerca](../../installation/prerequisites/search-engine/configure-nginx.md)

   oppure vedi:

   ![non riuscito](../../assets/configuration/elastic_test-fail.png)

In tal caso, provare a effettuare le seguenti operazioni:

- Verificare che il server del motore di ricerca sia in esecuzione.
- Se il server si trova su un host diverso da Commerce, accedere al server Commerce ed eseguire il ping dell&#39;host del motore di ricerca. Risolvi i problemi di connettività di rete e verifica di nuovo la connessione.
- Esaminare la finestra di comando in cui è stato avviato Elasticsearch o OpenSearch per individuare tracce ed eccezioni dello stack. È necessario risolverli prima di continuare. In particolare, assicurati di aver avviato il motore di ricerca come utente con privilegi di `root`.
- Assicurati che [UNIX firewall e SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) siano entrambi disabilitati oppure imposta le regole per consentire al motore di ricerca e a Commerce di comunicare tra loro.
- Verificare il valore del campo **[!UICONTROL Server Hostname]**. Verificare che il server sia disponibile. È possibile provare l&#39;indirizzo IP del server.
- Utilizzare il comando `netstat -an | grep <listen-port>` per verificare che la porta specificata nel campo **[!UICONTROL Server Port]** non sia utilizzata da un altro processo.

  Ad esempio, per verificare se il motore di ricerca è in esecuzione sulla porta predefinita, utilizzare il comando seguente:

  ```bash
  netstat -an | grep 9200
  ```

  Se è in esecuzione sulla porta 9200, viene visualizzato come segue:

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## Reindicizza la ricerca nel catalogo e aggiorna la cache dell’intera pagina

Dopo aver modificato la configurazione del motore di ricerca, è necessario reindicizzare l’indice di ricerca del catalogo e aggiornare la cache dell’intera pagina utilizzando la riga di comando o di amministrazione.

Per aggiornare la cache utilizzando l’Admin:

1. In Amministrazione, fare clic su **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Selezionare la casella di controllo accanto a **[!UICONTROL Page Cache]**.
1. Nell&#39;elenco **[!UICONTROL Actions]** in alto a destra, fare clic su **Aggiorna**.

   ![gestione cache](../../assets/configuration/refresh-cache.png)

Per pulire la cache utilizzando la riga di comando: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Per reindicizzare utilizzando la riga di comando:

1. Accedi al server Commerce come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.
1. Immettete uno dei seguenti comandi:

   Immetti il seguente comando per reindicizzare solo l’indice di ricerca del catalogo:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Immetti il comando seguente per reindicizzare tutti gli indicizzatori:

   ```bash
   bin/magento indexer:reindex
   ```

1. Attendere il completamento della reindicizzazione.

   >[!INFO]
   >
   >A differenza della cache, gli indicizzatori vengono aggiornati da un processo cron. Prima di iniziare a utilizzare il motore di ricerca, assicurati che [cron sia abilitato](../cli/configure-cron-jobs.md).
