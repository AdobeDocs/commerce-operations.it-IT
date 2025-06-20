---
title: 'ACSD-62872: gli aggiornamenti della pianificazione non vengono convalidati correttamente'
description: Applica la patch ACSD-62872 per risolvere il problema di Adobe Commerce con convalida di attributi univoci in cui gli aggiornamenti pianificati non vengono convalidati correttamente.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# ACSD-62872: gli aggiornamenti della pianificazione non vengono convalidati correttamente

La patch ACSD-62872 risolve il problema della convalida univoca degli attributi, in cui gli aggiornamenti pianificati non vengono convalidati correttamente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62872. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch è contrassegnata come obsoleta per le versioni 2.4.4 - 2.4.6-p8 nella versione 1.1.58 di QPT.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aggiornamento pianificato di un attributo personalizzato non viene convalidato correttamente.

<u>Passaggi da riprodurre</u>:

1. Crea un attributo personalizzato per le categorie.
1. Passa a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crea una nuova categoria.
1. Nella stessa categoria, passare alla sezione **[!UICONTROL Scheduled Updates]**.
1. Imposta un nuovo aggiornamento per questa categoria in qualsiasi momento futuro.
1. Prima di avviare l’aggiornamento pianificato, prova a modificare l’aggiornamento pianificato creato per la categoria.

<u>Risultati previsti</u>:

Deve essere in grado di aggiornare l’aggiornamento pianificato.

<u>Risultati effettivi</u>:

Errore: *Il valore dell&#39;attributo &quot;Custom Attribute&quot; non è univoco. Impostare un valore univoco e riprovare.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
