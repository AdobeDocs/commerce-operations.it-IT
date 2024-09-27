---
title: "ACSD-48866: errore durante la richiesta del feed RSS per le categorie"
description: Applicare la patch ACSD-48866 per risolvere il problema Adobe Commerce in cui si verifica un errore durante la richiesta del feed RSS per le categorie.
feature: Admin Workspace, Categories
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-48866: errore durante la richiesta del feed RSS per le categorie

La patch ACSD-48866 risolve il problema relativo alla presenza di un errore durante la richiesta di un feed RSS per le categorie. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. L’ID della patch è ACSD-48866. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore durante la richiesta di un feed RSS per le categorie.

<u>Passaggi da riprodurre</u>:

1. Abilita feed RSS in **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL RSS Config]** > **[!UICONTROL Enable RSS]**.
1. Abilita [!UICONTROL Top Level Category] in **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL Catalog]** > **[!UICONTROL Top Level Category]**.
1. Sfogliare la pagina delle categorie dei feed RSS di storefront.
1. Controllare i file di registro in `var/log`.

<u>Risultati previsti</u>:

Nessun errore nel file di registro.

<u>Risultati effettivi</u>:

Nel file di registro viene visualizzato il seguente errore:

```
Text fields are not optimised for operations that require per-document field data like aggregations and sorting, so these operations are disabled by default. Please use a keyword field instead. Alternatively, set fielddata=true on [updated_at] in order to load field data by uninverting the inverted index.
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
