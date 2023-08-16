---
title: Cambia ID incremento
description: Modifica l’ID di incremento per un’entità di database Commerce.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Cambia ID incremento

Questo articolo illustra come modificare l’ID incremento per un’entità database di Commerce (DB) (ordine, fattura, nota di accredito e così via) in un particolare archivio Commerce utilizzando `ALTER TABLE` Istruzione SQL.

## Versioni interessate

- Adobe Commerce (locale): 2.x.x
- Adobe Commerce sull’infrastruttura cloud: 2.x.x
- MySQL: [qualsiasi versione supportata](../../installation/prerequisites/database/mysql.md)

## Quando modificare l&#39;ID incremento

Potrebbe essere necessario modificare l&#39;ID incremento per le nuove entità DB nei seguenti casi:

- Dopo il ripristino di un backup rigido su un sito live
- Alcuni record degli ordini sono stati persi, ma i loro ID sono già utilizzati dai gateway di pagamento (come PayPal) per il tuo account esercente corrente. In questo caso, i gateway di pagamento interrompono l&#39;elaborazione di nuovi ordini con gli stessi ID, restituendo l&#39;errore &quot;ID fattura duplicato&quot;

>[!INFO]
>
>Puoi anche risolvere il problema del gateway di pagamento per PayPal consentendo più pagamenti per ID fattura nelle Preferenze di ricezione pagamento di PayPal. Consulta [Richiesta rifiutata gateway PayPal - problema fattura duplicata] nel _Knowledge Base_.

## Passaggi preliminari

1. Trova archivi ed entità per i quali modificare il nuovo ID incremento.
1. Connettersi al database MySQL.
Per l’infrastruttura cloud di Adobe Commerce, all’inizio è necessario connettersi all’ambiente utilizzando SSH.
1. Controlla l&#39;attuale `auto_increment` valore per la tabella di sequenza di entità utilizzando la query seguente:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Se si sta controllando un incremento automatico per un ordine nel punto vendita con ID=1, il nome della tabella sarà &#39;sequence_order_1&#39;.

Se il valore di `auto_increment` è &#39;1234&#39;, il prossimo ordine effettuato presso il negozio con `ID=1` avrà l’ID &quot;#100001234&quot;.

## Aggiorna entità per modificare l&#39;ID incremento

Aggiorna l’entità utilizzando la seguente query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
Importante: il nuovo valore di incremento deve essere maggiore di quello corrente.

Dopo l’esecuzione della seguente query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

L’ordine successivo effettuato al negozio con `ID=1` avrà l’ID &quot;#100002000&quot;.

## Passaggi consigliati aggiuntivi per gli ambienti di produzione cloud

Prima di eseguire `ALTER TABLE` in un ambiente di produzione di Adobe Commerce su infrastruttura cloud, si consiglia vivamente di eseguire i seguenti passaggi:

- Test dell&#39;intera procedura di modifica dell&#39;ID di incremento nell&#39;ambiente di staging
- [Creare un backup del database] per ripristinare il database di produzione in caso di errore

<!-- Link Definitions -->

[Richiesta rifiutata gateway PayPal - problema fattura duplicata]: https://support.magento.com/hc/en-us/articles/115002457473
[Creare un backup del database]: https://support.magento.com/hc/en-us/articles/360003254334
[qualsiasi versione supportata]
