---
title: Best practice per risolvere i problemi di prestazioni del database
description: Scopri come risolvere i problemi di database che rallentano le prestazioni sui siti Adobe Commerce implementati nell’infrastruttura cloud.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Best practice per risolvere i problemi di prestazioni del database

Questo articolo illustra come risolvere i problemi del database che influiscono negativamente sulle prestazioni del database in Adobe Commerce sui siti dell’infrastruttura cloud.

## Versioni interessate

Adobe Commerce sull’infrastruttura cloud

## Identificare e risolvere query con tempi di esecuzione lunghi

Determinare se l&#39;esecuzione delle query MySQL è lenta. A seconda del piano Adobe Commerce per l’infrastruttura cloud e quindi della disponibilità degli strumenti, puoi effettuare le seguenti operazioni.

### Analizzare le query del database con MySQL

È possibile utilizzare MySQL per identificare e risolvere query con tempi di esecuzione lunghi su qualsiasi progetto di infrastruttura cloud di Adobe Commerce.

1. Esegui il [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) dichiarazione.
1. Se vengono visualizzate query con tempi di esecuzione lunghi, esegui [MySQL `EXPLAIN` e `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) per ciascuno di essi, per scoprire cosa fa eseguire la query per un lungo periodo di tempo.
1. In base ai problemi rilevati, procedi alla correzione della query in modo che venga eseguita più rapidamente.

### Analizzare le query utilizzando Percona Toolkit (solo per l&#39;architettura Pro)

Se il progetto Adobe Commerce è implementato su un’architettura Pro, puoi utilizzare Percona Toolkit per analizzare le query.

1. Esegui il `pt-query-digest --type=slowlog` comando rispetto ai log delle query lente di MySQL.
   * Per individuare la posizione dei registri di query lente, consulta **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) nella documentazione per gli sviluppatori.
   * Consulta la [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) documentazione.
1. In base ai problemi rilevati, procedi alla correzione della query in modo che venga eseguita più rapidamente.

## Verifica che tutte le tabelle abbiano una chiave primaria

La definizione delle chiavi primarie è un requisito per una corretta progettazione del database e della tabella. Le chiavi primarie consentono di identificare in modo univoco una singola riga in qualsiasi tabella.

Se sono presenti tabelle senza una chiave primaria, il modulo di gestione di database predefinito per Adobe Commerce (InnoDB) utilizza come chiave primaria la prima chiave univoca non null. Se non è disponibile alcuna chiave univoca, InnoDB crea una chiave primaria nascosta (6 byte). Il problema relativo a una chiave primaria definita in modo implicito è che non è possibile controllarla. Inoltre, il valore implicito viene assegnato a livello globale per tutte le tabelle senza chiavi primarie. Questa configurazione può causare problemi di conflitto se si eseguono scritture simultanee su queste tabelle. Ciò potrebbe causare problemi di prestazioni perché le tabelle condividono anche l&#39;incremento globale dell&#39;indice della chiave primaria nascosta.

Per evitare questi problemi, definisci una chiave primaria per le tabelle che non ne hanno una.

### Identificare e aggiornare le tabelle senza una chiave primaria

1. Identificare le tabelle senza una chiave primaria utilizzando la seguente query SQL:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Per qualsiasi tabella senza una chiave primaria, aggiungi una chiave primaria aggiornando il `db_schema.xml` (schema dichiarativo) con un nodo simile al seguente:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Quando aggiungi il nodo, sostituisci il `referenceID` e `column name` variabili con valori personalizzati.

Per ulteriori informazioni, consulta [Configura schema dichiarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) nella documentazione per gli sviluppatori.

## Identificare e rimuovere gli indici duplicati

Identifica eventuali indici duplicati nel database e rimuovili.

### Verifica la presenza di indici duplicati

Per verificare la presenza di indici duplicati nell&#39;architettura cloud Pro o Starter, eseguire la seguente query SQL.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

La query restituisce i nomi delle colonne e i nomi di eventuali indici duplicati.

I commercianti dell&#39;architettura Pro possono anche eseguire il controllo utilizzando Percona Toolkit  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` comando.

### Rimuovere gli indici duplicati

Utilizzare il linguaggio SQL [Istruzione DROP INDEX](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) per rimuovere gli indici duplicati.

```SQL
DROP INDEX
```

## Informazioni aggiuntive

[Best practice per la configurazione del database per le distribuzioni cloud](../planning/database-on-cloud.md)
