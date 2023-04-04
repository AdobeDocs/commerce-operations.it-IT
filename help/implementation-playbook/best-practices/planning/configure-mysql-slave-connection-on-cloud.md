---
title: Procedure consigliate per configurare la connessione slave MySQL
description: Scopri come configurare la connessione slave MySQL per i siti Adobe Commerce distribuiti sull’infrastruttura cloud.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Procedure consigliate per configurare la connessione slave MySQL

>[!NOTE]
>
>Questo articolo contiene termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato o non benvenuto. Adobe sta lavorando per rimuovere questi termini dal codice, dalla documentazione e dalle esperienze utente.

Per i siti Adobe Commerce distribuiti sull&#39;architettura cloud Infrastructure Pro, Adobe consiglia di abilitare la connessione slave MYSQL per il database per impostazione predefinita.

Adobe Commerce è in grado di leggere più database in modo asincrono. Quando si abilita la connessione slave MYSQL, Adobe Commerce utilizza una connessione di sola lettura al database per ricevere il traffico di sola lettura su un nodo non master. Le prestazioni migliorano grazie al bilanciamento del carico quando un solo nodo gestisce il traffico di lettura-scrittura.

## Versioni interessate

Adobe Commerce su infrastruttura cloud, architettura Pro

## Configurare la connessione slave MySQL

In Adobe Commerce sull&#39;infrastruttura cloud, è possibile ignorare la configurazione predefinita per la connessione slave MYSQL impostando il [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabile. Imposta questa variabile su true per utilizzare automaticamente una connessione di sola lettura al database.

**Per abilitare la connessione slave MySQL**:

1. Nella workstation locale, passa alla directory del progetto.

1. In `.magento.env.yaml` imposta il `MYSQL_USE_SLAVE_CONNECTION` su true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Conferma `.magento.env.yaml` modifiche ai file e invio push all&#39;ambiente remoto.

   Al termine della distribuzione, la connessione slave MySQL viene abilitata per l&#39;ambiente cloud.

Scopri di più sulla personalizzazione dell’ambiente cloud ignorando la configurazione Commerce esistente con [Variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) in _Guida all’infrastruttura cloud di Adobe Commerce_.

## Informazioni aggiuntive

- [Collo di bottiglia a carico elevato di MySQL in Adobe Commerce su infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Best practice per il database per Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)
