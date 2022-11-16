---
title: Best practice per l'elaborazione e l'archiviazione dei pagamenti
description: Scopri come elaborare e archiviare in modo sicuro i dettagli di pagamento
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 124eaf6e7b465b320d3d7e6a3694130edb93f187
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# Best practice per l&#39;elaborazione e lo storage dei pagamenti

Uno dei principi fondamentali per mantenere [Conformità PCI](https://nam04.safelinks.protection.outlook.com/GetUrlReputation) sta adottando una strategia per elaborare e memorizzare correttamente i pagamenti con carta di credito.

Archiviare i dati dei titolari di carte in Adobe Commerce è **severamente vietato** e fare ciò potrebbe essere una violazione dei tuoi obblighi come commerciante ai sensi dello standard PCI-DSS (Payment Card Industry Data Security Standard). Maggiori informazioni sul nostro modello di responsabilità condivisa e le linee guida per gli obblighi dei commercianti sono disponibili nella [guida alla responsabilità condivisa per Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) nell&#39;Adobe Trust Center.

Segui le best practice riportate di seguito per assicurarti di elaborare correttamente le informazioni di pagamento sul tuo sito eCommerce. Ulteriori indicazioni sulle best practice generali sulla sicurezza sono disponibili nella [guida alle best practice sulla sicurezza per Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) sul centro di fiducia Adobe

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

* Adobe Commerce su infrastruttura cloud
* Adobe Commerce on-premise

## Protezione dei dati dei titolari delle carte

Se è necessario archiviare i dati del titolare della carta, i dati del titolare della carta devono essere conservati al di fuori di Adobe Commerce con garanzie di archiviazione. L&#39;esistenza di garanzie di archiviazione per i dettagli di pagamento, come i dati dei titolari della carta di credito, aiuta a prevenire frodi e altri potenziali problemi di sicurezza. In linea con gli altri standard PCI, avere delle protezioni è la prima linea di difesa. Alcuni metodi preferiti per migliorare la protezione dei dati memorizzati includono crittografia, troncamento, tokenizzazione, hash unidirezionale e mascheramento.

Le protezioni per le chiavi crittografiche sono vitali per le strategie di protezione dei dati. È fondamentale che i custodi competenti e affidabili controllino queste chiavi.

Infine, un numero di account primario (PAN) deve essere illeggibile durante l&#39;archiviazione (ad esempio, mascherato come XXX). Ciò include lo storage portatile e i supporti di backup come unità flash, unità USB e dischi rigidi esterni, e persino i registri di controllo.

## Cifratura della trasmissione dei dati del titolare della carta

La salvaguardia dei dati durante la trasmissione è fondamentale per proteggere le informazioni sui pagamenti, come i dati dei titolari delle carte. Quando queste informazioni vengono trasmesse su reti aperte, possono diventare più vulnerabili ai problemi di sicurezza.

### Utilizzare protocolli di trasmissione sicuri

Trasmettere i dati dei titolari di carte utilizzando protocolli e pratiche di trasmissione sicuri, tra cui:

* Chiavi e certificati attendibili
* Protocolli di trasmissione sicuri come TLS, SSH o VPN
* Algoritmi asimmetrici nella crittografia
* Test di Tokenization, masking e penetrazione con trasmissione e visualizzazione di PAN
* Limitare l&#39;accesso ai dati dei titolari della carta
* L&#39;accesso alle informazioni sensibili dovrebbe essere limitato in base alle necessità di sapere e concesso solo al personale autorizzato con esigenze aziendali

Il metodo consigliato per gestire i dati del titolare della carta consiste nel non memorizzare il numero di conto principale (PAN), ma nel eseguire il token con un provider di elaborazione del pagamento specifico e memorizzare il token, il tipo di carta e la data di scadenza crittografata. Puoi utilizzare il token come credenziale su file per utilizzi futuri, in quanto è univoco solo per ciascun esercente. Poiché il token è univoco, se si verifica un problema di sicurezza, il token in invalidato aiuta a prevenire attività fraudolente

## Informazioni aggiuntive

Se stai cercando soluzioni di pagamento consigliate per Adobe, ti preghiamo di prendere in considerazione [Adobe servizi di pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
