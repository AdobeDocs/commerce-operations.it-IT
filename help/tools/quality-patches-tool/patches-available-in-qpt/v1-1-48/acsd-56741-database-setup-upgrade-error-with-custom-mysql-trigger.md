---
title: 'ACSD-56741: Risoluzione dei problemi di installazione del database con trigger MySQL personalizzati'
description: Applica la patch ACSD-56741 per risolvere il problema di Adobe Commerce, dove un messaggio di errore *Tentativo di accedere all’offset dell’array sul valore di tipo null* viene visualizzato durante "setup:upgrade" a causa di un trigger MySQL personalizzato nel database non correlato all’indicizzazione e  [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741: Risoluzione dei problemi di installazione del database con trigger MySQL personalizzati

La patch ACSD-56741 risolve il problema che causava la visualizzazione di un messaggio di errore *Il tentativo di accedere all&#39;offset dell&#39;array sul valore di tipo null* durante `setup:upgrade` a causa di un trigger MySQL personalizzato nel database non correlato all&#39;indicizzazione e [!DNL MView]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. L’ID della patch è ACSD-56741. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0

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

   ```
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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
