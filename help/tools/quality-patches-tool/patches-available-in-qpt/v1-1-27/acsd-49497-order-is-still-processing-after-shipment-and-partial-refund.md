---
title: 'ACSD-49497: elaborazione dell''ordine ancora in corso dopo la spedizione e rimborso parziale'
description: Applicare la patch ACSD-49497 per risolvere il problema Adobe Commerce, in cui lo stato dell'ordine rimane elaborazione dopo la spedizione e viene applicato un rimborso parziale.
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
exl-id: e2e3d2b3-24be-4827-a735-aebfc6f475ea
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49497: elaborazione dell&#39;ordine ancora in corso dopo la spedizione e rimborso parziale

La patch di ACSD-49497 risolve il problema in cui lo stato dell&#39;ordine rimane in elaborazione dopo la spedizione e viene applicato un rimborso parziale. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27. L’ID della patch è ACSD-49497. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato di un nuovo ordine rimane nello stato *[!UICONTROL Processing]* anche dopo la spedizione e viene applicato un rimborso parziale.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con più elementi.
1. Da **[!UICONTROL Admin]**, creare una fattura per l&#39;ordine.
1. Da **[!UICONTROL Admin]**, creare una nota di credito e rimborsare un articolo solo parzialmente.
1. Da **[!UICONTROL Admin]**, richiedere la spedizione per gli articoli rimanenti nell&#39;ordine.
1. Osserva lo stato dell’ordine.

<u>Risultati previsti</u>:

Lo stato dell&#39;ordine deve essere *[!UICONTROL Complete]*.

<u>Risultati effettivi</u>:

Lo stato dell&#39;ordine rimane *[!UICONTROL Processing]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
