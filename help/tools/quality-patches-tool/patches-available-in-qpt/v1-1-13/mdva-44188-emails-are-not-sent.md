---
title: 'MDVA-44188: le e-mail non vengono inviate a ID contenenti ".-"'
description: La patch MDVA-44188 risolve il problema per cui le e-mail non vengono inviate agli ID e-mail contenenti &grave;.-". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13. L'ID della patch è MDVA-44188. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Communications
role: Admin
exl-id: 9029c7f1-3e62-44a1-8962-9730ae54db7d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# MDVA-44188: le e-mail non vengono inviate a ID contenenti &quot;.-&quot;

La patch di MDVA-44188 risolve il problema per cui le e-mail non vengono inviate agli ID e-mail contenenti `.-`. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13. L&#39;ID della patch è MDVA-44188. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile inviare e-mail agli ID e-mail che contengono `.-` nel nome utente.

<u>Passaggi da riprodurre</u>:

1. Registra un cliente con un indirizzo e-mail contenente `.-`. Ad esempio, `.-foo@example.com`.
1. Effettua un ordine.

<u>Risultati previsti</u>:

L&#39;utente con l&#39;ID e-mail contenente `.-` riceve normalmente le e-mail.

<u>Risultati effettivi</u>:

L&#39;e-mail non viene inviata all&#39;ID e-mail contenente `.-`. L&#39;errore seguente viene visualizzato nei log degli errori: *Impossibile aggiungere un indirizzo di posta elettronica non valido alla coda di posta*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
