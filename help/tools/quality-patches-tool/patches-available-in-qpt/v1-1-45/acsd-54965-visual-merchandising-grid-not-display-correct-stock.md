---
title: 'ACSD-54965: nella griglia [!UICONTROL Visual Merchandising] non viene visualizzato il titolo corretto'
description: Applicare la patch ACSD-54965 per risolvere il problema di Adobe Commerce per cui nella griglia [!UICONTROL Visual Merchandising] non viene visualizzato il titolo corretto quando un prodotto viene assegnato a un titolo personalizzato.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: bd8a3547-1d84-4a17-b006-b35d92256211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-54965: nella griglia [!UICONTROL Visual Merchandising] non viene visualizzato il titolo corretto

La patch ACSD-54965 risolve il problema che causa la mancata visualizzazione delle scorte corrette nella griglia [!UICONTROL Visual Merchandising] quando un prodotto viene assegnato a scorte personalizzate. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. L’ID della patch è ACSD-54965. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella griglia [!UICONTROL Visual Merchandising] non viene visualizzato il titolo corretto quando un prodotto viene assegnato al titolo personalizzato.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova origine.
1. Create un nuovo grezzo.
1. Crea due prodotti:
   * Un solo prodotto con il magazzino personalizzato.
   * Un solo prodotto con le scorte di default.
1. Aggiungi questi prodotti a una categoria.
1. Passare alla griglia [!UICONTROL visual Merchandising] (*[!UICONTROL Products in Category]*).

<u>Risultati effettivi</u>:

Negli ambiti *[!UICONTROL All Store Views]*, il prodotto con scorte personalizzate non mostra alcuna quantità. Solo quando è selezionato l&#39;ambito *[!UICONTROL Default Store View]*, le scorte personalizzate mostrano la quantità del prodotto.

<u>Risultati previsti</u>:

La griglia mostra tutte le informazioni sulle scorte se l&#39;ambito è *[!UICONTROL All Store Views]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
