---
title: "ACSD-50815: la quantità decimale per il prodotto semplice non può essere utilizzata per la nuova opzione di prodotto in bundle"
description: Applica la patch ACSD-50815 per risolvere il problema di Adobe Commerce, in cui la quantità decimale per un prodotto semplice non può essere utilizzata per una nuova opzione di prodotto in bundle.
feature: Products
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-50815: la quantità decimale per il prodotto semplice non può essere utilizzata per la nuova opzione di prodotto in bundle

La patch ACSD-50815 risolve il problema che impediva l’utilizzo della quantità decimale per un prodotto semplice per una nuova opzione di prodotto in bundle. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35. L’ID della patch è ACSD-50815. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità decimale per un prodotto semplice non può essere utilizzata per una nuova opzione di prodotto in bundle.

<u>Passaggi da riprodurre</u>:

1. Accedi come amministratore.
1. Crea un nuovo prodotto semplice.
   * Nella finestra **[!UICONTROL Advanced Inventory]**, impostare [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes].
   * Salva il prodotto semplice.
1. Crea un nuovo prodotto incluso.
1. Aggiungi un’opzione.
1. Aggiungi il prodotto semplice in questa opzione.
1. Imposta una quantità decimale per il prodotto semplice nell’opzione Prodotto in bundle. Ad esempio, 1.5.

<u>Risultati previsti</u>:

È possibile impostare la quantità decimale. Non viene visualizzato alcun errore.

<u>Risultati effettivi</u>:

Errore, *Immettere un numero valido in questo campo*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
