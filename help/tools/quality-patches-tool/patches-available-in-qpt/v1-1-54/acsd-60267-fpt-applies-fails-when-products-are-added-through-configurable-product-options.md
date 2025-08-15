---
title: 'ACSD-60267: l’FPT non si applica correttamente quando i prodotti vengono aggiunti tramite opzioni di prodotto configurabili'
description: Applica la patch ACSD-60267 per risolvere il problema di Adobe Commerce in cui l’imposta fissa sui prodotti (FPT, fixed product tax) si applica correttamente quando si aggiungono prodotti semplici direttamente al carrello, ma non riesce quando si selezionano gli stessi prodotti tramite opzioni di prodotto configurabili.
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: l’FPT non si applica correttamente quando i prodotti vengono aggiunti tramite opzioni di prodotto configurabili

La patch ACSD-60267 risolve il problema relativo alla corretta applicazione dell&#39;imposta sul prodotto (FPT, Fixed Product Tax) quando si aggiungono prodotti semplici direttamente al carrello, ma non riesce quando si selezionano gli stessi prodotti tramite opzioni di prodotto configurabili. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54. L’ID della patch è ACSD-60267. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La FPT (Fixed Product Tax, imposta fissa sui prodotti) funziona correttamente quando prodotti semplici con FPT vengono aggiunti al carrello, ma la FPT non viene aggiunta quando i prodotti vengono aggiunti tramite la selezione del prodotto configurabile.

<u>Passaggi da riprodurre</u>:

1. Imposta *[!UICONTROL Enable FPT]* su *Sì* passando a *Amministratore* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**.
1. Creare un attributo FPT e assegnarlo a un *[!UICONTROL Attribute Set]*.
1. Apri **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Per *[!UICONTROL Default Label]*, immettere un&#39;etichetta che identifichi l&#39;attributo.
1. Imposta *[!UICONTROL Catalog Input for Store Owner]* su *[!UICONTROL Fixed Product Tax]*.
1. Creare una nuova imposta e una nuova zona e assegnarla a un nuovo *[!UICONTROL Tax Rule]*.
1. Crea un prodotto configurabile con due semplici prodotti.
1. Ora assegna due diversi valori FPT a questi semplici prodotti.
1. Reindicizza e controlla i prezzi sul negozio.
1. Aggiungi i prodotti al carrello e controlla i totali parziali.

<u>Risultati previsti</u>:

* Nella pagina *[!UICONTROL Catalog]* sono visualizzati i prezzi, incluso FPT.
* I subtotali nel carrello includono FPT.

<u>Risultati effettivi</u>:

* Nella pagina *[!UICONTROL Catalog]* non vengono visualizzati i prezzi, incluso il valore FPT.
* Subtotali e riepilogo non validi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
