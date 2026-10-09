---
title: 'ACSD-66233: gli amministratori non possono aggiungere prodotti a causa di una finestra a comparsa dell’elenco di prodotti che non risponde'
description: Applica la patch ACSD-66233 per risolvere il problema di Adobe Commerce, a causa del quale gli amministratori non possono aggiungere prodotti alle categorie perché la finestra a comparsa [!UICONTROL Add Product] in Visual Merchandiser viene caricata per un tempo indefinito.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
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
source-wordcount: '377'
ht-degree: 0%
---
# ACSD-66233: gli amministratori non possono aggiungere prodotti a causa di una finestra a comparsa dell’elenco di prodotti che non risponde

La patch ACSD-66233 risolve un problema che impediva agli amministratori di aggiungere prodotti alle categorie a causa del caricamento indefinito della finestra a comparsa [!UICONTROL Add Product] in Visual Merchandiser. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66233. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problema relativo al caricamento indefinito della finestra a comparsa [!UICONTROL Add Product] in Visual Merchandiser, che impedisce agli amministratori di aggiungere prodotti alle categorie.

<u>Passaggi da riprodurre</u>:

1. Installa e abilita i moduli inventario.
1. Creare un numero elevato di origini inventario (ad esempio, 700).
1. Creare più scorte di magazzino (ad esempio, 12) e assegnarvi le origini di magazzino.
1. Crea alcuni prodotti e assegnali alle origini di magazzino.
1. Crea una categoria.
1. Espandere la sezione [!UICONTROL Products in Category].
1. Fare clic sul pulsante [!UICONTROL Add Product].
1. Osserva il pop-up con l’elenco dei prodotti.

<u>Risultati previsti</u>:

L’elenco dei prodotti viene caricato nella finestra a comparsa entro un tempo ragionevole.

<u>Risultati effettivi</u>:

La finestra a comparsa viene caricata indefinitamente e non viene visualizzato l’elenco dei prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
