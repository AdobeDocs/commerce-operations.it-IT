---
title: 'ACSD-61348: voci della lista dei desideri visibili tramite GraphQL ma non nella vetrina'
description: Applica la patch ACSD-61348 per risolvere il problema Adobe Commerce, in cui le voci della lista dei desideri sono visibili tramite GraphQL ma non nella vetrina in un ambiente multisito.
feature: Customers
role: Admin, Developer
source-git-commit: b3dcce33b5710cd3c4b835f5fc7fd8f16cdc6a7f
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: voci della lista dei desideri visibili tramite GraphQL ma non nella vetrina

La patch ACSD-61348 risolve il problema se le voci della lista dei desideri sono visibili tramite GraphQL ma non nella vetrina in un ambiente multi-sito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-61348. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli elementi della lista dei desideri sono visibili tramite GraphQL ma non nella vetrina in un ambiente multi-sito.

<u>Passaggi da riprodurre</u>:

1. Configura due siti web.
1. Vai a **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** e imposta **[!UICONTROL Share Customer Accounts]** su *[!UICONTROL Global]*.
1. Vai a **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** e imposta **[!UICONTROL Enable Multiple Wish Lists]** su *Sì*.
1. Vai a **[!UICONTROL Config General]** > **[!UICONTROL Web]** e imposta **[!UICONTROL Add Store Code to URLs]** su *Sì*.
1. Crea un prodotto semplice e assegnalo al secondo sito web.
1. Crea un cliente e accedi.
1. Aggiungere un prodotto alla lista dei desideri.
1. Assegna il prodotto al sito Web predefinito.
1. Passare alla pagina *[!UICONTROL Wishlist]* del sito Web predefinito.

<u>Risultati previsti</u>:

Il prodotto è sulla lista dei desideri.

<u>Risultati effettivi</u>:

Non ci sono prodotti nella lista dei desideri.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
