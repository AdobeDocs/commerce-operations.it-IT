---
title: Migra modifiche
description: Scopri come eseguire la migrazione solo dei dati che sono stati modificati dopo l’ultima migrazione dei dati del Magento 1 con [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# Migra modifiche

Lo strumento di migrazione incrementale installa le tabelle deltalog (con prefisso `m2_cl_*`) e i trigger (per il tracciamento delle modifiche) nel database del Magento 1 durante il [migrazione dei dati](data.md). Queste tabelle di dialogo dettagliate e i trigger sono essenziali per garantire la migrazione solo delle modifiche apportate nel Magento 1 dall&#39;ultima migrazione dei dati. Queste modifiche sono:

* Dati aggiunti dai clienti tramite vetrina (ordini creati, recensioni e modifiche nei profili dei clienti)

* Tutte le operazioni con ordini, prodotti e categorie nel pannello di amministrazione

>[!NOTE]
>
>Tutte le altre entità nuove o aggiornate immesse tramite l’amministratore, come gli attributi o le pagine CMS, non sono incluse nella migrazione incrementale e non vengono migrate.


Prima di iniziare, effettua le seguenti operazioni di preparazione:

1. Accedi al server applicazioni come [il proprietario del file system](../../../installation/prerequisites/file-system/overview.md).
1. Cambia in `/bin` o accertarsi che sia aggiunta al sistema `PATH`.

Consulta la [primi passi](overview.md#first-steps) per ulteriori dettagli.

## Eseguire il comando di migrazione incrementale

Per iniziare la migrazione delle modifiche incrementali, esegui:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. È possibile utilizzare questo argomento per testare la migrazione.

* `[-a|--auto]` è un argomento facoltativo che impedisce l&#39;arresto della migrazione quando si verificano errori di verifica dell&#39;integrità.

* `{<path to config.xml>}` è il percorso assoluto del file system a `config.xml`; questo argomento è obbligatorio.

>[!NOTE]
>
>La migrazione incrementale è un processo continuo; si riavvia automaticamente ogni 5 secondi. Utilizza CTRL-C per interrompere il processo di migrazione.


## Eseguire la migrazione dei dati creati da estensioni di terze parti

In `Delta` modalità, la [!DNL Data Migration Tool] esegue la migrazione dei dati creati solo dai moduli di Magento e non è responsabile del codice o delle estensioni create da sviluppatori di terze parti. Se queste estensioni hanno creato dati nel database storefront e il commerciante vuole averli nel Magento 2 — file di configurazione del [!DNL Data Migration Tool] devono essere create e modificate di conseguenza.

Se un’estensione dispone di tabelle proprie e devi tenere traccia delle modifiche per la migrazione delta, effettua le seguenti operazioni:

1. Aggiungi le tabelle da tracciare al `deltalog.xml` file
1. Creare una classe delta aggiuntiva che estende `Migration\App\Step\AbstractDelta`
1. Aggiungere il nome della classe appena creata alla sezione della modalità delta di `config.xml`
