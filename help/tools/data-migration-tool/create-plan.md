---
title: Creare un piano di migrazione dei dati
description: Segui questi passaggi per creare un piano di migrazione dei dati per garantire un aggiornamento corretto dal Magento 1 al Magento 2.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Creare un piano di migrazione dei dati

Per eseguire correttamente la migrazione ed evitare problemi, è necessario pianificare e testare a fondo la migrazione.

## Prima di iniziare: valuta l’aggiornamento

La migrazione è il momento ideale per apportare modifiche sostanziali e preparare il tuo sito al prossimo livello di crescita. Valuta se il nuovo sito deve essere progettato con più hardware o con una topologia più avanzata con migliori livelli di caching.

## Passaggio 1: esaminare le estensioni sul sito corrente

* Quali estensioni hai installato?

* Hai identificato se tutte queste estensioni sono necessarie sul nuovo sito? Potrebbero esserci vecchi che puoi rimuovere in modo sicuro.

* Hai determinato se esistono versioni di Magento 2 delle estensioni? Visita [Commerce Marketplace] per trovare le versioni più recenti o contatta il provider di estensioni.

* Quali risorse di database dalle estensioni desideri migrare?

## Passaggio 2: creare e preparare il negozio per la migrazione

* Configurare un sistema hardware di Magento 2 utilizzando la topologia e la progettazione che corrisponda almeno al Magento 1 esistente

* Installa Magento 2.x (con tutti i moduli di questa versione) e [!DNL Data Migration Tool] in un sistema che soddisfa i [requisiti di sistema](../../installation/system-requirements.md)

* Apporta le modifiche personalizzate al codice [!DNL Data Migration Tool] nel caso non sia necessario eseguire la migrazione di alcuni dati (come pagine CMS, regole di vendita) o convertire la personalizzazione del Magento durante la migrazione. Leggi le [specifiche tecniche](technical-specification.md) di [!DNL Data Migration Tool] per comprendere meglio come funziona la migrazione dall&#39;interno

## Passaggio 3: prova

Prima di avviare la migrazione nell’ambiente di produzione, è consigliabile eseguire tutti i passaggi di migrazione nell’ambiente di test.

In tale test di migrazione, segui questi passaggi:

* Copiare l&#39;archivio del Magento 1 in un server di gestione temporanea

* Migrazione completa dell&#39;archivio del Magento 1 replicato al Magento 2

* Verifica accuratamente il nuovo store

## Passaggio 4: avviare la migrazione

1. Assicurarsi che [!DNL Data Migration Tool] disponga di un accesso di rete per connettersi ai database del Magento 1 e del Magento 2. Aprire le porte corrispondenti nel firewall.

1. Interrompi tutte le attività nel pannello di amministrazione di Magento 1.x (ad eccezione della gestione degli ordini), come spedizione, creazione di fatture e note di accredito. L&#39;elenco delle attività consentite può essere esteso modificando le impostazioni della modalità Delta in [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Non devi riprendere queste attività fino a quando il tuo store di Magento 2 non diventa live.

1. È consigliabile interrompere tutti i processi cron del Magento 1.x.

   Tuttavia, se durante la migrazione sono necessari alcuni processi, assicurarsi che non creino nuove entità di database o non modifichino quelle esistenti nel modo in cui tali entità non possono essere elaborate in modalità Delta.

   Ad esempio, il processo cron `enterprise_salesarchive_archive_orders` sposta i vecchi ordini nell&#39;archivio. L&#39;esecuzione di questo processo durante la migrazione è sicura perché la modalità Delta lo riconosce ed elabora correttamente gli ordini archiviati.

1. Utilizzare [!DNL Data Migration Tool] per eseguire la migrazione di impostazioni e siti Web.

1. Copiare i file multimediali Magento 1.x nel Magento 2.x.

   È necessario copiare questi file manualmente dalla directory `magento1-root/media` a `magento2-root/pub/media`.

1. Utilizza [!DNL Data Migration Tool] per copiare in blocco i dati dal database del Magento 1 al database del Magento 2.

   Se alcune delle estensioni contengono dati di cui desideri eseguire la migrazione, potrebbe essere necessario installare queste estensioni adattate per il Magento 2. Se le estensioni hanno una struttura diversa nel database del Magento 2, utilizzare i file di mapping forniti con [!DNL Data Migration Tool].

1. Reindicizza tutti gli indici Magento 2.x. Per informazioni dettagliate, vedere [Gestire gli indicizzatori](../../configuration/cli/manage-indexers.md) nella _Guida alla configurazione_.

## Passaggio 5: apportare modifiche ai dati migrati (se necessario)

A volte potrebbe essere utile che il tuo archivio Magento 2 sia memorizzato con una struttura di catalogo, regole di vendita e pagine CMS diverse dopo la migrazione.

È importante prestare attenzione quando si lavora con modifiche manuali ai dati. Errori creano errori nel passaggio di migrazione dati incrementale che segue.

Ad esempio, un prodotto eliminato dal Magento 2: quello che è stato acquistato nel tuo negozio live il Magento 1 e che non è più disponibile nel tuo negozio Magento 2. Il trasferimento di dati su tale acquisto potrebbe causare un errore durante l&#39;esecuzione di [!DNL Data Migration Tool] in modalità Delta.

## Passaggio 6: aggiornare i dati incrementali

Dopo la migrazione dei dati, è necessario acquisire in modo incrementale gli aggiornamenti dei dati aggiunti nell&#39;archivio del Magento 1 (ad esempio nuovi ordini, revisioni e modifiche nei profili cliente) e trasferire tali aggiornamenti nell&#39;archivio del Magento 2 utilizzando la modalità Delta.

* Avvia la migrazione incrementale; gli aggiornamenti vengono eseguiti continuamente. È possibile interrompere il trasferimento degli aggiornamenti in qualsiasi momento premendo `Ctrl+C`.

* Durante questo periodo, verifica il tuo sito Magento 2 per individuare eventuali problemi il prima possibile. In caso di problemi, premere `Ctrl+C` per interrompere la migrazione incrementale e riavviarla dopo aver risolto i problemi.

>[!NOTE]
>
>È possibile che vengano visualizzati avvisi relativi al controllo del volume se si esegue contemporaneamente il test del sito del Magento 2 ed il processo di migrazione. Ciò accade perché nel Magento 2 vengono create entità che non esistono nell&#39;istanza del Magento 1.

## Passaggio 7: pubblicazione

Ora che il sito del Magento 2 è aggiornato al Magento 1 e funziona normalmente, eseguire le operazioni seguenti per passare al nuovo sito:

1. Mettere il Magento 1 in modalità di manutenzione (AVVIO DOWNTIME).

1. Premere Ctrl+C nella finestra di comando dello strumento di migrazione per interrompere gli aggiornamenti incrementali.

1. Avvia i processi cron del Magento 2.

1. Nel Magento 2, reindicizzare l&#39;indicizzatore di azioni. Per ulteriori informazioni, vedere la [Guida alla configurazione].

1. Utilizzando uno strumento a tua scelta, visita le pagine nel Magento 2 per memorizzare in cache le pagine prima dei clienti che utilizzano la vetrina.

1. Eseguire qualsiasi verifica finale del sito Magento 2.

1. Modificare il DNS, i load balancer e così via in modo che puntino al nuovo hardware di produzione (DOWNTIME ENDS).

1. Lo store del Magento 2 è ora pronto per l’uso. Tu e i tuoi clienti potete riprendere tutte le attività.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
