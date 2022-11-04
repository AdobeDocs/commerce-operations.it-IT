---
title: Utilizzo di MySQL trigger
description: Scopri come utilizzare i trigger MySQL in modo efficace con Adobe Commerce.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 79a825a094a80892cf1a30aa7f5c61bd351c69f5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per l&#39;utilizzo degli attivatori MySQL

Questo articolo spiega come evitare problemi di prestazioni quando si utilizzano attivatori MySQL. I trigger vengono utilizzati per registrare le modifiche nelle tabelle di controllo.

## Prodotti e versioni interessati

- Adobe Commerce on-premise
- Adobe Commerce su infrastruttura cloud

>[!WARNING]
>
>Per Adobe Commerce sui progetti cloud, verifica sempre le modifiche di configurazione nell’ambiente di staging prima di modificare la configurazione per l’ambiente di produzione.

## Comprendere l’impatto sulle prestazioni

I trigger vengono interpretati come codice il che significa che MySQL non li precompila.

Aggancia lo spazio di transazione della query, i trigger aggiungono il sovraccarico a un parser e a un interprete per ogni query eseguita con la tabella. I trigger condividono lo stesso spazio di transazione delle query originali e, mentre tali query sono in concorrenza per i blocchi nella tabella, i trigger competono in modo indipendente per i blocchi in un’altra tabella.

Questo sovraccarico aggiuntivo può influire negativamente sulle prestazioni del sito se vengono utilizzati molti trigger.

>[!WARNING]
>
>Adobe Commerce non supporta attivatori personalizzati nel database Adobe Commerce perché i trigger personalizzati possono introdurre incompatibilità con le versioni future di Adobe Commerce. Per le best practice, consulta [Linee guida generali MySQL](../../../installation/prerequisites/database/mysql.md) nella documentazione di Adobe Commerce.

## Utilizzare i trigger in modo efficace

Per evitare problemi di prestazioni quando si utilizzano i trigger, segui queste linee guida:

- Se sono presenti trigger personalizzati che scrivono alcuni dati quando viene eseguito l’attivatore, sposta questa logica per scrivere direttamente nelle tabelle di controllo. Ad esempio, aggiungendo una query aggiuntiva nel codice dell’applicazione, dopo la query per la quale si intendeva creare il trigger.
- Esamina i trigger personalizzati esistenti e considera la possibilità di rimuoverli e scriverli direttamente nelle tabelle dal lato dell’applicazione. Verifica la presenza di attivatori esistenti nel database utilizzando [`SHOW TRIGGERS` Istruzione SQL](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Per ulteriori informazioni, domande o dubbi, [inviare un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?#submit-ticket).

## Informazioni aggiuntive

- [Prerequisiti di MySQL](../../../installation/prerequisites/database/mysql.md)
- [Best practice per il database per Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)
