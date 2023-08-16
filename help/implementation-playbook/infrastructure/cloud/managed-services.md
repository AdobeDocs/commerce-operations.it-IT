---
title: Managed Services
description: Esamina le responsabilità di Adobe Managed Services, dei clienti e dei provider di servizi cloud per l’implementazione dell’infrastruttura cloud Adobe Commerce.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed Services

I servizi gestiti di Adobe Commerce su infrastruttura cloud sono sicuri per impostazione predefinita.

![Diagramma che mostra i servizi gestiti di Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilità condivisa

I piani di Adobe Commerce Pro si basano su un modello di sicurezza con responsabilità condivisa. In questo modello, le diverse parti hanno diverse aree di responsabilità per il mantenimento della sicurezza del sistema. Questo approccio consente sia la flessibilità che l’utilizzo delle migliori tecnologie cloud.

![Diagramma che mostra il modello di responsabilità condivisa Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilità Managed Services di Adobe

Adobe Managed Services è responsabile della sicurezza e della disponibilità dell’ambiente cloud Adobe Commerce Pro, del codice dell’applicazione Adobe Commerce Pro di base e dei sistemi di e-commerce interni. Ciò include, ma non è limitato a:

- Applicazione di patch a livello di server
- Gestione dei servizi necessari per fornire i piani di Adobe Commerce Pro
- Test di vulnerabilità
- Registrazione e monitoraggio degli eventi di sicurezza
- Gestione degli incidenti
- Monitoraggio operativo
- Supporto 24/7
- Garanzia di disponibilità dell&#39;infrastruttura del cliente in conformità agli SLA

Adobe Managed Services è anche responsabile della gestione delle configurazioni del firewall del server (iptables) e delle configurazioni del firewall perimetrale (gruppi di sicurezza). Adobe può inoltre rilasciare periodicamente aggiornamenti di sicurezza per l’applicazione principale. L&#39;applicazione di queste patch è responsabilità del cliente. Queste aree sono tutte coperte dalla certificazione PCI di Adobe Commerce su infrastruttura cloud.

### Responsabilità di AWS

Adobe Managed Services utilizza Amazon Web Services (AWS) per l’infrastruttura del server cloud. AWS è responsabile della sicurezza della rete, inclusi routing, switching e sicurezza della rete perimetrale tramite sistemi firewall e sistemi di rilevamento delle intrusioni (IDS). AWS è responsabile della sicurezza fisica dei centri dati che gestiscono gli ambienti cloud Adobe Commerce, nonché della sicurezza ambientale per garantire che siano presenti i controlli appropriati di alimentazione, raffreddamento e meccanismo.

I piani di Adobe Commerce Pro utilizzano:

- Amazon Elastic Compute Cloud (EC2)
- Servizio Amazon Simple Storage (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Bilanciatore di carico elastico Amazon (ELB)
- Servizi Amazon Cloud Trail.

Amazon dispone di un ampio programma di conformità che include certificazioni PCI DSS, SOC 2 e ISO 27001.

### Responsabilità del partner/cliente della soluzione

Il cliente è principalmente responsabile della sicurezza dell’implementazione personalizzata dell’applicazione Adobe Commerce in esecuzione nell’ambiente cloud del piano Adobe Commerce Pro. Ciò include:

- Garantire una configurazione e una codifica sicure delle attività di monitoraggio dell’applicazione e della sicurezza, compresi test di penetrazione e analisi regolari delle vulnerabilità.

- La sicurezza di qualsiasi personalizzazione, estensione, altre applicazioni o integrazioni utilizzate nel loro sistema.

- La sicurezza dei loro utenti e la concessione dell&#39;accesso alla loro configurazione e applicazione.

- Il cliente controlla tutte le distribuzioni del codice nei propri ambienti non di produzione. Questo controllo è anche responsabile dell’applicazione delle patch di sicurezza dell’applicazione all’applicazione principale Adobe Commerce, alle estensioni o a qualsiasi codice personalizzato.

- Il cliente deve eseguire test di penetrazione dell’applicazione personalizzata. Queste responsabilità possono essere gestite da risorse tecniche fornite dal cliente, dai partner di implementazione o dai servizi professionali Adobe Commerce.

- I clienti sono responsabili dei requisiti PCI dell&#39;applicazione personalizzata e dei propri processi. La conformità PCI del cliente si basa sulle certificazioni PCI di AWS e Adobe Commerce al fine di ridurre al minimo le aree da rivedere.
