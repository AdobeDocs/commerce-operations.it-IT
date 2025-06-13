---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] non è calcolato correttamente quando vengono applicati più sconti con priorità diverse'
description: Applicare la patch ACSD-61553 per risolvere il problema di Adobe Commerce in cui [!UICONTROL Cart Price Rule] viene calcolato in modo errato quando vengono applicati più sconti con priorità diverse.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] non è calcolato correttamente quando vengono applicati più sconti con priorità diverse

La patch ACSD-61553 risolve il problema relativo al calcolo errato di [!UICONTROL Cart Price Rule] quando vengono applicati più sconti con priorità diverse. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53. L’ID della patch è ACSD-61553. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p8

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Cart Price Rule] viene calcolato in modo errato quando vengono applicati più sconti con priorità diverse.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice al prezzo di 9.000 dollari.
1. Crea un [!UICONTROL Cart Price Rule]: regola A con uno sconto fisso di $ 700 senza condizioni e senza ignorare le regole successive.
1. Crea un altro [!UICONTROL Cart Price Rule]: regola B con uno sconto fisso di $1000 senza condizioni e senza ignorare le regole successive.
1. Aggiungi al carrello il prodotto con la quantità 13.
1. Aggiorna le regole con uno dei seguenti scenari:

   Scenario 01

       Regola A
       Priorità: 1
       Sconto Qtà massimo applicato a: 1
       
       Regola B
       Priorità: 0
       Sconto Qtà massimo applicato a: 0
   
   Scenario 02

       Regola A
       Priorità: 0
       Sconto Qtà massimo applicato a: 0
       
       Regola B
       Priorità: 1
       Sconto Qtà massimo applicato a: 1
   
   Scenario 03

       Regola A
       Priorità: 0
       Sconto Qtà massimo applicato a: 0
       
       Regola B
       Priorità: 0
       Sconto Qtà massimo applicato a: 1
   
1. Fare clic sul pulsante **[!UICONTROL Update Shopping Cart]** per ricalcolare gli sconti.

<u>Risultati previsti</u>:

Viene visualizzato il seguente sconto totale per scenari diversi:

    Scenario 01: $ 13.700
    Scenario 02: $ 10.100
    Scenario 03: $ 10.100

<u>Risultati effettivi</u>:

In tutti e tre gli scenari, lo sconto totale è di $9.000.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
