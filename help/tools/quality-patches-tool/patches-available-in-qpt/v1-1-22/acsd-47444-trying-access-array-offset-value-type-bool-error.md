---
title: 'ACSD-47444: errore _[!UICONTROL Trying to access array offset on value of type bool]_ durante l''accesso a determinati percorsi di categoria non esistenti per prodotti noti in PHP 7.4'
description: Applicare la patch ACSD-47444 per risolvere il problema Adobe Commerce in caso di errore _[!UICONTROL Trying to access array offset on value of type bool]_ durante l'accesso a determinati percorsi di categoria non esistenti per prodotti noti, in PHP 7.4.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444: errore _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;durante l&#39;accesso a determinati percorsi di categoria non esistenti per prodotti noti in PHP 7.4

La patch ACSD-47444 risolve il problema relativo all&#39;errore _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;durante l&#39;accesso a determinati percorsi di categoria non esistenti per prodotti noti in PHP 7.4. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore: _[!UICONTROL Trying to access array offset on value of type bool]_&#x200B;durante l&#39;accesso a determinati percorsi di categoria non esistenti per prodotti noti in PHP 7.4.

<u>Prerequisiti</u>:

PHP 7.4.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo prodotto, denominato &quot;test&quot;.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > imposta **[!UICONTROL Generate "category/product" URL Rewrites]** = _No_.
1. Vai alla vetrina e visita l’URL come ../abc/test.html (&quot;abc&quot; - non dovrebbe esistere).

<u>Risultati previsti</u>:

404 pagine.

<u>Risultati effettivi</u>:

Errore 500:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
