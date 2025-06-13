---
title: 'ACSD-51884: percorso della cache dell’immagine del prodotto non corretto nel comando di ridimensionamento'
description: Applica la patch ACSD-51884 per risolvere il problema Adobe Commerce, se il percorso della cache delle immagini del prodotto diventa errato dopo l’esecuzione del comando di ridimensionamento.
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884: percorso della cache dell’immagine del prodotto non corretto nel comando di ridimensionamento

La patch ACSD-51884 risolve il problema relativo a un errore interno, in cui il percorso della cache delle immagini del prodotto diventa errato dopo l’esecuzione del comando di ridimensionamento. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-51884. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il percorso della cache delle immagini del prodotto non è più corretto con il comando di ridimensionamento.

<u>Passaggi da riprodurre</u>:

1. Crea nuovo sito Web/store/storeview.
1. Crea un prodotto e assegnalo a entrambi i siti web e carica l’immagine del prodotto.
1. Crea un nuovo tema (consulta il file Adobe.zip in allegato).
1. In `app/design/Adobe/theme/etc/view.xml` modifica:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

a

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Applica il tema alla visualizzazione dello store creata in precedenza.
1. Visita la pagina dedicata al prodotto sul secondo sito Web. L’immagine del prodotto viene visualizzata correttamente.
1. Usa cache di svuotamento:
   `bin/magento cache:flush`
1. Visita la pagina dedicata al prodotto sul secondo sito Web.

<u>Risultati previsti</u>:

L’immagine del prodotto viene visualizzata correttamente.

<u>Risultati effettivi</u>:

L’immagine del prodotto non esiste.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
