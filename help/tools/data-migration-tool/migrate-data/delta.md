---
title: Migra modifiche
description: Scopri come eseguire la migrazione solo dei dati che sono stati modificati dopo l’ultima migrazione dei dati di Magento 1 con [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
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
source-wordcount: '358'
ht-degree: 0%
---
# Migra modifiche

Lo strumento di migrazione incrementale installa tabelle deltalog (con prefisso `m2_cl_*`) e trigger (per il rilevamento delle modifiche) nel database Magento 1 durante la [migrazione dei dati](data.md). Queste tabelle di dialogo e questi trigger sono essenziali per garantire che esegui la migrazione solo delle modifiche apportate in Magento 1 dall’ultima migrazione dei dati. Queste modifiche sono:

* Dati aggiunti dai clienti tramite vetrina (ordini creati, recensioni e modifiche nei profili dei clienti)

* Tutte le operazioni con ordini, prodotti e categorie nel pannello di amministrazione

>[!NOTE]
>
>Tutte le altre entità nuove o aggiornate immesse tramite l’amministratore, come gli attributi o le pagine CMS, non sono incluse nella migrazione incrementale e non vengono migrate.


Prima di iniziare, effettua le seguenti operazioni di preparazione:

1. Accedere al server applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).
1. Passare alla directory `/bin` o assicurarsi che sia aggiunta al sistema `PATH`.

Per ulteriori dettagli, consulta la sezione [primi passaggi](overview.md#first-steps).

## Eseguire il comando di migrazione incrementale

Per iniziare la migrazione delle modifiche incrementali, esegui:

```shell
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall&#39;inizio. È possibile utilizzare questo argomento per testare la migrazione.

* `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.

* `{<path to config.xml>}` è il percorso assoluto del file system di `config.xml`. Questo argomento è obbligatorio.

>[!NOTE]
>
>La migrazione incrementale è un processo continuo; si riavvia automaticamente ogni 5 secondi. Utilizza CTRL-C per interrompere il processo di migrazione.


## Eseguire la migrazione dei dati creati da estensioni di terze parti

Nella modalità `Delta`, [!DNL Data Migration Tool] esegue la migrazione dei dati creati solo dai moduli di Magento e non è responsabile del codice o delle estensioni create da sviluppatori di terze parti. Se queste estensioni hanno creato dati nel database storefront e il commerciante desidera che questi dati siano presenti in Magento 2, i file di configurazione di [!DNL Data Migration Tool] devono essere creati e modificati di conseguenza.

Se un’estensione dispone di tabelle proprie e devi tenere traccia delle modifiche per la migrazione delta, effettua le seguenti operazioni:

1. Aggiungere le tabelle da tracciare al file `deltalog.xml`
1. Creare una classe delta aggiuntiva che estende `Migration\App\Step\AbstractDelta`
1. Aggiungere il nome della classe appena creata alla sezione della modalità delta di `config.xml`
