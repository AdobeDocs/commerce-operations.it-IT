---
title: 'ACP2E-3731: le esportazioni di prodotti con visibilità [!UICONTROL Catalog, Search] includono record di altre viste store'
description: Applica la patch ACP2E-3731 per correggere l’Adobe Commerce in cui le esportazioni di prodotti con il filtro di visibilità impostato su [!UICONTROL Catalog, Search] includono righe non corrette nelle impostazioni multi-store a causa di varianti di attributi con ambito store.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: le esportazioni di prodotti con visibilità [!UICONTROL Catalog, Search] includono record di altre viste store

La patch ACP2E-3731 risolve il problema per cui le esportazioni di prodotti con visibilità *[!UICONTROL Catalog, Search]* includono erroneamente record di altre visualizzazioni di store in ambienti multi-store. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACP2E-3731. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p9

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le esportazioni dei prodotti includono righe non corrette quando il filtro di visibilità è impostato su *[!UICONTROL Catalog, Search]* nelle impostazioni multi-store a causa di varianti di attributi con ambito di archiviazione.

<u>Passaggi da riprodurre</u>:

1. Nel pannello di amministrazione, passa a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** per creare una visualizzazione aggiuntiva per sito Web, archivio e archivio.
1. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]**. Fare clic su **[!UICONTROL Add Attribute Set]** per creare un attributo. Imposta **[!UICONTROL Based On]** su *Predefinito*.
1. Crea un prodotto e assegnalo sia al sito web principale che a quello secondario.
1. Imposta un valore di testo per l&#39;attributo appena creato con **[!UICONTROL Scope]** impostato su *Tutte le visualizzazioni dello store*.
1. Modifica l’ambito nella vista dell’archivio secondario e aggiorna l’attributo con un valore diverso.
1. Modificare l&#39;ambito nella visualizzazione predefinita dello store e nella visualizzazione secondaria dello store, quindi impostare la visibilità del prodotto su *Non visibile singolarmente*.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Export]** e seleziona *Prodotti* dal menu a discesa.
1. Impostare un filtro in cui **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* e fare clic su **[!UICONTROL Continue]**.
1. Esegui il comando seguente per elaborare l’esportazione:

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Controlla il file esportato.

<u>Risultati previsti</u>:

Vengono esportati solo i record filtrati.

<u>Risultati effettivi</u>:

Il file esportato include una riga per la visualizzazione dell&#39;archivio secondario che non corrisponde ai criteri di filtro impostati durante l&#39;esportazione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
