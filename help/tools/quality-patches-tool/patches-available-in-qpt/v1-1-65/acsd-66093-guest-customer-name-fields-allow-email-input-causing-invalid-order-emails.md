---
title: 'ACSD-66093: i campi Nome cliente ospite consentono l’input delle e-mail, causando la generazione di e-mail di ordine non valide'
description: Applica la patch ACSD-66093 per risolvere il problema di Adobe Commerce, in cui è possibile immettere indirizzi e-mail nei campi **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** del cliente ospite e inviare e-mail di conferma dell'ordine non valide.
feature: Checkout
role: Admin, Developer
source-git-commit: 6ee2f99b53424071fda4cba9396aa039621135fc
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# ACSD-66093: i campi Nome cliente ospite consentono l’input delle e-mail, causando la generazione di e-mail di ordine non valide

La patch ACSD-66093 risolve il problema relativo all&#39;immissione degli indirizzi e-mail nei campi **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** del cliente ospite, generando messaggi e-mail di conferma dell&#39;ordine non validi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-66093. Il problema è stato risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p11

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È possibile immettere gli indirizzi di posta elettronica nei campi **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** del cliente ospite, causando messaggi di posta elettronica di conferma dell&#39;ordine non validi.

<u>Passaggi da riprodurre</u>:

1. Aggiungi prodotti al carrello come cliente ospite.
2. Vai al pagamento.
3. Inserisci l’indirizzo e-mail con &quot;test1@gmail.co&quot;.
4. Compila **[!UICONTROL First Name]** con &quot;<test2@gmail.co>&quot;.
5. Compila **[!UICONTROL Last Name]** con &quot;<test3@gmail.co>&quot;.
6. Compila altri campi obbligatori.
7. Ordinate.

<u>Risultati previsti</u>:

I messaggi di convalida devono essere visualizzati per indicare che i campi **[!UICONTROL First Name]** e **[!UICONTROL Last Name]** non sono validi, ad esempio *First Name non è valido. e Cognome non validi.* e l&#39;ordine non deve essere effettuato.

<u>Risultati effettivi</u>:

L&#39;ordine viene effettuato.
**[!UICONTROL First Name]** e **[!UICONTROL Last Name]** campi salvati come immessi.
L’e-mail di conferma dell’ordine viene inviata a tutte e tre le e-mail: test1@gmail.co, test2@gmail.co e test3@gmail.co.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
