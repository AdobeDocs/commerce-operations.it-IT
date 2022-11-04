---
title: Procedure consigliate per configurare la connessione slave MySQL
description: Scopri come configurare la connessione slave MySQL per i siti Adobe Commerce distribuiti sull’infrastruttura cloud.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Procedure consigliate per configurare la connessione slave MySQL

Per i siti Adobe Commerce distribuiti sull&#39;architettura cloud Infrastructure Pro, Adobe consiglia di abilitare la connessione slave MYSQL per il database per impostazione predefinita.

Adobe Commerce è in grado di leggere più database in modo asincrono.  Quando si abilita la connessione slave MYSQL, Adobe Commerce utilizza una connessione di sola lettura al database per ricevere il traffico di sola lettura su un nodo non master. Ciò migliora le prestazioni grazie al bilanciamento del carico, perché solo un nodo deve gestire il traffico di lettura-scrittura.

## Versioni interessate

Adobe Commerce su infrastruttura cloud, architettura Pro

## Configurare la connessione slave MySQL

La configurazione per la connessione slave MYSQL è impostata dal [MYSQL_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) distribuire la variabile nel file di configurazione dell’ambiente dell’infrastruttura cloud di Adobe Commerce, `.magento.env.yaml`. Imposta questa variabile su `true` per abilitare la connessione.

Per abilitare la connessione slave MySQL:

1. Modifica il `.magento.env.yaml` e verifica che `MYSQL_USE_SLAVE_CONNECTION` è abilitato.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Conferma le modifiche, quindi inviale al ramo dell’ambiente per distribuire l’aggiornamento.

   Al termine della distribuzione, la connessione slave MySQL viene abilitata nell&#39;infrastruttura cloud.

## Informazioni aggiuntive

- [Variabili di ambiente](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [Collo di bottiglia a carico elevato di MySQL in Adobe Commerce su infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Best practice per il database per Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)

>!![NOTE]
Siamo consapevoli che questo articolo può ancora contenere termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato o non benvenuto. Adobe sta lavorando per rimuovere questi termini dal codice, dalla documentazione e dalle esperienze utente.
