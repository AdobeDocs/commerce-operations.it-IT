---
title: Managed Services
description: Esamina le responsabilità di Adobe Managed Services, clienti e fornitori di servizi cloud per l’implementazione di Adobe Commerce sull’infrastruttura cloud.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Servizi gestiti

Per impostazione predefinita, Adobe Commerce sui servizi gestiti dell’infrastruttura cloud è protetto.

![Diagramma che mostra i servizi gestiti di Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilità condivisa

I piani Adobe Commerce Pro si basano su un modello di sicurezza con responsabilità condivisa. In questo modello, le diverse parti hanno diversi ambiti di responsabilità per il mantenimento della sicurezza del sistema. Questo approccio consente flessibilità e utilizzo delle migliori tecnologie cloud.

![Diagramma che mostra il modello di responsabilità condivisa di Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilità di Adobe Managed Services

Adobe Managed Services è responsabile della sicurezza e della disponibilità dell’ambiente cloud Adobe Commerce Pro, del codice dell’applicazione Adobe Commerce Pro di base e dei sistemi di e-commerce interni. Ciò include, tra l&#39;altro:

- Patch a livello di server
- Funzionamento dei servizi necessari per fornire i piani Adobe Commerce Pro
- Test di vulnerabilità
- Registrazione e monitoraggio degli eventi di sicurezza
- Gestione degli incidenti
- Monitoraggio operativo
- Supporto 24/7
- Garantire la disponibilità dell&#39;infrastruttura del cliente in conformità agli SLA

Adobe Managed Services è inoltre responsabile della gestione delle configurazioni del firewall del server (iptables) e del firewall perimetrale (gruppi di sicurezza). Adobe può anche rilasciare periodicamente aggiornamenti di sicurezza per l&#39;applicazione principale. È responsabilità dei clienti applicare queste patch. Queste aree sono tutte coperte dalla Certificazione PCI del sistema di infrastruttura cloud Adobe Commerce.

### Responsabilità di AWS

Adobe Managed Services utilizza Amazon Web Services (AWS) per l’infrastruttura del server cloud. AWS è responsabile della sicurezza della rete, inclusi routing, switching e protezione della rete perimetrale tramite sistemi firewall e sistemi di rilevamento intrusioni (IDS). AWS è responsabile della sicurezza fisica dei centri dati che gestiscono gli ambienti cloud Adobe Commerce, nonché della sicurezza ambientale per garantire che siano eseguiti i controlli di alimentazione, raffreddamento e meccanismo appropriati.

Adobe Commerce Pro prevede di utilizzare:

- Amazon Elastic Compute Cloud (EC2)
- Servizio di archiviazione semplice Amazon (S3)
- Archivio blocchi elastici Amazon (EBS)
- Amazon Virtual Private Cloud (VPC)
- Bilanciamento del carico elastico (ELB) di Amazon
- Servizi cloud Trail di Amazon.

Amazon dispone di un ampio programma di conformità, che include le certificazioni PCI DSS, SOC 2 e ISO 27001.

### Responsabilità del partner/cliente della soluzione

Il cliente è principalmente responsabile della sicurezza dell’implementazione personalizzata dell’applicazione Adobe Commerce in esecuzione nell’ambiente cloud del piano Adobe Commerce Pro. Ciò include:

- Garantire una configurazione e una codifica sicure delle attività di monitoraggio dell&#39;applicazione e della sicurezza, compresi test di penetrazione e analisi regolari della vulnerabilità.

- La sicurezza di personalizzazioni, estensioni, altre applicazioni o integrazioni utilizzate nel proprio sistema.

- La sicurezza dei loro utenti e la concessione dell&#39;accesso alla loro configurazione e applicazione.

- Il cliente controlla tutte le distribuzioni di codice nei propri ambienti non di produzione. Questo controllo ha anche la responsabilità di applicare patch di sicurezza dell’applicazione all’applicazione Adobe Commerce di base, alle estensioni o a qualsiasi codice personalizzato.

- Il cliente deve eseguire test di penetrazione della propria applicazione personalizzata. Queste responsabilità possono essere affrontate tramite risorse tecniche da parte del cliente, dei partner di implementazione o dei servizi professionali Adobe Commerce.

- I clienti sono responsabili dei requisiti PCI della propria applicazione personalizzata e dei propri processi. La conformità PCI del cliente si basa sulle certificazioni PCI di AWS e Adobe Commerce per ridurre al minimo le aree da rivedere.
