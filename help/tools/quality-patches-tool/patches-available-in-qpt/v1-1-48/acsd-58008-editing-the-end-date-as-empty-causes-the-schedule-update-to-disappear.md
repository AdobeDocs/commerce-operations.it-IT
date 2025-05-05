---
title: 'ACSD-58008: la modifica della data di fine come *empty* fa scomparire l’aggiornamento della pianificazione'
description: Applica la patch ACSD-58008 per risolvere il problema di Adobe Commerce, per cui la modifica della data di fine come *empty* fa scomparire l’aggiornamento della pianificazione.
feature: Staging, Page Content
role: Admin, Developer
exl-id: 6d2279e5-6580-4325-b0a8-ed62a95da3c2
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-58008: la modifica della data di fine come *empty* fa scomparire l&#39;aggiornamento della pianificazione

La patch ACSD-58008 risolve il problema per cui la modifica della data di fine come *vuota* fa scomparire l&#39;aggiornamento della pianificazione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48. L’ID della patch è ACSD-58008. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La modifica della data di fine come *empty* fa scomparire l&#39;aggiornamento della pianificazione

<u>Passaggi da riprodurre</u>:

1. Accedi come [!UICONTROL Admin].
1. Vai a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e crea una pagina.
1. Selezionare la pagina creata e fare clic su **[!UICONTROL Schedule New Update]**. *(spostarsi nell&#39;angolo superiore destro della pagina)*.
1. Crea quattro aggiornamenti. *(ad esempio, come incremento di* 2 *minuti)*.
1. Aggiorna *aggiorna 2* e imposta l&#39;ora su un&#39;ora precedente all&#39;ultimo *aggiornamento 4*.
1. Salva gli aggiornamenti effettuati.

<u>Risultati previsti</u>:

L&#39;aggiornamento della pianificazione mostra l&#39;*aggiornamento 3*.

<u>Risultati effettivi</u>:

L&#39;aggiornamento della pianificazione non mostra l&#39;*aggiornamento 3*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
