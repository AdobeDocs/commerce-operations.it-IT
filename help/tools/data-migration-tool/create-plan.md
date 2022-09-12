---
title: Creare un piano di migrazione dei dati
description: Segui questi passaggi per creare un piano di migrazione dei dati per garantire il successo dell’aggiornamento dal Magento 1 al Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---


# Creare un piano di migrazione dei dati

Per eseguire correttamente la migrazione ed evitare problemi, devi pianificare e testare a fondo la migrazione.

## Prima di iniziare: Aggiornare

La migrazione è un momento perfetto per apportare cambiamenti seri e preparare il tuo sito per il prossimo livello di crescita. Valuta se il tuo nuovo sito deve essere progettato con più hardware o una topologia più avanzata con livelli di memorizzazione in cache migliori.

## Passaggio 1: Esamina le estensioni sul sito corrente

* Quali estensioni hai installato?

* Hai identificato se hai bisogno di tutte queste estensioni sul tuo nuovo sito? Ci potrebbero essere vecchi che si può tranquillamente rimuovere.

* Hai determinato se esistono versioni Magento 2 delle estensioni? Visita [Commerce Marketplace] per trovare le versioni più recenti o contatta il provider di estensioni.

* Quali risorse di database dalle estensioni vuoi eseguire la migrazione?

## Passaggio 2: Creare e preparare il negozio per la migrazione

* Impostare un sistema hardware di Magento 2 utilizzando la topologia e il design che almeno corrispondono al sistema di Magento 1 esistente

* Installa Magento 2.x (con tutti i moduli di questa versione) e [!DNL Data Migration Tool] su un sistema che soddisfa le [Requisiti di sistema Magenti]

* Apporta le modifiche personalizzate al [!DNL Data Migration Tool] nel caso in cui non sia necessario migrare alcuni dati (come pagine CMS, regole di vendita) o si desideri convertire la personalizzazione del Magento durante la migrazione. Leggi la sezione [!DNL Data Migration Tool]s [Specifiche tecniche](technical-specification.md) per comprendere meglio come funziona la migrazione dall&#39;interno

## Passaggio 3: Prova a secco

Prima di avviare la migrazione nell’ambiente di produzione, è meglio seguire tutti i passaggi di migrazione nell’ambiente di test.

In questo test di migrazione, segui questi passaggi:

* Copiare l&#39;archivio Magento 1 in un server di staging

* Migrazione completa dello store Magento 1 replicato al Magento 2

* Prova accuratamente il tuo nuovo negozio

## Passaggio 4: Avvia la migrazione

1. Assicurati che il [!DNL Data Migration Tool] dispone di un accesso di rete per connettersi ai database di Magento 1 e Magento 2. Apri le porte corrispondenti nel firewall.

1. Arresta tutte le attività nel pannello di amministrazione di Magento 1.x (ad eccezione della gestione degli ordini), ad esempio la spedizione, la creazione di fatture e note di credito. L&#39;elenco delle attività consentite può essere esteso regolando le impostazioni della modalità Delta nel [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Non devi riprendere queste attività finché il tuo negozio di Magento 2 non diventa attivo.

1. Consigliamo di interrompere tutti i lavori del cron Magento 1.x.

   Tuttavia, se durante la migrazione è necessario eseguire alcuni processi, assicurati che non creino nuove entità di database o modifichino quelle esistenti nel modo in cui tali entità non possono essere elaborate dalla modalità Delta.

   Ad esempio, il `enterprise_salesarchive_archive_orders` cron job sposta i vecchi ordini all&#39;archivio. L&#39;esecuzione di questo processo durante la migrazione è sicura perché la modalità Delta riconosce questo processo ed elabora correttamente gli ordini archiviati.

1. Utilizza la [!DNL Data Migration Tool] per migrare le impostazioni e i siti web.

1. Copia i file multimediali Magento 1.x in Magento 2.x.

   È necessario copiare manualmente questi file dal `magento1-root/media` directory to `magento2-root/pub/media`.

1. Utilizza la [!DNL Data Migration Tool] per copiare in massa i dati dal database di Magento 1 al database di Magento 2.

   Se alcune delle estensioni dispongono di dati da migrare, potrebbe essere necessario installare queste estensioni adattate per il Magento 2. Nel caso in cui le estensioni abbiano una struttura diversa nel database di Magento 2, utilizza i file di mappatura forniti con [!DNL Data Migration Tool].

1. Reindicizza tutti gli indici Magento 2.x. Per ulteriori informazioni, consulta la sezione [Guida alla configurazione].

## Passaggio 5: Apporta modifiche ai dati migrati (se necessario)

A volte può essere utile avere il tuo negozio Magento 2 con diverse strutture di catalogo, regole di vendita e pagine CMS dopo la migrazione.

È importante prestare attenzione durante l’elaborazione delle modifiche manuali dei dati. Gli errori creano errori nel passaggio di migrazione dei dati incrementale che segue.

Ad esempio, un prodotto eliminato dal Magento 2: quello che è stato acquistato sul tuo negozio live Magento 1 e che non è più disponibile nel tuo negozio Magento 2. Il trasferimento di dati su tale acquisto potrebbe causare un errore durante l&#39;esecuzione del [!DNL Data Migration Tool] in modalità Delta.

## Passaggio 6: Aggiornamento dei dati incrementali

Dopo la migrazione dei dati, devi acquisire in modo incrementale gli aggiornamenti dati aggiunti nell’archivio del Magento 1 (come nuovi ordini, revisioni e modifiche nei profili cliente) e trasferire questi aggiornamenti nell’archivio del Magento 2 utilizzando la modalità Delta.

* Avviare la migrazione incrementale; gli aggiornamenti vengono eseguiti continuamente. È possibile interrompere il trasferimento degli aggiornamenti in qualsiasi momento premendo `Ctrl+C`.

* Testa il tuo sito Magento 2 in questo periodo di tempo per risolvere eventuali problemi il prima possibile. In caso di problemi, premere `Ctrl+C` per interrompere la migrazione incrementale e riavviarla dopo aver risolto i problemi.

>[!NOTE]
>
>Gli avvisi sul controllo del volume possono comparire nel caso in cui si effettui un test del sito di Magento 2 ed esegua contemporaneamente il processo di migrazione. Questo accade perché nel Magento 2 si creano entità che non esistono nell&#39;istanza del Magento 1.

## Passaggio 7: Viva

Ora che il tuo sito Magento 2 è aggiornato con il Magento 1 e funziona normalmente, procedi come segue per passare al nuovo sito:

1. Mettere il sistema di Magento 1 in modalità di manutenzione (DOWNTIME STARTS).

1. Premere Ctrl+C nella finestra di comando dello strumento di migrazione per arrestare gli aggiornamenti incrementali.

1. Inizia il tuo Magento 2 lavori di cron.

1. Nel sistema di Magento 2, reindicizzare l&#39;indicizzatore delle azioni. Per ulteriori informazioni, consulta la sezione [Guida alla configurazione].

1. Utilizzando uno strumento a tua scelta, visita le pagine nel tuo sistema di Magento 2 per memorizzare in cache le pagine prima dei clienti che utilizzano la tua vetrina.

1. Esegui qualsiasi verifica finale del tuo sito di Magento 2.

1. Cambiare DNS, bilanciatori di carico e così via per puntare a nuovo hardware di produzione (DOWNTIME ENDS).

1. Lo store Magento 2 è ora pronto per l&#39;uso. Tu e i tuoi clienti potete riprendere tutte le attività.

<!-- LINK ADDRESSES -->
[Requisiti di sistema Magenti]: ../../installation/system-requirements.md
[Commerce Marketplace]: https://marketplace.magento.com
[Guida alla configurazione]: ../../configuration/cli/manage-indexers.md
