---
title: 'ACSD-50276: il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla'
description: Applica la patch ACSD-50276 per risolvere il problema di Adobe Commerce, a causa del quale il modulo di registrazione del cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla.
feature: Attributes, Storefront
role: Admin
exl-id: e7cb2416-d10b-46b0-83c4-93b107560d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50276: il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla

La patch ACSD-50276 risolve il problema che impedisce il funzionamento del modulo di registrazione del cliente nella vetrina se viene creato un attributo cliente a selezione multipla. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. L’ID della patch è ACSD-50276. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il modulo di registrazione cliente non funziona nella vetrina se viene creato un attributo cliente a selezione multipla.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo attributo cliente a selezione multipla con le seguenti impostazioni:

   * *[!UICONTROL Required = Yes]*
   * *[!UICONTROL Show on storefront = Yes]*, selezionare *[!UICONTROL Customer registration form]*.

1. Apri il modulo di registrazione cliente nella vetrina.

<u>Risultati previsti</u>:

Il modulo di registrazione cliente viene caricato correttamente.

<u>Risultati effettivi</u>:

* Il modulo di registrazione cliente non viene caricato.
* Viene registrato il seguente errore:

  ```PHP
  report. CRITICAL: Exception: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in vendor/magento/module-custom-attribute-management/Block/Form/Renderer/Multiselect.php
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
