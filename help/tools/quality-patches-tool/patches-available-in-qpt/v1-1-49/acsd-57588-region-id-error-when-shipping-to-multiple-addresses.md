---
title: 'ACSD-57588: errore nell’elaborazione dell’ID di regione durante la spedizione a più indirizzi'
description: Applica la patch ACSD-57588 per risolvere il problema di Adobe Commerce, a causa del quale la spedizione di un ordine a più indirizzi genera un errore durante l’elaborazione dell’ID di regione.
feature: Orders, Shipping/Delivery
role: Admin, Developer
exl-id: 9a455d32-47d3-4d29-b12e-068bbee98f89
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57588: errore nell’elaborazione dell’ID di regione durante la spedizione a più indirizzi

La patch ACSD-57588 risolve il problema che causa la spedizione di un ordine a più indirizzi, causando un errore durante l’elaborazione dell’ID di regione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. L’ID della patch è ACSD-57588. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore attivato durante l’elaborazione dell’ID di regione durante la spedizione a più indirizzi.

<u>Passaggi da riprodurre</u>:

1. Configura il metodo di pagamento [!DNL Braintree].
1. Accedi come cliente sulla vetrina.
1. Aggiungi un prodotto al carrello e procedi alla visualizzazione e alla modifica del carrello.
1. Aggiungere più indirizzi *(ad esempio, UK, US, CA)* durante il processo di pagamento e rivedere l&#39;ordine.
1. Nella pagina di pagamento, seleziona l’opzione di pagamento con carta di credito, immetti le credenziali necessarie e inserisci l’ordine.

<u>Risultati previsti</u>:

L’ordine può essere effettuato correttamente.

<u>Risultati effettivi</u>:

L’ordine non viene effettuato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
