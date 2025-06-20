---
title: 'ACSD-48318: Errore di nidificazione dell’emulazione dell’ambiente in "system.log"'
description: Applica la patch ACSD-48318 per risolvere il problema di Adobe Commerce, dove ogni volta che viene inviata un’e-mail di fattura compare un messaggio di errore *main.ERROR:Environment emulation nesting is not allowed* in "system.log".
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318: errore di nidificazione emulazione ambiente in `system.log`

La patch di ACSD-48318 risolve il problema che causa un messaggio di errore *main.ERROR:Environment emulation nesting is not allowed* (Impossibile nidificare l&#39;emulazione dell&#39;ambiente) in `system.log` ogni volta che viene inviata un&#39;e-mail di fattura. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. L’ID della patch è ACSD-48318. Tieni presente che il problema è risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
