---
title: 'ACSD-61522: gli indirizzi e-mail nei campi *First and Last Name* (Nome e cognome) inviano conferme di ordine non valide'
description: Applica la patch ACSD-61522 per risolvere il problema di Adobe Commerce, che consente di immettere indirizzi e-mail nei campi *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* di un cliente ospite. In tal caso verranno inviate e-mail di conferma dell'ordine non valide.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522: gli indirizzi e-mail nei campi *Nome e Cognome* inviano conferme di ordini non valide

La patch ACSD-61522 risolve il problema che consente di immettere indirizzi e-mail nei campi *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* di un cliente ospite, causando l&#39;invio di e-mail di conferma dell&#39;ordine non valide. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61522. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p9

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il sistema consente l&#39;immissione di indirizzi e-mail nei campi *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* di un cliente ospite, con conseguente invio di e-mail di conferma dell&#39;ordine non valide.

<u>Passaggi da riprodurre</u>:

1. Aggiungi qualsiasi prodotto al carrello come cliente ospite.
1. Vai a **[!UICONTROL Checkout]**.
1. Compila il campo *[!UICONTROL Email Address]* con *test1@example.com*.
1. Compila il campo *[!UICONTROL First Name]* con *<test2@example.com>*.
1. Compila *[!UICONTROL Last Name]* con *<test3@example.com>*.
1. Compila altri campi obbligatori.
1. Effettua l’ordine.

<u>Risultati previsti</u>:

Non è possibile utilizzare indirizzi e-mail nei campi *[!UICONTROL First Name]* e *[!UICONTROL Last Name]*.

<u>Risultati effettivi</u>:

1. L’ordine viene effettuato.
1. *[!UICONTROL First Name]* e *[!UICONTROL Last Name]* campi salvati come immessi.
1. Le e-mail di conferma dell’ordine vengono inviate a tutte e tre le e-mail.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
