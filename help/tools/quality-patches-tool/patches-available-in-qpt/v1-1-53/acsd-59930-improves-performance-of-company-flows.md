---
title: "ACSD-59930: Migliora le prestazioni dei flussi aziendali"
description: Applica la patch ACSD-59930 per risolvere il problema di Adobe Commerce, se nel pannello di amministrazione viene visualizzato un errore di *Timeout* durante la creazione, il salvataggio o l’eliminazione di una società con un amministratore che ha indirizzi *1000+* nella rubrica.
feature: Customers, B2B
role: Admin, Developer
source-git-commit: bff014ede6ab7e8e72700814bb4edda2e733557a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: migliora le prestazioni dei flussi aziendali

La patch ACSD-59930 risolve il problema che causava la visualizzazione di un errore di *Timeout* nel pannello di amministrazione durante la creazione, il salvataggio o l&#39;eliminazione di una società con un amministratore con *1000+* indirizzi nella rubrica. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53. L’ID della patch è ACSD-59930. Questo problema è pianificato per essere risolto in Adobe Commerce B2B-1.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Migliora le prestazioni dei flussi di creazione, salvataggio ed eliminazione della società.

<u>Prerequisiti:</u>:

Installare e abilitare i moduli B2B di Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Crea un cliente con *1000+* indirizzi in *[!UICONTROL Address Book]*.
1. Crea una società e utilizza il cliente in precedenza come amministratore.
1. Salva la società.

<u>Risultati previsti</u>:

La società è stata creata senza visualizzare errori di timeout.

<u>Risultati effettivi</u>:

Viene visualizzato un errore di timeout.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].