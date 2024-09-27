---
title: "ACSD-46767: le cache di pagina [!UICONTROL Category] annullano la validità quando cambia la quantità di scorte"
description: Applicare la patch ACSD-46767 per risolvere il problema di Adobe Commerce, in cui le cache di pagina [!UICONTROL Category] annullano la validità quando cambia la quantità di magazzino, anche se il prodotto è ancora in magazzino.
feature: Cache, Products, Inventory
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category] le cache di pagina invalidano quando cambia la quantità di azioni

La patch di ACSD-46767 risolve il problema per cui le cache della pagina [!UICONTROL Category] vengono invalidate quando cambia la quantità di magazzino, anche se il prodotto è ancora in magazzino. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46. L’ID della patch è ACSD-46767. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le cache di pagina [!UICONTROL Category] annullano la validità quando cambia la quantità di scorte.

<u>Passaggi da riprodurre</u>:

1. Crea alcuni prodotti e aggiungili alla stessa categoria.
1. Apri la pagina *[!UICONTROL Category]* nella vetrina per assicurarti che la pagina sia memorizzata nella cache.
1. Ordinare uno dei prodotti della categoria *(la quantità di prodotto è cambiata, ma il prodotto è ancora disponibile)*.
1. Aprire di nuovo la pagina [!UICONTROL Category] nella vetrina.

<u>Risultati effettivi</u>:

La pagina non viene caricata dalla cache. Viene rigenerato.

<u>Risultati previsti</u>:

La pagina viene caricata dalla cache.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
