---
title: Best practice per l’elaborazione e l’archiviazione dei pagamenti
description: Scopri come elaborare e memorizzare in modo sicuro i dettagli di pagamento
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Best practice per l’elaborazione e l’archiviazione dei pagamenti

Uno dei principi chiave per mantenere la conformità PCI [1&rbrace; consiste nell&#39;avere una strategia per elaborare e archiviare correttamente i pagamenti con carta di credito.](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html?lang=it)

Memorizzare i dati del titolare della carta in Adobe Commerce è **severamente vietato** e ciò potrebbe costituire una violazione dei tuoi obblighi in quanto esercente in base allo standard PCI-DSS (Payment Card Industry Data Security Standard). Ulteriori informazioni sul modello di responsabilità condivisa e sulle linee guida per gli obblighi degli esercenti sono disponibili nella [Guida al modello di responsabilità condivisa di Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) nel Centro affidabilità di Adobe.

Segui le best practice riportate di seguito per assicurarti di elaborare correttamente le informazioni di pagamento sul tuo sito eCommerce. Per ulteriori informazioni sulle procedure consigliate per la sicurezza, vedere [Proteggere il sito e l&#39;infrastruttura](../launch/security-best-practices.md).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

* Adobe Commerce sull’infrastruttura cloud
* Adobe Commerce on-premise

## Protezione dei dati del titolare della carta

Se è necessario memorizzare i dati del titolare della carta, questi devono essere memorizzati al di fuori di Adobe Commerce con protezioni per la conservazione. L&#39;esistenza di protezioni per la memorizzazione dei dati di pagamento, come i dati dei titolari della carta di credito, contribuisce a prevenire le frodi e altri potenziali problemi di sicurezza. In linea con gli altri standard PCI, la prima linea di difesa consiste nell&#39;adozione di protezioni. Alcuni metodi preferiti per migliorare la protezione dei dati memorizzati includono la crittografia, il troncamento, la tokenizzazione, l’hashing unidirezionale e il masking.

Le protezioni per le chiavi crittografiche sono fondamentali per le strategie di protezione dei dati. È fondamentale disporre di custodi competenti e affidabili che supervisionino queste chiavi.

Infine, un numero di account principale (PAN) deve essere illeggibile durante l&#39;archiviazione, ad esempio mascherato con `XXX`. Ciò include storage portatile e supporti di backup quali unità flash, USB e dischi rigidi esterni, nonché registri di verifica.

## Crittografare la trasmissione dei dati del titolare della carta

La protezione dei dati durante la trasmissione è fondamentale per proteggere le informazioni sui pagamenti, come i dati dei titolari della carta. Quando queste informazioni vengono trasmesse su reti aperte, possono diventare più vulnerabili a problemi di sicurezza.

### Utilizzare protocolli di trasmissione sicuri

Trasmettere i dati dei titolari delle carte utilizzando protocolli e pratiche di trasmissione sicuri, tra cui:

* Chiavi e certificati attendibili
* Protocolli di trasmissione sicuri come TLS, SSH o VPN
* Algoritmi asimmetrici nella crittografia
* Tokenizzazione, mascheramento e test di penetrazione con PAN di trasmissione e visualizzazione
* Limita l’accesso ai dati del titolare della carta
* L&#39;accesso alle informazioni sensibili dovrebbe essere limitato in base al principio della necessità di sapere e concesso solo al personale autorizzato con esigenze aziendali

Il metodo consigliato per gestire i dati del titolare della carta consiste nel tokenizzarli invece di memorizzarli. Tokenizza la carta con un provider di elaborazione dei pagamenti specifico e archivia il token, il tipo di carta e la data di scadenza crittografata. Puoi utilizzare il token come credenziale su file per utilizzi futuri, in quanto è univoco solo per ogni commerciante. Poiché il token è univoco, in caso di problemi di sicurezza il token viene invalidato, contribuendo a prevenire attività fraudolente.

## Informazioni aggiuntive

Se stai cercando soluzioni di pagamento consigliate da Adobe, prendi in considerazione [Servizi di pagamento Adobe](https://experienceleague.adobe.com/docs/commerce/payment-services/overview.html?lang=it).
