---
title: 'ACSD-50336: e-mail di avviso sul prodotto non inviate'
description: Applica la patch ACSD-50336 per risolvere il problema di Adobe Commerce, in cui le e-mail di avviso sul prodotto non vengono inviate quando un prodotto è di nuovo disponibile o il prezzo viene modificato.
feature: Communications, Personalization, Products
role: Admin
exl-id: 45dd12af-a3b2-4cfa-be90-af1c7b5f74b3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%
---
# ACSD-50336: e-mail di avviso sul prodotto non inviate

La patch ACSD-50336 risolve il problema che impedisce l&#39;invio delle e-mail di avviso sui prodotti quando un prodotto è di nuovo disponibile o quando il prezzo viene modificato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-50336. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail di avviso sul prodotto non vengono inviate quando un prodotto è di nuovo in magazzino o il prezzo viene modificato.

<u>Prerequisiti</u>:

Imposta avvisi sui prodotti per quando un prodotto viene reinserito nell&#39;archivio.

<u>Passaggi da riprodurre</u>:

1. Accedi come cliente sulla vetrina.
1. Apri un prodotto non disponibile.
1. Iscriviti per ricevere una notifica quando il prodotto è *di nuovo disponibile*.
1. Aggiorna il prodotto da [!UICONTROL Admin] affinché sia _di nuovo disponibile_.

<u>Risultati previsti</u>:

Al cliente viene inviata una notifica e-mail sul prodotto *di nuovo in magazzino*.

<u>Risultati effettivi</u>:

Il cliente non riceve alcuna notifica e-mail sul prodotto *di nuovo disponibile*. Nel registro viene visualizzato il seguente errore:

```text
report. CRITICAL: Magento\ProductAlert\Model\Mailing\ErrorEmailSender::execute(): Argument #2 ($storeId) must be of type int, string given, called in vendor/magento/module-product-alert/Model/Mailing/AlertProcessor.php on line 130 [] []
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
