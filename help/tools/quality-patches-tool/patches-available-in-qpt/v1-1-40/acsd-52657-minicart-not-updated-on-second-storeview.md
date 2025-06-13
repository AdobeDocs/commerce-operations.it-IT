---
title: 'ACSD-52657: Minicart non aggiornato nel secondo storeview che utilizza il sottodominio'
description: Applica la patch ACSD-52657 per risolvere il problema Adobe Commerce, se il minicart non viene aggiornato nella seconda visualizzazione store che utilizza un sottodominio.
feature: Shopping Cart
role: Admin, Developer
exl-id: feec9dde-5532-481b-9410-7f6be9df4be7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52657: Minicart non aggiornato nel secondo storeview che utilizza il sottodominio

La patch ACSD-52657 risolve il problema se il minicart non viene aggiornato nella seconda visualizzazione store che utilizza un sottodominio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. L’ID della patch è ACSD-52657. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Minicart non viene aggiornato nella visualizzazione archivio secondaria che utilizza un sottodominio.

<u>Passaggi da riprodurre</u>:

1. Crea un secondo storeview e configura un sottodominio per l’URL di base.
1. Aggiorna il dominio dei cookie in modo che abbia il dominio comune.
1. Nel negozio principale, aggiungi un prodotto al carrello.
1. Aggiorna la seconda visualizzazione dello store, quindi vai alla pagina del carrello.

<u>Risultati previsti</u>:

Il carrello e il minicart vengono aggiornati nel sottodominio.

<u>Risultati effettivi</u>:

Il minicart non viene aggiornato quando si aggiorna l&#39;archivio secondario, ma la pagina del carrello mostra il prodotto aggiunto ed è possibile effettuare un ordine nella sessione (`PHPSESSID` cookie è condiviso).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
