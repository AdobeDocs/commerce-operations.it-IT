---
title: 'ACSD-53204: *Errore "Il prodotto non può essere salvato"* su richieste simultanee di aggiunta di immagini alla galleria'
description: Applica la patch ACSD-53204 per risolvere il problema di Adobe Commerce, se viene generato l’errore *The product can not be save* (Impossibile salvare il prodotto) quando si eseguono richieste simultanee per aggiungere immagini alla galleria di prodotti utilizzando l’endpoint rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204: errore &quot;*Impossibile salvare il prodotto*&quot; nelle richieste simultanee di aggiunta di immagini alla raccolta

La patch ACSD-53204 risolve il problema che causa l&#39;errore &quot;*Impossibile salvare il prodotto*&quot; quando si eseguono richieste simultanee per aggiungere immagini alla raccolta prodotti utilizzando l&#39;endpoint `rest/V1/products/<sku>/media`. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-53204. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

&quot;*Impossibile salvare il prodotto*&quot; viene generato l&#39;errore quando si eseguono richieste simultanee per aggiungere immagini alla raccolta prodotti utilizzando l&#39;endpoint `rest/V1/products/<sku>/media`.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Crea un prodotto con SKU p1.
1. Effettuare più richieste simultanee all&#39;endpoint `rest/V1/products/<sku>/media` per caricare più immagini contemporaneamente.

<u>Risultati previsti</u>:

Le immagini vengono salvate senza errori.

<u>Risultati effettivi</u>:

&quot;*Impossibile salvare il prodotto*&quot; errore restituito di tanto in tanto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
