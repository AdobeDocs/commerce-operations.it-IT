---
title: Managed Services
description: Review the responsibilities of Adobe Managed Services, customers, and cloud service providers for your Adobe Commerce on cloud infrastructure implementaiton.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Managed services

Per impostazione predefinita, Adobe Commerce sui servizi gestiti dall’infrastruttura cloud è protetto.

![Diagramma che mostra Adobe Commerce Managed Services](../../../assets/playbooks/managed-services.svg)

## Shared responsibility

I piani di Adobe Commerce Pro si basano su un modello di sicurezza con responsabilità condivisa. In this model, different parties have different areas of responsibility for maintaining the security of the system. Questo approccio consente flessibilità e utilizzo delle migliori tecnologie cloud.

![Diagramma che mostra il modello di responsabilità condivisa di Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilità dei servizi gestiti da Adobe

Adobe Managed Services is responsible for the security and availability of the Adobe Commerce Pro cloud environment, the core Adobe Commerce Pro application code, and internal commerce systems. This includes, but is not limited to:

- Patch a livello di server
- Funzionamento dei servizi necessari per la fornitura dei piani Adobe Commerce Pro
- Test di vulnerabilità
- Security event logging and monitoring
- Gestione degli incidenti
- Monitoraggio operativo
- Supporto 24/7
- Ensuring that the customer infrastructure is available in accordance with SLAs

Adobe Managed Services è inoltre responsabile della gestione delle configurazioni del firewall del server (iptables) e del firewall perimetrale (gruppi di sicurezza). Adobe may also release security updates to the core application on a periodic basis. È responsabilità dei clienti applicare queste patch. Queste aree sono tutte coperte dalla certificazione PCI del sistema di infrastruttura cloud Adobe Commerce.

### AWS responsibilities

Adobe Managed Services utilizza Amazon Web Services (AWS) per l’infrastruttura del server cloud. AWS è responsabile della sicurezza della rete, compresi routing, switching e sicurezza della rete perimetrale tramite sistemi firewall e sistemi di rilevamento intrusioni (IDS). AWS is responsible for physical security to the data centers managing the Adobe Commerce cloud environments, as well as environmental security to ensure proper power, cooling, and mechanism controls are in place.

Adobe Commerce Pro plans use:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Bilanciamento del carico elastico (ELB) di Amazon
- Servizi cloud Trail di Amazon.

Amazon dispone di un ampio programma di conformità, che include le certificazioni PCI DSS, SOC 2 e ISO 27001.

### Solution partner/customer responsibilities

Il cliente è principalmente responsabile della sicurezza dell’implementazione personalizzata dell’applicazione Commerce di Adobe in esecuzione nell’ambiente cloud del piano Adobe Commerce Pro. Ciò include:

- Garantire una configurazione e una codifica sicure delle attività di monitoraggio dell&#39;applicazione e della sicurezza, compresi test di penetrazione e analisi regolari della vulnerabilità.

- The security of any customization, extensions, other applications, or integrations used in their system.

- La sicurezza dei loro utenti e la concessione dell&#39;accesso alla loro configurazione e applicazione.

- The customer controls all code deployments to their non-production environments. Questo controllo ha anche la responsabilità di applicare patch di sicurezza dell’applicazione all’applicazione Commerce di Adobe di base, alle estensioni o a qualsiasi codice personalizzato.

- Il cliente deve eseguire test di penetrazione della propria applicazione personalizzata. Queste responsabilità possono essere affrontate tramite risorse tecniche da parte del cliente, dei partner di implementazione o dei servizi professionali Adobe Commerce.

- I clienti sono responsabili dei requisiti PCI della propria applicazione personalizzata e dei propri processi. La conformità PCI del cliente si basa sulle certificazioni PCI di AWS e Adobe Commerce per ridurre al minimo le aree da rivedere.
