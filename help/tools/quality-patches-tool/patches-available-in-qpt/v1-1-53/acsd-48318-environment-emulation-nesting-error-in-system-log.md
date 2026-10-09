---
title: 'ACSD-48318: Errore di nidificazione dell’emulazione dell’ambiente in "system.log"'
description: Applica la patch ACSD-48318 per risolvere il problema di Adobe Commerce, dove ogni volta che viene inviata un’e-mail di fattura compare un messaggio di errore *main.ERROR:Environment emulation nesting is not allowed* in "system.log".
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '329'
ht-degree: 0%
---
# ACSD-48318: errore di nidificazione emulazione ambiente in `system.log`

La patch di ACSD-48318 risolve il problema per cui non è consentito nidificare l&#39;emulazione del messaggio di errore *main.ERROR:Environment* viene visualizzato in `system.log` ogni volta che viene inviata un&#39;e-mail di fattura. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. L’ID della patch è ACSD-48318. Tieni presente che il problema è risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il messaggio di errore *La nidificazione dell&#39;emulazione dell&#39;ambiente non è consentita* viene visualizzato in `system.log` ogni volta che viene inviata un&#39;e-mail di fattura.

<u>Passaggi da riprodurre</u>:

1. Inserire un ordine e generare una fattura.
1. Aprire la fattura da Admin e fare clic su **[!UICONTROL Send Email]**.
1. Seguire lo stesso passaggio per *nota di credito* e *spedizione* facendo clic su **[!UICONTROL Send Email]**.

<u>Risultati previsti</u>:

Nessun errore in `system.log`.

<u>Risultati effettivi</u>:

`system.log` è pieno di *main.ERROR: la nidificazione dell&#39;emulazione dell&#39;ambiente non è consentita* error.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
