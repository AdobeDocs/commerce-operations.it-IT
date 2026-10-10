---
title: 'ACSD-47179: l’eliminazione di massa delle recensioni dei prodotti non funziona se si accede come ruolo utente limitato'
description: Applica la patch ACSD-47179 per risolvere il problema di Adobe Commerce, in cui l’eliminazione di massa delle revisioni dei prodotti non funziona quando si accede come ruolo utente limitato.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%
---
# ACSD-47179: l’eliminazione di massa delle recensioni dei prodotti non funziona se si accede come ruolo utente limitato

La patch ACSD-47179 risolve il problema dell’eliminazione di massa delle revisioni dei prodotti quando si accede come ruolo utente limitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.23. L’ID della patch è ACSD-47179. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’eliminazione di massa delle revisioni dei prodotti non funziona se si accede come ruolo utente limitato.

<u>Passaggi da riprodurre</u>:

1. Crea un sito Web secondario.
1. Crea un ruolo utente limitato al sito Web secondario con autorizzazioni complete per le sezioni seguenti:
   * Catalogo
   * Cliente
   * Marketing
1. Crea un prodotto e assegnalo al sito web secondario.
1. Aggiungi due recensioni al prodotto dal front-end.
1. Accedere all&#39;amministratore [!DNL Commerce] utilizzando l&#39;utente amministratore con restrizioni appena creato.
1. Prova a eliminare in massa le recensioni in sospeso.

<u>Risultati previsti</u>:

Un amministratore con autorizzazioni sufficienti è in grado di eliminare in massa le revisioni in sospeso.

<u>Risultati effettivi</u>:

Si è verificato il seguente errore: _Si è verificato un errore. Eccezione generata in support_ report.log_

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
