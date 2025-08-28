---
title: 'ACP2E-3767: dopo il salvataggio di un prodotto bundle, viene nuovamente visualizzata l’ultima opzione bundle'
description: Applica la patch ACP2E-3767 per risolvere il problema di Adobe Commerce che impediva la rimozione dell’ultima opzione di bundle in un prodotto bundle.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767: dopo il salvataggio di un prodotto bundle, viene nuovamente visualizzata l’ultima opzione bundle

La patch ACP2E-3767 risolve il problema che causa la ricomparsa dell’ultima opzione del bundle dopo il salvataggio del prodotto del bundle. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACP2E-3767. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile rimuovere l’ultima opzione bundle in un prodotto bundle.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Seleziona **[!UICONTROL Simple Product]** dal menu a discesa.
1. Inserisci i dati richiesti e salva.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Seleziona **[!UICONTROL Bundle Product]** dal menu a discesa.
1. Immetti i dati richiesti.
1. In Elementi bundle fare clic su **[!UICONTROL Add Option]**.
1. Aggiungi un titolo alla nuova opzione, quindi fai clic su **[!UICONTROL Add Products to Option]**.
1. Selezionare il prodotto semplice creato in precedenza, quindi **[!UICONTROL Add Selected Products]**.
1. Salva prodotto bundle.
1. Rimuovi l’opzione bundle e salva.

<u>Risultati previsti</u>:

1. L’opzione bundle è stata rimossa correttamente.
1. Se la rimozione non è consentita, viene visualizzato un messaggio.

<u>Risultati effettivi</u>:

1. L’opzione bundle rimane attiva.
1. Non viene visualizzato alcun errore o notifica.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
