---
title: '[!DNL Data Migration Tool] prerequisiti'
description: Scopri cosa devi fare prima di iniziare a utilizzare il [!DNL Data Migration Tool] trasferire dati tra il Magento 1 e il Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] prerequisiti

Prima di avviare la migrazione, accertati che siano soddisfatti i seguenti requisiti.

## MAGENTO 2

* Configurare il Magento 2 in modo che soddisfi [requisiti di sistema](../../installation/system-requirements.md).

  Utilizza una topologia e una progettazione che corrispondano almeno al Magento 1 esistente.

* [Installa Magento 2](../../installation/overview.md).

## Cron

Non avviare lavori cron Magento 2.

## Database

* Dopo l&#39;installazione, eseguire il backup o [dump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) il database Magento 2 non appena possibile. Questo consente di ripristinare lo stato iniziale del database se la migrazione non ha esito positivo.

* Verifica se [!DNL Data Migration Tool] dispone dell&#39;accesso di rete per connettere i database del Magento 1 e del Magento 2.

  Aprire le porte del firewall in modo che lo strumento di migrazione possa comunicare con i database.

* Assicurarsi che gli account MySQL dispongano di tutti i privilegi necessari per accedere ai database di Magento.

Se la registrazione binaria è abilitata per il database del Magento 1, impostare la [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) Variabile di sistema MySQL su `1`, o concedono [PRIVILEGIO SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) sul tuo account.

* Si sconsiglia di creare nuove entità (prodotti, categorie e attributi) nell’archivio del Magento 2 prima della migrazione, perché [!DNL Data Migration Tool] sovrascrive tali nuove entità con quelle vecchie del Magento 1.

## Estensioni

Migra il codice dell’estensione del Magento 1 al Magento 2.

Per trovare le versioni più recenti delle estensioni, visita [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) o contatta il provider di estensioni.

È inoltre possibile utilizzare [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
