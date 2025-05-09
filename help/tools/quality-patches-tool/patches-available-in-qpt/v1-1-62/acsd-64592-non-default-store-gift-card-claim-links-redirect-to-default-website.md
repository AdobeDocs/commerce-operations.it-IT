---
title: 'ACSD-64592: collegamenti di richiesta di rimborso non predefiniti per gift card del negozio reindirizzati al sito Web predefinito'
description: Applica la patch ACSD-64592 per risolvere il problema in cui, in una configurazione multi-sito, quando una Gift Card virtuale viene acquistata dal sito web secondario (non predefinito), il collegamento Codice gift card nell’e-mail ha l’URL predefinito del sito web.
feature: Gift, Products
role: Admin, Developer
source-git-commit: 39866e1cf8f2afd892c9e151259a446d0277d58f
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# ACSD-64592: collegamenti di richiesta di rimborso non predefiniti per gift card del negozio reindirizzati al sito Web predefinito

La patch ACSD-64592 risolve un problema in cui, in un ambiente multisito, se una gift card virtuale viene acquistata da un sito web secondario (non primario), l’e-mail contenente il collegamento Codice gift card indirizzerà gli utenti all’URL del sito web predefinito. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

In una configurazione multi-sito, quando una gift card virtuale viene acquistata da un sito secondario (non predefinito), l’e-mail contenente il collegamento Codice gift card indirizza gli utenti all’URL del sito web predefinito.

<u>Passaggi da riprodurre</u>:

1. Crea una visualizzazione secondaria per sito Web, store e store.
1. Configurare URL di base diversi per il sito Web di base e secondario.
1. Crea una gift card virtuale con alcune opzioni di importo.
1. Generare un nuovo pool di codici in **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**.
1. Effettuare un ordine con il prodotto Gift Card sul sito secondario.
1. Fattura l&#39;ordine nell&#39;amministratore Commerce.
1. Controlla l&#39;URL nel collegamento Codice gift card di *Ti è stato inviato un regalo dall&#39;e-mail di Two*.

<u>Risultati previsti</u>:

Il collegamento Codice gift card deve contenere il collegamento al secondo sito Web.

<u>Risultati effettivi</u>:

Il collegamento Codice gift card presenta l’URL predefinito del sito web, anche se l’ordine viene effettuato sul secondo sito web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:
* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
