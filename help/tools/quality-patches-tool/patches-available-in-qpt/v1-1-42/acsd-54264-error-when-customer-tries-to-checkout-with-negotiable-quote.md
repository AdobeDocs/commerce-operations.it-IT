---
title: 'ACSD-54264: errore durante il tentativo del cliente di effettuare il check-out con un preventivo negoziabile'
description: Applica la patch ACSD-54264 per risolvere il problema di Adobe Commerce, in cui viene visualizzato il messaggio di errore "Impossibile aggiornare l’attributo richiesto. Viene visualizzata la riga ID:store_id" quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un'altra vista del punto vendita.
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264: viene visualizzato un errore quando il cliente tenta di effettuare il check-out con un preventivo negoziabile

La patch ACSD-54264 risolve il problema che impediva l&#39;aggiornamento dell&#39;attributo richiesto tramite un messaggio di errore *. ID riga: store_id* viene visualizzato quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un&#39;altra visualizzazione archivio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42. L’ID della patch è ACSD-54264. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Messaggio di errore *Impossibile aggiornare l&#39;attributo richiesto. ID riga: store_id* viene visualizzato quando un cliente tenta di effettuare il Check-Out con un preventivo negoziabile da un&#39;altra visualizzazione archivio.

<u>Prerequisiti</u>:

I moduli B2B di Adobe Commerce vengono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;ulteriore visualizzazione Store per il sito Web predefinito.
1. Abilita *[!UICONTROL B2B Quote]* nella configurazione.
1. Accedi come cliente aziendale in una delle visualizzazioni dello store.
1. Aggiungi un prodotto a *[!UICONTROL Shopping Cart]*.
1. Inviare il preventivo per la revisione.
1. In qualità di utente amministratore, passa a **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** e invia il preventivo approvato.
1. In qualità di cliente dell’azienda, modifica la visualizzazione del punto vendita con un’altra.
1. Prova a dare un&#39;occhiata.

<u>Risultati previsti</u>:

Il cliente effettua un ordine con questo preventivo.

<u>Risultati effettivi</u>:

* L&#39;errore si verifica durante il salvataggio delle informazioni di spedizione:

  `You cannot update the request attribute. Row ID: store_id =#`

* Viene registrato il seguente errore:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
