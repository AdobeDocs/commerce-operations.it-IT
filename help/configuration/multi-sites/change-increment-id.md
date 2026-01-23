---
title: Cambia ID incremento
description: Modificare l'ID di incremento per un'entità di database Commerce.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Cambia ID incremento

In questo articolo viene illustrato come modificare l&#39;ID incremento per un&#39;entità database (DB) di Commerce (ordine, fattura, nota di accredito e così via) in un particolare archivio Commerce utilizzando l&#39;istruzione SQL `ALTER TABLE`.

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
>Puoi anche risolvere il problema del gateway di pagamento per PayPal consentendo più pagamenti per ID fattura nelle Preferenze di ricezione pagamento di PayPal. Vedi [Richiesta rifiutata dal gateway PayPal - problema fattura duplicata](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) nella _Knowledge Base_.

## Passaggi preliminari

1. Trova archivi ed entità per i quali modificare il nuovo ID incremento.
1. Connettersi al database MySQL.
Per l’infrastruttura cloud di Adobe Commerce, all’inizio è necessario connettersi all’ambiente utilizzando SSH.
1. Controllare il valore `auto_increment` corrente per la tabella di sequenza delle entità utilizzando la query seguente:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Se si sta controllando un incremento automatico per un ordine nel punto vendita con ID=1, il nome della tabella sarà &#39;sequence_order_1&#39;.

Se il valore della colonna `auto_increment` è &#39;1234&#39;, l&#39;ordine successivo effettuato presso l&#39;archivio con `ID=1` avrà l&#39;ID &#39;#100001234&#39;.

## Aggiorna entità per modificare l&#39;ID incremento

Aggiorna l’entità utilizzando la seguente query:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>Importante: il nuovo valore di incremento deve essere maggiore di quello corrente.

Dopo l’esecuzione della seguente query:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

L&#39;ordine successivo effettuato con `ID=1` avrà l&#39;ID &#39;#100002000&#39;.

## Passaggi consigliati aggiuntivi per gli ambienti di produzione cloud

Prima di eseguire la query `ALTER TABLE` in un ambiente di produzione di Adobe Commerce su un&#39;infrastruttura cloud, si consiglia vivamente di eseguire i passaggi seguenti:

- Test dell&#39;intera procedura di modifica dell&#39;ID di incremento nell&#39;ambiente di staging
- [Crea un backup del database](https://support.magento.com/hc/en-us/articles/360003254334) per ripristinare il database di produzione in caso di errore

