---
title: 'ACSD-45049: l’impostazione dell’attributo "E’ obbligatorio" del cliente non funziona secondo l’ambito del sito web in Admin'
description: Applicare la patch ACSD-45049 per risolvere il problema di Adobe Commerce in cui l'attributo cliente "[!UICONTROL Is required]" non viene correttamente sostituito in base all'ambito del sito Web in Admin.
feature: Attributes, Customers
role: Admin, Developer
exl-id: 368af877-a3ec-431f-8f41-5d51354be571
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-45049: l&#39;impostazione dell&#39;attributo del cliente *[!UICONTROL Is required]* non funziona in base all&#39;ambito del sito Web in Admin

La patch ACSD-45049 risolve il problema se l&#39;impostazione dell&#39;attributo del cliente *[!UICONTROL Is required]* non funziona correttamente in base all&#39;ambito del sito Web in Admin. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) 1.1.50. L’ID della patch è ACSD-45049. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p7 e 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;impostazione dell&#39;attributo del cliente *[!UICONTROL Is required]* non funziona correttamente in base all&#39;ambito del sito Web in Amministrazione.

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web.
1. Apri **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Crea un nuovo attributo, set **[!UICONTROL Is value required]** = *No*.
1. Passare al sito Web predefinito e modificare **[!UICONTROL Is value required]** = *Sì*. L&#39;altro sito Web ha il valore predefinito.
1. Crea un nuovo cliente da Amministratore per il sito Web non predefinito.

<u>Risultati previsti</u>:

L&#39;attributo non è necessario per il sito Web non predefinito.

<u>Risultati effettivi</u>:

* L’attributo è obbligatorio per il sito web non predefinito quando si crea un cliente in Admin.
* L’attributo non è necessario per il sito web non predefinito al momento della registrazione di un cliente nella vetrina.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
