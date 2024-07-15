---
title: Best practice per aggiornare i servizi
description: Scopri come mantenere aggiornato lo stack di tecnologia Adobe Commerce su infrastruttura cloud.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Best practice per aggiornare i servizi

Questo articolo fornisce consigli per mantenere aggiornato lo stack di tecnologia Adobe Commerce on cloud infrastructure e fornisce collegamenti a risorse utili.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.x e versioni successive

## Aggiorna servizi

Aggiorna i servizi e i componenti utilizzati da Adobe Commerce prima che raggiungano o siano prossimi alla data di fine del ciclo di vita. Questo consente di mantenere il passo con la conformità PCI e ridurre le vulnerabilità di sicurezza.

I clienti che utilizzano i piani Starter possono eseguire autonomamente gli aggiornamenti dei servizi. Per ulteriori informazioni su come eseguire questa operazione, consultare [Modifica versione del servizio](https://devdocs.magento.com/cloud/project/services.html#change-service-version).

I clienti con piani Pro possono eseguire il self-service solo sugli aggiornamenti dei servizi nel proprio [ambiente di integrazione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Per gli aggiornamenti dei servizi in produzione, è necessario [inviare un ticket di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) richiedendo l&#39;aggiornamento.

>[!WARNING]
>
>Gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione.

È possibile visualizzare l&#39;elenco delle versioni del servizio e delle date di fine del ciclo di vita nel seguente file: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Questo file non può essere considerato un’unica fonte di verità. In caso di dubbi, consulta i siti web ufficiali dei fornitori di queste tecnologie.

## Informazioni aggiuntive

[Requisiti di sistema](../../../installation/system-requirements.md)
