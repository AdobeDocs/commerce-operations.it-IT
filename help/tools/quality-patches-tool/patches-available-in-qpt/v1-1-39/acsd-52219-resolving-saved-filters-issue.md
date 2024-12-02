---
title: 'ACSD-52219: risoluzione del problema di filtro delle griglie di amministrazione nel passaggio alla visualizzazione segnalibro'
description: Applica la patch ACSD-52219 per risolvere il problema di Adobe Commerce, in cui i filtri salvati delle griglie di amministrazione non funzionano come previsto quando si passa di frequente da una visualizzazione di segnalibro all’altra.
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219: risoluzione del problema di filtro delle griglie di amministrazione nel passaggio alla visualizzazione segnalibro

La patch ACSD-52219 risolve il problema relativo al mancato funzionamento dei filtri salvati dalle griglie di amministrazione quando si passa di frequente da una visualizzazione all&#39;altra. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39. L’ID della patch è ACSD-52219. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si passa spesso da una visualizzazione all&#39;altra, i filtri salvati nelle griglie di amministrazione non funzionano come previsto.

<u>Passaggi da riprodurre</u>:

1. Accedere alla griglia [!DNL Sales Order] nell&#39;amministratore.
1. Crea da due a tre filtri.
1. Verificare le impostazioni del filtro cambiando le visualizzazioni per assicurarsi che vengano salvate con precisione.
1. Passare a Filter1 o Filter2.
1. Aggiorna la pagina per aggiornare i dati visualizzati.
1. Passa a una visualizzazione diversa e osserva che i filtri rimangono invariati.
1. Nella vista predefinita vengono ora visualizzati i risultati filtrati, anche se non è stato impostato alcun filtro specifico.

<u>Risultati previsti</u>:

I filtri non vengono scambiati e mantengono lo stato originale.

<u>Risultati effettivi</u>:

Quando si modifica una vista, i filtri si mescolano e la vista corretta non viene salvata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
