---
title: 'ACSD-63182: errore durante il salvataggio di un prodotto dopo la duplicazione del prodotto nel bundle'
description: Applica la patch ACSD-63182 per risolvere il problema di Adobe Commerce in cui si verifica un errore durante il salvataggio di un prodotto dopo che un prodotto bundle è stato duplicato con MSI abilitato.
feature: Inventory, Catalog Management
Role: Admin, Developer
exl-id: 2c664c89-e00e-40a8-9127-8c3f36c5bab9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-63182: errore durante il salvataggio di un prodotto dopo la duplicazione del prodotto nel bundle

La patch ACSD-63182 risolve il problema che impediva il salvataggio di un prodotto semplice utilizzato come opzione bundle dopo la duplicazione del prodotto del bundle. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63182. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore durante il salvataggio di un prodotto semplice utilizzato come opzione bundle dopo la duplicazione del prodotto bundle.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova sorgente MSI e un nuovo stock.
1. Creare due prodotti semplici: **p1** e **p2**.
1. Crea un prodotto bundle **b1** con **p1** e **p2** come opzioni bundle.
1. Modifica il **prodotto bundle b1** e fai clic su ***[!UICONTROL Save and Duplicate]***.
1. Modifica il **prodotto semplice p1** e fai clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

Il prodotto viene salvato senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:
*Eccezione: esiste già un elemento (Magento\Catalog\Model\Product\Interceptor) con lo stesso ID &#39;XXX&#39;.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
