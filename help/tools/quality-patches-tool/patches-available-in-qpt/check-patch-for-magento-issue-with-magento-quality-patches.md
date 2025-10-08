---
title: Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches
description: Questo articolo fornisce una panoramica dello strumento Quality Patches (QPT) e collegamenti alle risorse che spiegano come utilizzarlo.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Verifica la patch per il problema Adobe Commerce con lo strumento Quality Patches

Questo articolo fornisce una panoramica dello strumento Quality Patches (QPT) e collegamenti alle risorse che spiegano come utilizzarlo.

## Prodotti e versioni interessati

* Adobe Commerce on-premise, tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Che cosa sono le patch di qualità

Lo [strumento Patch di qualità](https://github.com/magento/quality-patches) (QPT) è costituito da singole patch sviluppate da Adobe e dalla community Magento Open Source.

Consente di:

* applicare le patch di qualità incluse nella confezione
* ripristinare le patch applicate in precedenza
* visualizzare le informazioni generali sulle patch di qualità disponibili per la versione installata di Adobe Commerce.

Di seguito è riportato un esempio della tabella di stato che consente di visualizzare le patch disponibili:

![Tabella di stato dello strumento Patch di qualità che mostra le patch disponibili e il relativo stato di installazione](/help/assets/tools/status_table.png)

Lo strumento ha lo scopo di consentire l’utilizzo autonomo di patch per problemi che potresti riscontrare con Adobe Commerce o di applicare facilmente patch suggerite dal supporto Adobe Commerce.

>[!NOTE]
>
>QPT è solo per patch di qualità. Le patch di sicurezza sono disponibili in [Centro sicurezza PC Magento](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## Patch disponibili nello strumento Patch di qualità

Per un elenco delle patch disponibili, consultare [Strumento Patch di qualità](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.

## Come installare e utilizzare lo strumento Quality Patches

I comandi di installazione e utilizzo sono diversi per Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud, perché per il cloud il pacchetto QPT è incluso nel pacchetto degli strumenti ece.

### Come installare e utilizzare QPT per Adobe Commerce on-premise

Per informazioni dettagliate su come installare e utilizzare il QPT per l&#39;applicazione e il ripristino delle patch, consultare la [Guida all&#39;aggiornamento software > Applicazione delle patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.

### Come installare e utilizzare QPT per Adobe Commerce sull’infrastruttura cloud

Consulta [Cloud for Adobe Commerce > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori per informazioni dettagliate su come installare e utilizzare QPT per applicare e ripristinare le patch su Adobe Commerce nell&#39;infrastruttura cloud.

## Lettura correlata

* [Note sulla versione dello strumento Patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes) nella documentazione per gli sviluppatori.
* [Applicare le patch del compositore fornite da Adobe](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento) nella Knowledge Base di supporto.
