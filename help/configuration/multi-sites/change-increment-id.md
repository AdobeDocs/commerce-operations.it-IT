---
title: Cambia ID incremento
description: Modificare l’ID incrementale per un’entità di database Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Cambia ID incremento

Questo articolo illustra come modificare l’ID incrementale per un’entità di database Commerce (DB) (ordine, fattura, nota di credito e così via) in un particolare archivio Commerce utilizzando `ALTER TABLE` Istruzione SQL.

## Versioni interessate

- Adobe Commerce (locale): 2.x.x
- Adobe Commerce sull’infrastruttura cloud: 2.x.x
- MySQL: [qualsiasi versione supportata](../../installation/prerequisites/database/mysql.md)

## Quando è necessario modificare l&#39;ID incrementale

Potrebbe essere necessario modificare l&#39;ID incrementale per le nuove entità DB in questi casi:

- Dopo un ripristino del backup su un sito Live
- Alcuni record d&#39;ordine sono stati persi, ma i loro ID sono già utilizzati dai gateway di pagamento (come PayPal) per il tuo attuale account Merchant. In questo caso, i gateway di pagamento smettono di elaborare nuovi ordini con gli stessi ID, restituendo l’errore &quot;ID fattura duplicato&quot;

>[!INFO]
>
>Puoi anche risolvere il problema del gateway dei pagamenti per PayPal consentendo più pagamenti per ID fattura nelle preferenze di pagamento di PayPal. Vedi [Richiesta rifiutata dal gateway PayPal - problema di fattura duplicato] in _Knowledge Base_.

## Passaggi preliminari

1. Trova negozi ed entità per i quali il nuovo ID incrementale deve essere modificato.
1. Connettersi al database MySQL.
Per Adobe Commerce sull’infrastruttura cloud, all’inizio è necessario connettersi all’ambiente utilizzando SSH.
1. Controlla la corrente `auto_increment` valore per la tabella di sequenza di entità utilizzando la seguente query:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Se controlli un incremento automatico per un ordine nell&#39;archivio con ID=1, il nome della tabella sarà &#39;sequence_order_1&#39;.

Se il valore di `auto_increment` è &#39;1234&#39;, l&#39;ordine successivo posto al negozio con `ID=1` avrà l’ID &quot;#100001234&quot;.

## Aggiorna entità per modificare l&#39;ID incrementale

Aggiorna l’entità utilizzando la seguente query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Importante: Il nuovo valore di incremento deve essere maggiore del valore corrente.

Dopo aver eseguito la seguente query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

L&#39;ordine successivo posto al negozio con `ID=1` avrà l’ID &quot;#100002000&quot;.

## Passaggi aggiuntivi consigliati per gli ambienti di produzione cloud

Prima di eseguire `ALTER TABLE` su un ambiente di produzione di Adobe Commerce su un’infrastruttura cloud, si consiglia vivamente di eseguire questi passaggi:

- Testa l&#39;intera procedura di modifica dell&#39;ID incrementale nell&#39;ambiente di staging
- [Creare un backup del database] per ripristinare il database di produzione in caso di errore

<!-- Link Definitions -->

[Richiesta rifiutata dal gateway PayPal - problema di fattura duplicato]: https://support.magento.com/hc/en-us/articles/115002457473
[Creare un backup del database]: https://support.magento.com/hc/en-us/articles/360003254334
[qualsiasi versione supportata]
