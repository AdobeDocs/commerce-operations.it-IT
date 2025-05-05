---
title: "ACSD-48661: problema di convalida del separatore virgola del limite di credito della società"
description: Applica la patch ACSD-48661 per risolvere il problema Adobe Commerce, in cui quando il limite di credito della società è superiore a 999, il separatore di virgola impedisce il salvataggio della società a causa di un errore di convalida.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48661: problema di convalida del separatore virgola del limite di credito della società

La patch ACSD-48661 risolve il problema se, quando il limite di credito dell’azienda è maggiore di 999, il separatore di virgola impedisce il salvataggio dell’azienda a causa di un errore di convalida. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26. L’ID della patch è ACSD-48661. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Systems Commerce (tutti i metodi di distribuzione) 2.4.5-p1

**Compatibile con le versioni Adobe Systems Commerce:**

* Adobe Systems Commerce (tutti i metodi di distribuzione) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando il limite di credito della società è superiore a 999, il separatore virgola impedisce il salvataggio della società a causa di un errore di convalida.

<u>Passaggi da riprodurre</u>:

1. Abilita la funzionalità aziendale in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Creare una società e aggiungere un limite di credito maggiore di 999 nella scheda **[!UICONTROL Company Credit]**.
1. Salva l&#39;azienda.
1. Modifica l&#39;azienda e prova a salvarla di nuovo.

<u>Risultati attesi</u>:

Sei in grado di salvare l&#39;azienda senza fissare il limite di credito. La virgola non è supportata per i campi di input per importi e prezzi.

<u>Risultati effettivi</u>:

Impossibile salvare la società a causa di un errore di convalida nel campo *[!UICONTROL Credit Limit]*. Adobe Commerce aggiunge automaticamente i separatori virgola per i limiti di credito anche se il campo [!UICONTROL Credit Limit] non accetta virgole.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Letture correlate

Per ulteriori informazioni , [!DNL Quality Patches Tool]consulta:

* [[!DNL Quality Patches Tool] Rilasciato: una nuova strumento di patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) di qualità self-service nel knowledge base di supporto.
* [Controlla se la patch è disponibile per il tuo problema di Adobe Systems Commerce utilizzando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) la [!UICONTROL Quality Patches Tool] guida.


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
