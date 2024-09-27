---
title: '"ACSD-53176: la regola del prodotto con la condizione "is one of" non corrisponde"'
description: Applica la patch ACSD-53176 per risolvere il problema di Adobe Commerce in cui la relativa regola prodotto "è una delle" condizioni non funziona correttamente per "Products to Match".
feature: Marketing Tools
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176: la regola prodotto con condizione `is one of` non corrisponde

La patch ACSD-53176 risolve il problema che causa il funzionamento errato della condizione `is one of` della regola prodotto correlata per **Prodotti da abbinare**. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.36. L’ID della patch è ACSD-53176. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La condizione `is one of` della regola prodotto correlata non funziona correttamente per **Prodotti da abbinare**.

<u>Passaggi da riprodurre</u>:

1. Creazione di 3-4 prodotti.
1. Crea una nuova regola prodotto correlata.

   Imposta la regola in modo che corrisponda a due o più prodotti:
   * `SKU is one of "S1,S2".`

   Imposta la regola per visualizzare due o più elementi:
   * `Product SKU is one of constant value "S2,S3".`

1. Apri il prodotto S1 su Storefront.

<u>Risultati previsti</u>:

I prodotti correlati &quot;S2&quot; e &quot;S3&quot; sono visualizzati su entrambe le pagine di prodotto &quot;S1&quot; e &quot;S2&quot;.

<u>Risultati effettivi</u>:

I prodotti correlati non vengono visualizzati nelle pagine dei prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
