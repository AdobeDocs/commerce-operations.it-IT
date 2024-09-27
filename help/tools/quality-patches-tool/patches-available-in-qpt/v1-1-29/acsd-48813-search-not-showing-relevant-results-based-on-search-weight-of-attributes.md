---
title: "ACSD-48813: la ricerca non mostra risultati rilevanti in base al peso degli attributi di ricerca"
description: Applica la patch ACSD-48813 per risolvere il problema di Adobe Commerce, in cui la ricerca non mostra risultati rilevanti in base al peso della ricerca degli attributi.
feature: Admin Workspace, Attributes, Search
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-48813: la ricerca non mostra risultati rilevanti in base al peso degli attributi della ricerca

La patch ACSD-48813 risolve il problema per cui la ricerca non mostra risultati rilevanti in base al peso della ricerca degli attributi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-48813. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La ricerca non mostra risultati rilevanti in base al peso della ricerca degli attributi.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con dati di esempio.
1. Impostare il motore di ricerca come [!DNL Elasticsearch].
1. Accedi come amministratore.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Products]**.
1. Apri l&#39;attributo *name*.
1. Apri la scheda *[!UICONTROL Properties]* della vetrina.
1. Selezionare [!UICONTROL Search Weight] = *10* dal valore a discesa.
1. Fare clic su **[!UICONTROL Save Attribute]**.
1. Aprire la vetrina e cercare la parola *Indietro*.

<u>Risultati previsti</u>:

I prodotti in zaino vengono restituiti nella parte superiore dei risultati di ricerca.

<u>Risultati effettivi</u>:

I prodotti zaino vengono restituiti nel mezzo dei risultati di ricerca.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
