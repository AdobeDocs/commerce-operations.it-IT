---
title: Configurazione del motore di ricerca
description: Configura un motore di ricerca con Adobe Commerce e Magenti Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---


# Configurazione del motore di ricerca

Questa sezione illustra le impostazioni minime che è necessario scegliere per testare Elasticsearch o OpenSearch con Adobe Commerce e Magento Open Source. A partire dalle versioni 2.4.4 e 2.4.3-p2, tutti i campi etichettati **Elasticsearch** si applica anche a OpenSearch.

Per ulteriori dettagli sulla configurazione del motore di ricerca, consulta la sezione [Guida utente](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html).

## Configura il motore di ricerca dall’amministratore

Per configurare il sistema per l&#39;utilizzo di Elasticsearch o OpenSearch:

1. Accedi all’amministratore come amministratore.
1. Fai clic su **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Catalogo** > **Ricerca nel catalogo**.
1. Da **Motore di ricerca** selezionare la versione corrispondente del motore di ricerca Se si utilizza OpenSearch, è necessario selezionare Elasticsearch7.

   Nella tabella seguente sono elencate le opzioni di configurazione necessarie per configurare e verificare la connessione con Commerce.
A meno che non siano state modificate le impostazioni del server del motore di ricerca, le impostazioni predefinite funzioneranno. Passa al passaggio successivo.

   | Opzione | Descrizione |
   |--- |--- |
   | **Nome host del server Elasticsearch** | Immettere il nome host completo o l&#39;indirizzo IP del computer che esegue Elasticsearch o OpenSearch.<br>Adobe Commerce sull’infrastruttura cloud: Ottieni questo valore dal tuo sistema di integrazione. |
   | **Porta server Elasticsearch** | Immettere la porta proxy del server Web. Il valore predefinito è 9200<br>Adobe Commerce sull’infrastruttura cloud: Ottieni questo valore dal tuo sistema di integrazione. |
   | **Prefisso indice Elasticsearch** | Immettere il prefisso dell&#39;indice del motore di ricerca. Se utilizzi una singola istanza per più di un’installazione Commerce (ambienti di staging e produzione), devi specificare un prefisso univoco per ogni installazione. In caso contrario, è possibile utilizzare il prefisso predefinito magento2. |
   | **Abilita autenticazione HTTP Elasticsearch** | Fai clic su **Sì** solo se hai abilitato l’autenticazione per il server del motore di ricerca. In tal caso, fornisci un nome utente e una password nei campi forniti. |

1. Fai clic su **Prova connessione**.

   Risposta di esempio:

   ![success](../../assets/configuration/elastic_test-success.png)

   Continua con:

   - [Configurare Apache per il motore di ricerca](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Configurare l’allegato per il motore di ricerca](../../installation/prerequisites/search-engine/configure-nginx.md)

   o vedi:

   ![fallito](../../assets/configuration/elastic_test-fail.png)

In tal caso, prova quanto segue:

- Assicurati che il server del motore di ricerca sia in esecuzione.
- Se il server si trova su un host diverso da Commerce, accedi al server Commerce ed effettua il ping dell’host del motore di ricerca. Risolvere i problemi di connettività di rete e testare nuovamente la connessione.
- Esaminare la finestra del comando in cui è stato avviato Elasticsearch o OpenSearch per individuare tracce ed eccezioni di stack. Prima di continuare, è necessario risolverli. In particolare, assicurati di aver avviato il motore di ricerca come utente con `root` privilegi.
- Assicurati che [Firewall UNIX e SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) sono entrambi disabilitati o impostano regole per consentire al motore di ricerca e a Commerce di comunicare tra loro.
- Verifica il valore del **Nome host del server Elasticsearch** campo . Assicurati che il server sia disponibile. È invece possibile provare l&#39;indirizzo IP del server.
- Utilizza la `netstat -an | grep <listen-port>` per verificare che la porta specificata nel **Porta server Elasticsearch** campo non utilizzato da un altro processo.

   Ad esempio, per verificare se il motore di ricerca è in esecuzione sulla porta predefinita, utilizzare il comando seguente:

   ```bash
   netstat -an | grep 9200
   ```

   Se è in esecuzione sulla porta 9200, viene visualizzato in modo simile al seguente:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Reindicizzazione della ricerca nel catalogo e aggiornamento della cache a pagina intera

Dopo aver modificato la configurazione del motore di ricerca, è necessario reindicizzare l&#39;indice di ricerca del catalogo e aggiornare la cache della pagina intera utilizzando l&#39;amministratore o la riga di comando.

Per aggiornare la cache utilizzando l’amministratore:

1. In Admin, fai clic su **Sistema** > **Gestione cache**.
1. Seleziona la casella di controllo accanto a **Cache pagina**.
1. Da **Azioni** elenco in alto a destra, fai clic su **Aggiorna**.

   ![gestione cache](../../assets/configuration/refresh-cache.png)

Per pulire la cache utilizzando la riga di comando: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Per reindicizzare utilizzando la riga di comando:

1. Accedi al tuo server Commerce come o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Immettere uno dei seguenti comandi:

   Immettere il comando seguente per reindicizzare solo l&#39;indice di ricerca del catalogo:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Immetti il seguente comando per reindicizzare tutti gli indici:

   ```bash
   bin/magento indexer:reindex
   ```

1. Attendi il completamento della reindicizzazione.

   >[!INFO]
   >
   >A differenza della cache, gli indici vengono aggiornati da un lavoro cron. Assicurati [cron abilitato](../cli/configure-cron-jobs.md) prima di iniziare a utilizzare il motore di ricerca.

