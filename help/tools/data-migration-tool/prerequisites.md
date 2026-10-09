---
title: '[!DNL Data Migration Tool] prerequisiti'
description: Scopri cosa devi fare prima di iniziare a utilizzare [!DNL Data Migration Tool] per trasferire dati tra Magento 1 e Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%
---
# [!DNL Data Migration Tool] prerequisiti

Prima di avviare la migrazione, accertati che siano soddisfatti i seguenti requisiti.

## Sistema Magento 2

* Configura il tuo sistema Magento 2 in modo che soddisfi i [requisiti di sistema](../../installation/system-requirements.md).

  Utilizza una topologia e una progettazione che corrispondano almeno al sistema Magento 1 esistente.

* [Installa Magento 2](../../installation/overview.md).

## Cron

Non avviare i processi cron di Magento 2.

## Database

* Dopo l&#39;installazione, esegui il backup o [dump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) del database Magento 2 il prima possibile. Questo consente di ripristinare lo stato iniziale del database se la migrazione non ha esito positivo.

* Verificare che [!DNL Data Migration Tool] disponga dell&#39;accesso di rete per connettere i database Magento 1 e Magento 2.

  Aprire le porte del firewall in modo che lo strumento di migrazione possa comunicare con i database.

* Assicurarsi che gli account MySQL dispongano di tutti i privilegi necessari per accedere ai database Magento.

Se la registrazione binaria è abilitata per il database Magento 1, impostare la variabile di sistema MySQL globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) su `1` o concedere il privilegio [SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) al proprio account.

* Non è consigliabile creare nuove entità (prodotti, categorie e attributi) nell&#39;archivio di Magento 2 prima della migrazione, perché [!DNL Data Migration Tool] sovrascrive tali nuove entità con quelle precedenti di Magento 1.

## Estensioni

Migra il codice dell’estensione Magento 1 a Magento 2.

Per trovare le versioni più recenti delle estensioni, visita [[!DNL [Commerce Marketplace]]](https://commercemarketplace.adobe.com//) o contatta il provider di estensioni.

È inoltre possibile utilizzare [[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
