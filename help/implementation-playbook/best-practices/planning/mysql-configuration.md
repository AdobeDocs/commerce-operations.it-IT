---
title: Best practice di configurazione MySQL
description: Scopri in che modo i trigger MySQL e le connessioni slave influiscono sulle prestazioni del sito Commerce e come utilizzarle in modo efficace.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Best practice di configurazione MySQL

>[!NOTE]
>
>Questo argomento contiene termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato o non gradito. Adobe sta lavorando per rimuovere questi termini dal codice, dalla documentazione e dalle esperienze utente.

## Triggers

Questo articolo spiega come evitare problemi di prestazioni quando si utilizzano i trigger MySQL. Gli attivatori vengono utilizzati per registrare le modifiche nelle tabelle di controllo.

### Prodotti e versioni interessati

- Adobe Commerce on-premise
- Adobe Commerce sull’infrastruttura cloud

>[!WARNING]
>
>Per i progetti Adobe Commerce su cloud, verifica sempre le modifiche alla configurazione nell’ambiente di staging prima di modificare la configurazione per l’ambiente di produzione.

### Impatto sulle prestazioni

I trigger vengono interpretati come codice, il che significa che MySQL non li precompila.

Collegandosi allo spazio delle transazioni della query, i trigger aggiungono un sovraccarico a un parser e a un interprete per ogni query eseguita con la tabella. I trigger condividono lo stesso spazio di transazione delle query originali e, mentre tali query competono per i blocchi della tabella, i trigger competono in modo indipendente per i blocchi di un&#39;altra tabella.

Questo sovraccarico aggiuntivo può influire negativamente sulle prestazioni del sito se vengono utilizzati molti trigger.

>[!WARNING]
>
>Adobe Commerce non supporta i trigger personalizzati nel database di Adobe Commerce, in quanto possono introdurre incompatibilità con le versioni future di Adobe Commerce. Per le best practice, vedere [Linee guida generali per MySQL](../../../installation/prerequisites/database/mysql.md) nella documentazione di Adobe Commerce.

### Uso efficace

Per evitare problemi di prestazioni quando si utilizzano i trigger, attenersi alle seguenti linee guida:

- Se disponi di trigger personalizzati che scrivono alcuni dati quando il trigger viene eseguito, sposta questa logica per scrivere direttamente nelle tabelle di controllo. Ad esempio, aggiungendo una query aggiuntiva nel codice dell’applicazione, dopo la query per la quale intendi creare il trigger.
- Rivedi i trigger personalizzati esistenti e prendi in considerazione la loro rimozione e la scrittura diretta nelle tabelle dal lato dell’applicazione. Controllare i trigger esistenti nel database utilizzando l&#39;istruzione SQL [`SHOW TRIGGERS`](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Per ulteriore assistenza, domande o dubbi, [invia un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it&#submit-ticket).

## Connessioni slave

Adobe Commerce può leggere più database in modo asincrono. Se prevedi un carico elevato per il database MySQL di un sito Commerce distribuito sull’architettura Pro dell’infrastruttura cloud, l’Adobe consiglia di abilitare la connessione slave MYSQL.

Quando si abilita la connessione slave MYSQL, Adobe Commerce utilizza una connessione di sola lettura al database per ricevere traffico di sola lettura su un nodo non principale. Le prestazioni migliorano grazie al bilanciamento del carico quando un solo nodo gestisce il traffico in lettura-scrittura.

### Versioni interessate

Adobe Commerce su infrastruttura cloud, solo architettura Pro

### Configurazione

Nell&#39;infrastruttura cloud di Adobe Commerce è possibile ignorare la configurazione predefinita per la connessione slave MYSQL impostando la variabile [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#mysql_use_slave_connection). Impostare questa variabile su `true` per utilizzare automaticamente una connessione di sola lettura al database.

**Per abilitare la connessione slave MySQL**:

1. Sulla workstation locale, passa alla directory del progetto.

1. Nel file `.magento.env.yaml`, impostare `MYSQL_USE_SLAVE_CONNECTION` su true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Eseguire il commit delle modifiche al file `.magento.env.yaml` e inviare il messaggio push all&#39;ambiente remoto.

   Al termine della distribuzione, la connessione slave MySQL viene abilitata per l&#39;ambiente cloud.
