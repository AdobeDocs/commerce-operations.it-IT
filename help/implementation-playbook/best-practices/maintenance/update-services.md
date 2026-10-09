---
title: Best practice per aggiornare i servizi
description: Scopri come mantenere aggiornato lo stack di tecnologia Adobe Commerce su infrastruttura cloud.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%
---
# Best practice per aggiornare i servizi

Questo articolo fornisce consigli per mantenere aggiornato lo stack di tecnologia Adobe Commerce on cloud infrastructure e fornisce collegamenti a risorse utili.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud 2.4.x e versioni successive

## Aggiorna servizi

Aggiorna i servizi e i componenti utilizzati da Adobe Commerce prima che raggiungano o siano prossimi alla data di fine del ciclo di vita. Questo consente di mantenere il passo con la conformità PCI e ridurre le vulnerabilità di sicurezza.

I clienti che utilizzano i piani Starter possono eseguire autonomamente gli aggiornamenti dei servizi. Per ulteriori informazioni su come eseguire questa operazione, consultare [Modifica versione del servizio](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/service/services-yaml#change-service-version).

I clienti con piani Pro possono eseguire il self-service solo sugli aggiornamenti dei servizi nel proprio [ambiente di integrazione](https://experienceleague.adobe.com/it/docs/experience-cloud-kcs/kbarticles/ka-27242). Per gli aggiornamenti dei servizi in produzione, è necessario [inviare un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) richiedendo l&#39;aggiornamento.

>[!WARNING]
>
>Gli aggiornamenti dei servizi non possono essere inviati a un ambiente di produzione senza un preavviso di 48 ore lavorative al team dell&#39;infrastruttura Adobe. Ciò è necessario affinché Adobe possa garantire la disponibilità di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Adobe consiglia di attivare la modalità di manutenzione del sito durante l’aggiornamento del servizio.

È possibile visualizzare l&#39;elenco delle versioni del servizio e delle date di fine del ciclo di vita nel seguente file: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Questo file non può essere considerato un’unica fonte di verità. In caso di dubbi, consulta i siti web ufficiali dei fornitori di queste tecnologie.

## Informazioni aggiuntive

[Requisiti di sistema](../../../installation/system-requirements.md)
