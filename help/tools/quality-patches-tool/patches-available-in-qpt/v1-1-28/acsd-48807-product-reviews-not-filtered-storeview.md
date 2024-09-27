---
title: "ACSD-48807: recensioni dei prodotti non filtrate per storeview"
description: Applica la patch ACSD-48807 per risolvere il problema di Adobe Commerce per cui le recensioni dei prodotti non vengono filtrate dalla visualizzazione dello store tramite GraphQL.
feature: Admin Workspace, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-48807: recensioni dei prodotti non filtrate per storeview

La patch ACSD-48807 risolve il problema per cui le recensioni dei prodotti non vengono filtrate tramite storeview tramite GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. L’ID della patch è ACSD-48807. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le recensioni dei prodotti non vengono filtrate dalla visualizzazione dello store tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;ulteriore visualizzazione dello store.
1. Crea un account cliente e accedi.
1. Nella visualizzazione predefinita dello store, crea una revisione per un prodotto.
1. Passa a un’altra visualizzazione dello store e crea un’altra revisione per un prodotto.
1. Approva entrambe le recensioni in Adobe Commerce Admin.
1. Invia una query GraphQL del cliente per recuperare le recensioni dei prodotti specificando la visualizzazione dello store creata al passaggio 1 nell’intestazione.
1. Osserva la risposta.

<u>Risultati previsti</u>:

Nella risposta viene restituita solo la recensione del prodotto per la visualizzazione dello store specificata.

<u>Risultati effettivi</u>:

Entrambe le recensioni sono restituite nella risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
