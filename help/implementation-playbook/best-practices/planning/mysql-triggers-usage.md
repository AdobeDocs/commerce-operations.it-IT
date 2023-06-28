---
title: Utilizzo trigger MySQL
description: Scopri come utilizzare i trigger MySQL in modo efficace con Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: acac3e47-67c8-4eea-80e3-e26f2854391a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Best practice per l’utilizzo dei trigger MySQL

Questo articolo spiega come evitare problemi di prestazioni quando si utilizzano i trigger MySQL. Gli attivatori vengono utilizzati per registrare le modifiche nelle tabelle di controllo.

## Prodotti e versioni interessati

- Adobe Commerce on-premise
- Adobe Commerce sull’infrastruttura cloud

>[!WARNING]
>
>Per i progetti Adobe Commerce su cloud, verifica sempre le modifiche alla configurazione nell’ambiente di staging prima di modificare la configurazione per l’ambiente di produzione.

## Comprendere l’impatto sulle prestazioni

I trigger vengono interpretati come codice, il che significa che MySQL non li precompila.

Collegandosi allo spazio delle transazioni della query, i trigger aggiungono un sovraccarico a un parser e a un interprete per ogni query eseguita con la tabella. I trigger condividono lo stesso spazio di transazione delle query originali e, mentre tali query competono per i blocchi della tabella, i trigger competono in modo indipendente per i blocchi di un&#39;altra tabella.

Questo sovraccarico aggiuntivo può influire negativamente sulle prestazioni del sito se vengono utilizzati molti trigger.

>[!WARNING]
>
>Adobe Commerce non supporta i trigger personalizzati nel database di Adobe Commerce, in quanto possono introdurre incompatibilità con le versioni future di Adobe Commerce. Per le best practice, consulta [Linee guida generali MySQL](../../../installation/prerequisites/database/mysql.md) nella documentazione di Adobe Commerce.

## Utilizzare i trigger in modo efficace

Per evitare problemi di prestazioni quando si utilizzano i trigger, attenersi alle seguenti linee guida:

- Se disponi di trigger personalizzati che scrivono alcuni dati quando il trigger viene eseguito, sposta questa logica per scrivere direttamente nelle tabelle di controllo. Ad esempio, aggiungendo una query aggiuntiva nel codice dell’applicazione, dopo la query per la quale intendi creare il trigger.
- Rivedi i trigger personalizzati esistenti e prendi in considerazione la loro rimozione e la scrittura diretta nelle tabelle dal lato dell’applicazione. Verifica la presenza di trigger esistenti nel database utilizzando [`SHOW TRIGGERS` Istruzione SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Per ulteriore assistenza, domande o dubbi, [invia un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Informazioni aggiuntive

- [Prerequisiti MySQL](../../../installation/prerequisites/database/mysql.md)
- [Best practice per il database di Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)
