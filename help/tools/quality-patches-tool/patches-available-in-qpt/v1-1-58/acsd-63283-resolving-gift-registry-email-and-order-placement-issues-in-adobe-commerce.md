---
title: 'ACSD-63283: risoluzione di [!UICONTROL Gift Registry] problemi di invio di e-mail e ordini in Adobe Commerce'
description: Applicare la patch ACSD-63283 per risolvere il problema Adobe Commerce per cui l'ordinamento di elementi da [!UICONTROL Gift Registry] causa un'eccezione e assicura che [!UICONTROL Gift Registry Updates] includa solo gli elementi corretti.
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283: risoluzione di [!UICONTROL Gift Registry] problemi di invio di e-mail e ordini in Adobe Commerce

La patch ACSD-63283 risolve il problema per cui l&#39;ordinamento di elementi da [!UICONTROL Gift Registry] causa un&#39;eccezione e assicura che [!UICONTROL Gift Registry Updates] includa solo gli elementi corretti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63283. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

>[!NOTE]
>Questa patch sostituisce ed estende la patch [ACSD-56280](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La funzionalità [!UICONTROL Gift Registry] in Adobe Commerce è interessata da due problemi significativi:

* Quando un cliente ordina articoli dal proprio [!UICONTROL Gift Registry], il processo non riesce a causa di un&#39;eccezione attivata.
* Inoltre, l&#39;e-mail [!UICONTROL Gift Registry Updates] inviata al proprietario del Registro di sistema include erroneamente gli elementi di tutti i registri delle donazioni, anziché limitare gli aggiornamenti agli elementi del Registro di sistema specifico in fase di aggiornamento.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti: Prodotto A e Prodotto B.
1. Creare due clienti: Cliente A e Cliente B.
1. Accedi come cliente A e crea un nuovo [!UICONTROL Gift Registry].
1. Passare alla pagina del prodotto A e aggiungerla a [!UICONTROL Wishlist]. Aprire [!UICONTROL Wishlist Page] e spostare il prodotto A in [!UICONTROL Gift Registry] utilizzando [!UICONTROL Add to Gift Registry].
1. Accedi come cliente B, crea un nuovo [!UICONTROL Gift Registry] e aggiungi il prodotto B.
1. Come cliente B, condividi [!UICONTROL Gift Registry] tramite e-mail: **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**.
1. Esci come cliente B.
1. Fai clic sul collegamento ricevuto nell’e-mail. Aggiungere il prodotto B a [!UICONTROL Cart] e ordinare.

<u>Risultati previsti</u>:

Il cliente B riceve l&#39;e-mail con gli elementi aggiornati solo dal proprio registro regali.

<u>Risultati effettivi</u>:

Il cliente B riceve l&#39;e-mail con gli articoli da tutti i registri dei regali.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
