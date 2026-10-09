---
title: 'ACSD-50849: l’aggiunta di un nuovo prodotto dopo aver cancellato la cache causa una mancata corrispondenza'
description: Applica la patch ACSD-50849 per risolvere il problema di Adobe Commerce, in cui l’aggiunta di un nuovo prodotto alla categoria dopo la cancellazione della cache determina una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti.
feature: Cache, Categories, Products
role: Admin
exl-id: e7fd0614-eaa3-48ad-95ff-87f7ad3d76c1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%
---
# ACSD-50849: l’aggiunta di un nuovo prodotto dopo aver cancellato la cache causa una mancata corrispondenza

La patch ACSD-50849 risolve il problema che, quando si aggiunge un nuovo prodotto alla categoria dopo aver cancellato la cache, si verifica una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) QPT 1.1.32. L’ID della patch è ACSD-50849. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aggiunta di un nuovo prodotto alla categoria dopo la cancellazione della cache determina una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti.
1. Assegna un prodotto a una categoria.
1. Apri la categoria dall’amministratore.
1. Pulire la cache `bin/magento cache:flush`.
1. Aggiungi il secondo prodotto alla categoria.

<u>Risultati previsti</u>:

I prodotti esistenti assegnati alla categoria non vengono rimossi automaticamente.

<u>Risultati effettivi</u>:

Il primo prodotto (esistente) viene rimosso automaticamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
