---
title: 'ACSD-58383: note di credito duplicate da richieste di rimborso simultanee tramite  [!DNL REST API]'
description: Applicare la patch ACSD-58383 per risolvere il problema Adobe Commerce in cui l'emissione di un rimborso tramite il [!DNL REST API] con due richieste identiche eseguite contemporaneamente, crea note di credito duplicate.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: d3d98c04afe32d80cdf985b1d93c8a2cb57236ed
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-58383: note di credito duplicate da richieste di rimborso simultanee tramite [!DNL REST API]

La patch ACSD-58383 risolve il problema che, emettendo un rimborso tramite [!DNL REST API] con due richieste identiche eseguite contemporaneamente, genera note di credito duplicate.

Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-58383. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le note di credito duplicate derivano da due rimborsi creati contemporaneamente.

<u>Passaggi da riprodurre</u>:

1. Configurare [!DNL Paypal Express] in Commerce [!UICONTROL Admin].
1. Imposta azione di pagamento su *Vendita*.
1. Configurare l&#39;IPN [!DNL PayPal] (Instant Payment Notification) sul sito Web Sandbox [!DNL PayPal].
1. Emetti il rimborso sul sito Web Sandbox [!DNL PayPal].
1. Emulare un messaggio IPN da [!DNL PayPal] utilizzando gli strumenti per sviluppatori. IPN deve creare una nota di credito.
1. Creare una seconda nota di credito utilizzando una chiamata [!DNL API].

<u>Risultati previsti</u>:

Viene creata una sola nota di credito per lo stesso articolo.


<u>Risultati effettivi</u>:

Per lo stesso articolo vengono create due note di credito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
