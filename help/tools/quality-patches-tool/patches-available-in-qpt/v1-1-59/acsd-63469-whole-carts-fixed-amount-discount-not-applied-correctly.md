---
title: 'ACSD-63469: sconti sul carrello a importo fisso non applicati correttamente con più regole'
description: Applica la patch ACSD-63469 per risolvere il problema Adobe Commerce, in cui gli sconti di importo fisso per l’intero carrello non vengono applicati correttamente quando viene applicata più di una regola.
feature: Price Rules
role: Admin, Developer
source-git-commit: 3699a9f64198558fcf1ffe53753f035d22c2d301
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# ACSD-63469: sconti sul carrello a importo fisso non applicati correttamente con più regole

La patch ACSD-63469 risolve il problema che non consente la corretta applicazione degli sconti a importo fisso per l&#39;intero carrello quando vengono applicate più regole. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-63469. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando più regole **[!UICONTROL Fixed amount discount for whole cart]** vengono applicate contemporaneamente e i prodotti hanno prezzi scontati o speciali, il valore dello sconto viene calcolato in modo errato.

<u>Passaggi da riprodurre</u>:

1. Creare due prodotti con un prezzo di 850 e 85 dollari e impostare i prezzi speciali rispettivamente su 765 e 68 dollari.
1. Creare due **[!UICONTROL Cart Price Rules]** come segue:
   * Regola 1
      * **[!UICONTROL Conditions]**: per il prodotto $ 850, impostare *Qtà* su *uguale o maggiore di 2*
      * **[!UICONTROL Actions]**: Applica **[!UICONTROL Fixed amount discount for whole cart]** di *$153*
   * Articolo 2
      * **[!UICONTROL Conditions]**: per il prodotto $ 85, impostare *Qtà* su *uguale o maggiore di 2*
      * **[!UICONTROL Actions]**: Applica **[!UICONTROL Fixed amount discount for whole cart]** di *$14*
1. Aggiungi entrambi i prodotti al carrello, ciascuno con una quantità di 2.

<u>Risultati previsti</u>:

Lo sconto applicato nel carrello è di $167.

<u>Risultati effettivi</u>:

Lo sconto applicato nel carrello è di $41.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Questa sezione è facoltativa; potrebbero essere necessari alcuni passaggi dopo l’applicazione della patch per risolvere il problema. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

