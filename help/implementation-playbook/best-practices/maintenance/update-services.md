---
title: Procedure consigliate per i servizi di aggiornamento
description: Scopri come mantenere aggiornato lo stack tecnologico di Adobe Systems Commerce su infrastruttura cloud.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Procedure consigliate per i servizi di aggiornamento

Questo articolo fornisce consigli per mantenere aggiornato lo stack tecnologico di Adobe Systems Commerce su infrastruttura cloud e fornisce collegamenti a risorse utili.

## Prodotti e versioni interessati

Adobe Systems Commerce su infrastruttura cloud 2.4.x e versioni successive

## Servizi di aggiornamento

Aggiorna i servizi e i componenti utilizzati da Adobe Systems Commerce prima che raggiungano o siano vicini alla data di fine del ciclo di vita. Ciò consente di tenere il passo con la conformità PCI e ridurre le vulnerabilità della sicurezza.

I clienti con piani Starter possono usufruire autonomamente degli aggiornamenti dei servizi. Fare riferimento a [Modificare la versione](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) del servizio per informazioni dettagliate su come eseguire questa operazione.

I clienti con piani Pro possono gestire autonomamente solo gli aggiornamenti dei servizi nel loro [ambiente](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html) di integrazione. Per gli aggiornamenti dei servizi in Produzione, è necessario [inviare un ticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) di supporto per richiedere l&#39;aggiornamento.

>[!WARNING]
>
>Gli aggiornamenti del servizio non possono essere inviati all&#39;ambiente di produzione senza un preavviso di 48 ore lavorative all&#39;team dell&#39;infrastruttura. Ciò è necessario in quanto dobbiamo assicurarci di avere un tecnico di supporto dell&#39;infrastruttura disponibile per aggiornare la configurazione entro un arco temporale desiderato con tempi di inattività minimi per l&#39;ambiente di produzione.

È possibile visualizzare l&#39;elenco delle versioni del servizio e delle date di fine del ciclo di vita nel seguente file: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Questo file non può essere considerato un&#39;unica fonte di verità. In caso di dubbio, fare riferimento ai siti Web ufficiali dei fornitori per queste tecnologie.

## Informazioni aggiuntive

[requisiti di sistema](../../../installation/system-requirements.md)
