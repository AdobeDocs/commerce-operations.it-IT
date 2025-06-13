---
title: 'ACSD-50367: l’esportazione dell’indirizzo del cliente non funziona con l’attributo a selezione multipla'
description: Applica la patch ACSD-50367 per risolvere il problema di Adobe Commerce per cui l’esportazione dell’indirizzo del cliente non funziona quando viene creato un attributo **&grave;Indirizzo del cliente&grave;** a selezione multipla senza valori.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367: l’esportazione dell’indirizzo del cliente non funziona

La patch ACSD-50367 risolve il problema che impedisce il funzionamento dell&#39;esportazione dell&#39;indirizzo del cliente quando viene creato un attributo **`Customer Address`** a selezione multipla senza valori. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. L’ID della patch è ACSD-50367. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;esportazione dell&#39;indirizzo del cliente non funziona quando viene creato un attributo **`Customer Address`** a selezione multipla senza valori.

<u>Prerequisiti</u>:

Crea un cliente con un indirizzo.

<u>Passaggi da riprodurre</u>:

1. Creare un attributo **`Customer Address`** a selezione multipla in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]**.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** e seleziona il tipo di entità **`Customer Address`**.
1. Esporta gli indirizzi dei clienti. Vedrai che non viene esportato nulla.
1. Eliminare l&#39;attributo **`Customer Address`** a selezione multipla ed esportare di nuovo gli indirizzi dei clienti. Questa volta viene generato il file CSV degli indirizzi.

<u>Risultati previsti</u>:

Gli indirizzi dei clienti possono essere esportati come file CSV quando viene creato un attributo **`Customer Address`** a selezione multipla.

<u>Risultati effettivi</u>:

Gli indirizzi dei clienti non possono essere esportati come file CSV quando viene creato un attributo **`Customer Address`** a selezione multipla.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
