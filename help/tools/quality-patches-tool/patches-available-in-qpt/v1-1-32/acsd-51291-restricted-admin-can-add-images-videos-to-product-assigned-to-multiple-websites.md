---
title: 'ACSD-51291: l’amministratore con restrizioni può aggiungere immagini/video a prodotti assegnati a più siti web'
description: Applica la patch ACSD-51291 per risolvere il problema di Adobe Commerce, in cui un amministratore con restrizioni di accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-51291: l’amministratore con restrizioni può aggiungere immagini/video a prodotti assegnati a più siti web

La patch ACSD-51291 risolve il problema per cui un amministratore con restrizioni con accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-51291. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un amministratore con restrizioni di accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web.

<u>Passaggi da riprodurre</u>

1. Accedi come amministratore.
1. Crea un secondo sito Web, store e visualizzazione store.
1. Crea un secondo ruolo di amministratore con risorse solo per il secondo sito Web, store e visualizzazione store.
1. Crea un secondo amministratore e assegnalo al nuovo ruolo di amministratore con restrizioni.
1. Crea un nuovo prodotto e assegnalo ai siti Web predefiniti e nuovi.
1. Esci dal profilo di amministrazione principale.
1. Accedi come nuovo amministratore con restrizioni.
1. Modifica il prodotto creato, che è stato assegnato a entrambi i siti web.
1. Apri la scheda **[!UICONTROL Images and Videos]**.

<u>Risultati previsti</u>:

* Viene visualizzato il seguente messaggio:

  *L&#39;amministratore con restrizioni può eseguire azioni con immagini o video solo quando dispone dei diritti per tutti i siti Web a cui è assegnato il prodotto.*

* Il pulsante **[!UICONTROL Add Video]** non è attivo.

<u>Risultati effettivi</u>:

L’amministratore con restrizioni può aggiungere immagini e video anche quando il prodotto viene assegnato a un sito web a cui non ha accesso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
