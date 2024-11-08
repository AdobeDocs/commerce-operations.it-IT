---
title: Best practice per aggiornare i servizi
description: Scopri come mantenere aggiornato lo stack di tecnologia Adobe Commerce su infrastruttura cloud.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Best practice per aggiornare i servizi

Questo articolo fornisce consigli per mantenere aggiornato lo stack di tecnologia Adobe Commerce on cloud infrastructure e fornisce collegamenti a risorse utili.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.x e versioni successive

## Aggiorna servizi

Aggiorna i servizi e i componenti utilizzati da Adobe Commerce prima che raggiungano o siano prossimi alla data di fine del ciclo di vita. Questo consente di mantenere il passo con la conformità PCI e ridurre le vulnerabilità di sicurezza.

I clienti che utilizzano i piani Starter possono eseguire autonomamente gli aggiornamenti dei servizi. Per ulteriori informazioni su come eseguire questa operazione, consultare [Modifica versione del servizio](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version).

I clienti con piani Pro possono eseguire il self-service solo sugli aggiornamenti dei servizi nel proprio [ambiente di integrazione](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Per gli aggiornamenti dei servizi in produzione, è necessario [inviare un ticket di supporto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) richiedendo l&#39;aggiornamento.

>[!WARNING]
>
>Gli aggiornamenti dei servizi non possono essere inviati a un ambiente di produzione senza un preavviso di 48 ore lavorative al team dell&#39;infrastruttura Adobe. Questo è necessario affinché Adobe possa garantire la disponibilità di un tecnico del supporto dell’infrastruttura per aggiornare la configurazione entro l’intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell’ambiente di produzione. Adobe consiglia di attivare la modalità di manutenzione del sito durante l’aggiornamento del servizio.

È possibile visualizzare l&#39;elenco delle versioni del servizio e delle date di fine del ciclo di vita nel seguente file: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Questo file non può essere considerato un’unica fonte di verità. In caso di dubbi, consulta i siti web ufficiali dei fornitori di queste tecnologie.

## Informazioni aggiuntive

[Requisiti di sistema](../../../installation/system-requirements.md)
