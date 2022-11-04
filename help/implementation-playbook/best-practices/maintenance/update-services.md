---
title: Best practice per l’aggiornamento dei servizi
description: Scopri come mantenere aggiornato lo stack di tecnologia dell’infrastruttura cloud Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per l’aggiornamento dei servizi

Questo articolo fornisce raccomandazioni per mantenere aggiornato lo stack di tecnologia dell’infrastruttura cloud Adobe Commerce e fornisce collegamenti a risorse utili.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.x e versioni successive

## Aggiorna servizi

Aggiorna i servizi e i componenti utilizzati da Adobe Commerce prima che raggiungano o siano prossimi alla data di fine del ciclo di vita. Questo aiuta a tenere il passo con la conformità PCI e a ridurre le vulnerabilità di sicurezza.

I clienti che utilizzano i piani Starter possono self-service su aggiornamenti di servizi. Fai riferimento a [Cambia versione del servizio](https://devdocs.magento.com/cloud/project/services.html#change-service-version) per informazioni dettagliate su come eseguire questa operazione.

I clienti su piani Pro possono solo self-service su aggiornamenti di servizi nel loro [Ambiente di integrazione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md). Per gli aggiornamenti dei servizi su Produzione, devi [inviare un ticket di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) richiesta dell&#39;aggiornamento.

>[!WARNING]
>
>Gli aggiornamenti del servizio non possono essere inviati all&#39;ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Questo è necessario in quanto è necessario garantire la disponibilità di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro un intervallo di tempo desiderato e ridurre al minimo i tempi di inattività dell&#39;ambiente di produzione.

Puoi visualizzare l’elenco delle versioni del servizio e delle date di fine del ciclo di vita nel file seguente: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Questo file non può essere considerato una singola fonte di verità. Se hai dubbi, fai riferimento ai siti web ufficiali dei fornitori per queste tecnologie.

## Informazioni aggiuntive

[Requisiti di sistema](../../../installation/system-requirements.md)
