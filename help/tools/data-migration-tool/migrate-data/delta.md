---
title: Migrare le modifiche
description: Scopri come eseguire la migrazione solo dei dati modificati dall’ultima migrazione dei dati del Magento 1 con [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Migrare le modifiche

Lo strumento di migrazione incrementale installa le tabelle di catalogo (con prefisso `m2_cl_*`) e trigger (per il tracciamento delle modifiche) nel database di Magento 1 durante il [migrazione dei dati](data.md). Queste tabelle e trigger di debug sono essenziali per garantire che esegua la migrazione solo delle modifiche apportate al Magento 1 dall’ultima migrazione dei dati. Queste modifiche sono:

* Dati aggiunti dai clienti tramite [vetrina](https://glossary.magento.com/storefront) (ordini creati, revisioni e modifiche nei profili cliente)

* Tutte le operazioni con ordini, prodotti e categorie nel [Amministratore](https://glossary.magento.com/magento-admin) pannello

>[!NOTE]
>
>Tutte le altre entità nuove o aggiornate immesse tramite l’amministratore, come le pagine Attributi o CMS, non sono incluse nella migrazione incrementale e non vengono migrate.


Prima di iniziare, procedi come segue per preparare:

1. Accedi al server delle applicazioni come [proprietario del file system](../../../installation/prerequisites/file-system/overview.md).
1. Cambia in `/bin` o assicurati che sia aggiunto al tuo sistema `PATH`.

Consulta la sezione [primi passi](overview.md#first-steps) per ulteriori dettagli.

## Esegui il comando di migrazione incrementale

Per avviare la migrazione delle modifiche incrementali, esegui:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dove:

* `[-r|--reset]` è un argomento facoltativo che avvia la migrazione dall’inizio. Puoi utilizzare questo argomento per testare la migrazione.

* `[-a|--auto]` è un argomento facoltativo che impedisce l’arresto della migrazione in caso di errori di controllo dell’integrità.

* `{<path to config.xml>}` è il percorso assoluto del file system a `config.xml`; questo argomento è obbligatorio.

>[!NOTE]
>
>La migrazione incrementale è un processo continuo; si riavvia automaticamente ogni 5 secondi. Utilizzare CTRL+C per interrompere il processo di migrazione.


## Eseguire la migrazione dei dati creati da estensioni di terze parti

In `Delta` la modalità [!DNL Data Migration Tool] esegue la migrazione dei dati creati solo dai moduli propri del Magento e non è responsabile del codice o delle estensioni effettuate da sviluppatori di terze parti. Se queste estensioni hanno creato dati nel database di storefront e il commerciante vuole avere questi dati nel Magento 2 — file di configurazione del [!DNL Data Migration Tool] devono essere create e modificate di conseguenza.

Se [estensione](https://glossary.magento.com/extension) dispone di proprie tabelle e devi tenere traccia delle relative modifiche per la migrazione delta, segui questi passaggi:

1. Aggiungi le tabelle da tracciare al `deltalog.xml` file
1. Crea una classe delta aggiuntiva che estende il `Migration\App\Step\AbstractDelta`
1. Aggiungi il nome della nuova classe creata alla sezione della modalità delta del `config.xml`
