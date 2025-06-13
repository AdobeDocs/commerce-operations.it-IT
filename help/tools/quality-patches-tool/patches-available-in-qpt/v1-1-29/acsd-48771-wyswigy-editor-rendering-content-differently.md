---
title: 'ACSD-48771: l’editor di WYSIWYG esegue il rendering del contenuto in modo diverso'
description: Applica la patch ACSD-48771 per risolvere il problema di Adobe Commerce, in cui l’editor WYSIWYG esegue il rendering del contenuto in modo diverso.
feature: Cache, Page Content
role: Admin
exl-id: 9480af54-800b-4802-b1a3-65d1a6e169ec
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-48771: l’editor di WYSIWYG esegue il rendering del contenuto in modo diverso

La patch ACSD-48771 risolve il problema in cui l’editor WYSIWYG esegue il rendering del contenuto in modo diverso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-48771. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’editor di WYSIWYG esegue il rendering del contenuto in modo diverso.

<u>Passaggi da riprodurre</u>:

1. Vai all’amministratore di Adobe Commerce, crea una nuova pagina con una riga con tre colonne e salva la pagina.
1. Aggiorna Adobe Commerce a una delle versioni più recenti.
1. Impostare il browser [!DNL Chrome] per disabilitare la cache e la velocità su *Fast 3G*.
1. Passa nuovamente alla pagina di modifica e la aggiorna fino a quando le colonne non diventano righe.
1. Salvare la pagina mentre le colonne sono in righe.

<u>Risultati previsti</u>:

Il generatore di pagine Amministratore non deve visualizzare colonne nelle righe.

<u>Risultati effettivi</u>:

Le colonne vengono visualizzate in righe diverse.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
