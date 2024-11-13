---
title: "ACSD-60804: la modifica di un cliente associato a un’azienda eliminata genera un errore"
description: Applicare la patch ACSD-60804 per risolvere il problema Adobe Commerce, se la modifica di un cliente associato a una società eliminata causa un errore *Chiamata a una funzione membro getSuperUserId() su null*.
feature: Companies, Customers, B2B
role: Admin, Developer
source-git-commit: 1231dac065565ff636424673a15ae4148a5f84dd
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-60804: la modifica di un cliente associato a un’azienda eliminata genera un errore

La patch ACSD-60804 risolve il problema per cui la modifica di un cliente associato a una società eliminata causa un errore *Chiamata a una funzione membro getSuperUserId() su null*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. L’ID della patch è ACSD-60804. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La modifica di un cliente associato a una società eliminata causa un errore *Chiamata a una funzione membro getSuperUserId() su null*.

<u>Prerequisiti:</u>:

Installare e abilitare i moduli B2B di Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Vai a **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Accedere a `mysql` per l&#39;istanza.
1. Eliminare la società in cui `entity_id` = *1*.
1. Vai a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifica il cliente che è stato creato automaticamente al momento della creazione della società.

<u>Risultati previsti</u>:

Il cliente viene modificato senza che venga generato un errore di eccezione.

<u>Risultati effettivi</u>:

Errore: *Chiamata a una funzione membro getSuperUserId() su null* se al cliente non è associata alcuna società.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
