---
title: Best practice per aggiornare i servizi
description: Scopri come mantenere aggiornato lo stack di tecnologia Adobe Commerce su infrastruttura cloud.
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Best practice per aggiornare i servizi

Questo articolo fornisce consigli per mantenere aggiornato lo stack di tecnologia Adobe Commerce on cloud infrastructure e fornisce collegamenti a risorse utili.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.x e versioni successive

## Aggiorna servizi

Aggiorna i servizi e i componenti utilizzati da Adobe Commerce prima che raggiungano o siano prossimi alla data di fine del ciclo di vita. Questo consente di mantenere il passo con la conformità PCI e ridurre le vulnerabilità di sicurezza.

I clienti che utilizzano i piani Starter possono eseguire autonomamente gli aggiornamenti dei servizi. Fai riferimento a [Modifica versione del servizio](https://devdocs.magento.com/cloud/project/services.html#change-service-version) per informazioni dettagliate su come eseguire questa operazione.

I clienti che utilizzano i piani Pro possono effettuare il self-service solo con gli aggiornamenti dei servizi [Ambiente di integrazione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Per gli aggiornamenti dei servizi in produzione, è necessario [invia un ticket di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) richiesta dell’aggiornamento.

>[!WARNING]
>
>Gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione.

L&#39;elenco delle versioni del servizio e delle date di fine del ciclo di vita è disponibile nel seguente file: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Questo file non può essere considerato un’unica fonte di verità. In caso di dubbi, consulta i siti web ufficiali dei fornitori di queste tecnologie.

## Informazioni aggiuntive

[Requisiti di sistema](../../../installation/system-requirements.md)
