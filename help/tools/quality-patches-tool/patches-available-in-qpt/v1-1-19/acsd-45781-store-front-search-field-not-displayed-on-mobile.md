---
title: 'ACSD-45781: campo di ricerca frontale store non visualizzato sul dispositivo mobile'
description: La patch MDVA-45781 risolve il problema che impedisce la visualizzazione del campo di ricerca della vetrina sul dispositivo mobile. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.19. L'ID della patch è MDVA-45781. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: Cache, Native Luma Frontend Development, Search
role: Admin
exl-id: f761461b-2dd0-45d2-b80d-57793f6f0924
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-45781: campo di ricerca frontale store non visualizzato sul dispositivo mobile

La patch MDVA-45781 risolve il problema che impedisce la visualizzazione del campo di ricerca della vetrina sul dispositivo mobile. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.19. L&#39;ID della patch è MDVA-45781. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il campo di ricerca frontale del Negozio non viene visualizzato sul dispositivo mobile

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Commerce > **Archivi** > **Configurazione** > **Catalogo** > **Ricerca nel catalogo** e imposta:
   * Abilita Recommendations di ricerca a *No*
   * Abilita suggerimenti di ricerca a *No*
1. Fai clic sul pulsante **Salva configurazione**.
1. Pulizia della cache.
1. Utilizzando il tema Luma standard, sfoglia con mobile.
1. Fai clic sul pulsante **Cerca**.

<u>Risultati previsti</u>:

Viene visualizzato il modulo di ricerca input.

<u>Risultati effettivi</u>:

Non succede niente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
