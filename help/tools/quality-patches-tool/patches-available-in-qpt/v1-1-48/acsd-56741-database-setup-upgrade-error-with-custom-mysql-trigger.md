---
title: 'ACSD-56741: Risoluzione dei problemi di installazione del database con trigger MySQL personalizzati'
description: Applica la patch ACSD-56741 per risolvere il problema di Adobe Commerce, dove viene visualizzato un messaggio di errore *Tentativo di accedere all’offset dell’array con valore di tipo null* durante "setup:upgrade" a causa di un trigger MySQL personalizzato nel database non correlato all’indicizzazione e a [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%
---
# ACSD-56741: Risoluzione dei problemi di installazione del database con trigger MySQL personalizzati

La patch ACSD-56741 risolve il problema che causava la visualizzazione di un messaggio di errore *Il tentativo di accedere all&#39;offset dell&#39;array sul valore di tipo null* durante `setup:upgrade` a causa di un trigger MySQL personalizzato nel database non correlato all&#39;indicizzazione e [!DNL MView]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-56741. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un messaggio di errore *Il tentativo di accedere all&#39;offset dell&#39;array sul valore di tipo null* è stato visualizzato durante `setup:upgrade` a causa di un trigger MySQL personalizzato nel database non correlato all&#39;indicizzazione e a [!DNL MView].

<u>Passaggi da riprodurre</u>:

1. Esegui `php bin/magento indexer:set-mode schedule`.

   ```text
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Esegui `php bin/magento c:f`.
1. Esegui `php bin/magento setup:upgrade`.

<u>Risultati previsti</u>:

L&#39;aggiornamento della configurazione termina senza errori.

<u>Risultati effettivi</u>:

L&#39;aggiornamento dell&#39;installazione termina con un messaggio di errore:

*Avviso: tentativo di accesso all&#39;offset della matrice su un valore di tipo null*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
