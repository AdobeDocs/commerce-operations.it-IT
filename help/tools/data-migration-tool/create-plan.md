---
title: Creare un piano di migrazione dati
description: Scopri come creare un piano di migrazione dei dati per l’aggiornamento da Magento 1 a Magento 2. Pianifica e verifica la migrazione per evitare problemi.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
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
source-wordcount: '890'
ht-degree: 0%
---
# Creare un piano di migrazione dei dati

Per eseguire correttamente la migrazione ed evitare problemi, è necessario pianificare in modo approfondito e testare la migrazione.

## Prima di iniziare: è consigliabile eseguire un aggiornamento

La migrazione è un buon momento per apportare modifiche sostanziali e preparare il tuo sito al prossimo livello di crescita. Valuta se il nuovo sito deve essere progettato con hardware aggiuntivo o con una topologia più avanzata con livelli di caching migliori.

## Passaggio 1: esaminare le estensioni sul sito corrente

* Quali estensioni hai installato?

* Hai identificato se tutte queste estensioni sono necessarie sul nuovo sito? Potrebbero esserci vecchi che puoi rimuovere in modo sicuro.

* Hai determinato se esistono versioni delle estensioni per Magento 2? Visita [Commerce Marketplace](https://commercemarketplace.adobe.com/) per trovare le versioni più recenti o contatta il provider di estensioni.

* Quali risorse di database dalle estensioni desideri migrare?

## Passaggio 2: creare e preparare il negozio per la migrazione

* Configurare un sistema hardware Magento 2 utilizzando una topologia e una progettazione che corrispondano almeno al sistema Magento 1 esistente

* Installa Magento 2 (con tutti i moduli di questa versione) e [!DNL Data Migration Tool] in un sistema che soddisfa i [requisiti di sistema](../../installation/system-requirements.md)

* Personalizzare il codice [!DNL Data Migration Tool] per ignorare alcuni dati (come pagine CMS e regole di vendita) o convertire personalizzazioni durante la migrazione. Leggi le [specifiche tecniche](technical-specification.md) di [!DNL Data Migration Tool] per ulteriori informazioni sul funzionamento della migrazione

## Passaggio 3: prova

Prima di avviare la migrazione nell’ambiente di produzione, segui tutti i passaggi di migrazione nell’ambiente di test.

In tale test di migrazione, segui questi passaggi:

* Copiare l’archivio di Magento 1 in un server di staging

* Migrazione completa dello store Magento 1 replicato a Magento 2

* Verifica accuratamente il nuovo store

## Passaggio 4: avviare la migrazione

1. Assicurarsi che [!DNL Data Migration Tool] disponga di un accesso di rete per connettersi ai database di Magento 1 e Magento 2. Aprire le porte corrispondenti nel firewall.

1. Interrompi tutte le attività nel pannello di amministrazione di Magento 1 (ad eccezione di Order Management), come la spedizione, la creazione di fatture e note di credito. L&#39;elenco delle attività consentite può essere esteso modificando le impostazioni della modalità Delta in [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Non riprendere queste attività fino a quando il tuo store di Magento 2 non diventa live.

1. È consigliabile interrompere tutti i processi cron di Magento 1.

   Se alcuni processi devono essere eseguiti durante la migrazione, assicurarsi che non creino o modifichino entità di database in modi che non possono essere elaborati in modalità Delta.

   Ad esempio, il processo cron `enterprise_salesarchive_archive_orders` sposta i vecchi ordini nell&#39;archivio. L&#39;esecuzione di questo processo durante la migrazione è sicura perché la modalità Delta lo riconosce ed elabora correttamente gli ordini archiviati.

1. Utilizzare [!DNL Data Migration Tool] per eseguire la migrazione di impostazioni e siti Web.

1. Copia i file multimediali Magento 1 in Magento 2.

   Copiare questi file manualmente dalla directory `magento1-root/media` in `magento2-root/pub/media`.

1. Utilizza [!DNL Data Migration Tool] per copiare in blocco i dati dal database di Magento 1 al database di Magento 2.

   Se alcune delle estensioni dispongono di dati di cui desideri eseguire la migrazione, potrebbe essere necessario installare queste estensioni adattate per Magento 2. Se le estensioni hanno una struttura diversa nel database di Magento 2, utilizza i file di mappatura forniti con [!DNL Data Migration Tool].

1. Reindicizza tutti gli indicizzatori di Magento 2. Per informazioni dettagliate, vedere [Gestire gli indicizzatori](../../configuration/cli/manage-indexers.md) nella _Guida alla configurazione_.

## Passaggio 5: apportare modifiche ai dati migrati (se necessario)

Dopo la migrazione, talvolta potrebbe essere utile disporre del negozio Magento 2 con una struttura di catalogo, regole di vendita e pagine CMS diverse.

È importante prestare attenzione quando si lavora con modifiche manuali ai dati. Errori creano errori nel passaggio di migrazione dati incrementale che segue.

Ad esempio, un prodotto eliminato da Magento 2: quello che è stato acquistato sul tuo store live di Magento 1 e che non è più disponibile nel tuo store di Magento 2. Il trasferimento di dati su tale acquisto potrebbe causare un errore durante l&#39;esecuzione di [!DNL Data Migration Tool] in modalità Delta.

## Passaggio 6: aggiornare i dati incrementali

Dopo la migrazione dei dati, utilizza la modalità Delta per acquisire e trasferire gli aggiornamenti incrementali da Magento 1 (come nuovi ordini, recensioni e modifiche al profilo cliente) a Magento 2.

* Avvia la migrazione incrementale; gli aggiornamenti vengono eseguiti continuamente. È possibile interrompere il trasferimento degli aggiornamenti in qualsiasi momento premendo `Ctrl+C`.

* Durante questo periodo, testa il tuo sito Magento 2 per rilevare eventuali problemi il prima possibile. In caso di problemi, premere `Ctrl+C` per interrompere la migrazione incrementale e riavviarla dopo aver risolto i problemi.

>[!NOTE]
>
>Se esegui test del sito Magento 2 ed esegui contemporaneamente il processo di migrazione, potrebbero comparire avvisi relativi al controllo del volume. Questo accade perché in Magento 2 si creano entità che non esistono nell’istanza di Magento 1.

## Passaggio 7: pubblicazione

Una volta completata la migrazione completa e il normale funzionamento del sito Magento 2, completa il passaggio:

1. Metti il sistema Magento 1 in modalità di manutenzione (DOWNTIME STARTS).

1. Premere Ctrl+C nella finestra di comando dello strumento di migrazione per interrompere gli aggiornamenti incrementali.

1. Avvia i processi cron di Magento 2.

1. Nel sistema Magento 2, reindicizza l’indicizzatore azionario. Per ulteriori informazioni, vedere [Gestire gli indicizzatori](../../configuration/cli/manage-indexers.md) nella _Guida alla configurazione_.

1. Utilizzando uno strumento a tua scelta, visita le pagine nel sistema Magento 2 per memorizzare in cache le pagine prima dei clienti che utilizzano la vetrina.

1. Esegui qualsiasi verifica finale del sito Magento 2.

1. Modificare il DNS, i load balancer e così via in modo che puntino al nuovo hardware di produzione (DOWNTIME ENDS).

1. Magento 2 Store è ora pronto per l’uso. Tu e i tuoi clienti potete riprendere tutte le attività.
