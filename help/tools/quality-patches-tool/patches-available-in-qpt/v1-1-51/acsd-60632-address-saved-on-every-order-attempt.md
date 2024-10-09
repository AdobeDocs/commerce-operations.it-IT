---
title: "ACSD-60632: indirizzo salvato con ogni tentativo di ordine"
description: Applica la patch ACSD-60632 per risolvere il problema Adobe Commerce relativo al salvataggio di un nuovo indirizzo a ogni tentativo di inserimento dell’ordine, indipendentemente dal fatto che l’ordine sia stato creato correttamente o meno.
feature: Orders, Products
role: Admin, Developer
source-git-commit: d68d6f7501e7dd6faf36f8506d1b0aab028eed58
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: indirizzo salvato con ogni tentativo di ordine

La patch ACSD-60632 risolve il problema relativo al salvataggio di un nuovo indirizzo a ogni tentativo di inserimento dell’ordine, indipendentemente dal fatto che l’ordine sia stato creato correttamente o meno. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51. L’ID della patch è ACSD-60632. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Ogni volta che si tenta di inserire un ordine, nel sistema viene salvata una nuova voce di indirizzo, indipendentemente dal fatto che l’ordine sia stato creato correttamente.

<u>Passaggi da riprodurre</u>:

1. Abilita metodo di pagamento **[!DNL PayPal Payflow Link]**:
   * In un computer locale, il sistema non può ricevere chiamate API da [!DNL PayPal Payflow Link] senza un IP reale.
1. Crea un prodotto semplice.
1. Crea un cliente registrato senza indirizzo.
1. Aggiungi il prodotto al carrello.
1. Procedi con il Checkpoint.
1. Inserisci l’indirizzo. Assicurati che il primo indirizzo sia stato creato in questo passaggio.
1. Nella pagina *[!UICONTROL Review and Payments]* selezionare il pulsante di opzione **[!UICONTROL Credit Card (Payflow Link)]**.
1. Fare clic su **[!UICONTROL Continue]**:
   * La pagina di estrazione ritorna al passaggio *[!UICONTROL Review and Payments]* con l&#39;indirizzo prepopolato e il messaggio di errore previsto.
1. Selezionare nuovamente il pulsante di opzione *[!UICONTROL Credit Card (Payflow Link)]*.
1. Fai clic su **[!UICONTROL Continue]**.

<u>Risultati previsti</u>:

Non viene creato un nuovo indirizzo al secondo tentativo di posizionamento dell’ordine.

<u>Risultati effettivi</u>:

Un nuovo indirizzo viene creato dopo ogni tentativo di posizionamento dell’ordine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
