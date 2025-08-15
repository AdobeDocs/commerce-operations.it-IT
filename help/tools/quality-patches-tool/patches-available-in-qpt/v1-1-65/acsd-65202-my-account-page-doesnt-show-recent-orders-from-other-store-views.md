---
title: 'ACSD-65202: la pagina Il mio account non mostra gli ordini recenti provenienti da altre visualizzazioni del negozio'
description: Applica la patch ACSD-65202 per risolvere il problema Adobe Commerce, in cui nella pagina Il mio account non vengono visualizzati gli ordini recenti provenienti da altre visualizzazioni dello stesso store.
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-65202: la pagina [!UICONTROL My Account] non mostra gli ordini recenti da altre visualizzazioni dello store

La patch ACSD-65202 risolve il problema che impedisce alla pagina **[!UICONTROL My Account]** di visualizzare gli ordini recenti provenienti da altre visualizzazioni dello stesso store. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-65202. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p12

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si passa alla pagina dell&#39;account cliente (sezione **[!UICONTROL My Account]**), non vengono visualizzati gli ordini recenti inseriti in un&#39;altra visualizzazione dello store. Tuttavia, quando si passa alla cronologia degli ordini (sezione *[!UICONTROL My Orders]*), vengono visualizzati tutti gli ordini in entrambe le visualizzazioni dello store.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Nel pannello *Amministratore*, crea una nuova visualizzazione archivio e immetti il relativo codice come, *secondo*, per identificare la visualizzazione.
1. Crea un prodotto semplice e reindicizza.
1. Creare un account cliente e inserire un ordine nella visualizzazione predefinita dello store il cui codice è *default*.
1. Vai alla pagina **[!UICONTROL My Orders]** e controlla che l&#39;ordine sia visibile in entrambe le visualizzazioni dello store, ad esempio:
1. Predefinito: https://localhost/pub/default/sales/order/history/
1. Secondo: https://localhost/pub/second/sales/order/history/

1. Vai alla pagina **[!UICONTROL My Account]** in entrambe le visualizzazioni dello store:
1. Predefinito: https://localhost/pub/default/customer/account/
1. Secondo: https://localhost/pub/second/customer/account/

<u>Risultati previsti</u>:

Nella pagina Ordini è possibile visualizzare gli ordini di entrambe le visualizzazioni del punto vendita. È lo stesso negozio, ma con una visualizzazione diversa.

<u>Risultati effettivi</u>:

Il comportamento è incoerente. Gli ordini non vengono visualizzati nella seconda visualizzazione dello store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
