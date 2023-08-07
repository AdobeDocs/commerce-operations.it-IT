---
title: Procedure consigliate per configurare la connessione slave MySQL
description: Scopri come configurare la connessione slave MySQL per i siti Adobe Commerce distribuiti nell’infrastruttura cloud.
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 3532480e2172c39ceb4ec55c9819d5271fd1fcdb
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Procedure consigliate per configurare la connessione slave MySQL

>[!NOTE]
>
>Questo articolo contiene termini software standard del settore che alcuni possono trovare razzisti, sessisti o oppressivi e che possono far sentire il lettore ferito, traumatizzato o non gradito. Adobe sta lavorando per rimuovere questi termini dal codice, dalla documentazione e dalle esperienze utente.

Adobe Commerce può leggere più database in modo asincrono. Se prevedi un carico elevato per il database MySQL di un sito Commerce distribuito sull’architettura Pro dell’infrastruttura cloud, l’Adobe consiglia di abilitare la connessione slave MYSQL.

Quando si abilita la connessione slave MYSQL, Adobe Commerce utilizza una connessione di sola lettura al database per ricevere traffico di sola lettura su un nodo non principale. Le prestazioni migliorano grazie al bilanciamento del carico quando un solo nodo gestisce il traffico in lettura-scrittura.

## Versioni interessate

Adobe Commerce su infrastruttura cloud, solo architettura Pro

## Configura connessione slave MySQL

Nell’infrastruttura cloud di Adobe Commerce on, puoi sovrascrivere la configurazione predefinita per la connessione slave MYSQL impostando il [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variabile. Imposta questa variabile su `true` per utilizzare automaticamente una connessione di sola lettura al database.

**Per attivare la connessione slave MySQL**:

1. Sulla workstation locale, passa alla directory del progetto.

1. In `.magento.env.yaml` file, imposta `MYSQL_USE_SLAVE_CONNECTION` su true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Eseguire il commit di `.magento.env.yaml` modifiche ai file e invio all&#39;ambiente remoto.

   Al termine della distribuzione, la connessione slave MySQL viene abilitata per l&#39;ambiente cloud.

## Informazioni aggiuntive

Ulteriori informazioni sulla personalizzazione dell’ambiente cloud tramite l’override della configurazione Commerce esistente con [Variabili di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) nel _Guida di Adobe Commerce sull’infrastruttura cloud_.

Consulta la [Collo di bottiglia di MySQL ad alto carico in Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html) articolo nel _Knowledge Base di supporto_.
