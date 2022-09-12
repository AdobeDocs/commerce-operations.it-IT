---
title: "[!DNL Data Migration Tool] prerequisiti"
description: "Scopri cosa devi fare prima di iniziare a utilizzare i [!DNL Data Migration Tool] trasferire i dati tra il Magento 1 e il Magento 2."
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# [!DNL Data Migration Tool] prerequisiti

Prima di avviare la migrazione, accertati che siano soddisfatti i seguenti requisiti.

## Magento 2

* Impostare il sistema di Magento 2 in modo che soddisfi i requisiti [requisiti di sistema](../../installation/system-requirements.md).

   Utilizzare una topologia e una progettazione che almeno corrispondano al sistema di Magento 1 esistente.

* [Installa Magento 2](../../installation/overview.md).

## Cron

Non avviare lavori di cron Magento 2.

## Database

* Dopo l&#39;installazione, eseguire il backup o [scaricare](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) il database di Magento 2 il prima possibile. In questo modo è possibile ripristinare lo stato iniziale del database se la migrazione non ha esito positivo.

* Verifica se [!DNL Data Migration Tool] dispone dell&#39;accesso alla rete per collegare i database di Magento 1 e Magento 2.

   Apri le porte nel firewall in modo che lo strumento di migrazione possa comunicare con i database.

* Assicurati che gli account MySQL dispongano di tutti i privilegi necessari per accedere ai database di Magento.

Se la funzione Registrazione binario è abilitata per il database di Magento 1, imposta la variabile globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) Variabile di sistema MySQL in `1`o concedere [Privilegio SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) al tuo account.

* Non consigliamo di creare nuove entità (prodotti, categorie e attributi) nell’archivio del Magento 2 prima della migrazione perché la variabile [!DNL Data Migration Tool] sovrascrive tali nuove entità con quelle vecchie del Magento 1.

## Estensioni

Esegui la migrazione del codice di estensione Magento 1 al Magento 2.

Per trovare le versioni più recenti delle estensioni, visita [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) o contatta il provider di estensioni.

È inoltre possibile utilizzare [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
