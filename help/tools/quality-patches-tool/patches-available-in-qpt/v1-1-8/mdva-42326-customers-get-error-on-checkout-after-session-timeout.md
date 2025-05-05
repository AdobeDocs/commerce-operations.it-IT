---
title: "MDVA-42326: i clienti ricevono un errore al momento dell'estrazione dopo il timeout della sessione"
description: La patch di MDVA-42326 risolve il problema relativo all'errore che i clienti ricevono al momento del pagamento dopo il timeout della sessione, anche se il carrello acquisti persistente è abilitato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8. L'ID della patch è MDVA-42326. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Checkout, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-42326: i clienti ricevono un errore al momento dell&#39;estrazione dopo il timeout della sessione

La patch di MDVA-42326 risolve il problema relativo all&#39;errore che i clienti ricevono al momento del pagamento dopo il timeout della sessione, anche se il carrello acquisti persistente è abilitato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.8. L&#39;ID della patch è MDVA-42326. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti ricevono un errore al momento del pagamento dopo il timeout della sessione, anche se il carrello acquisti persistente è abilitato.

<u>Prerequisiti</u>:

1. Vai a **Configurazione** > **Generale** > **Web** > **Impostazioni cookie predefinite** > **Durata cookie** e imposta su **120**.
1. Vai a **Configurazione** > **Clienti** > **Configurazione cliente** > **Opzioni clienti online** e imposta entrambi i valori su **2**.
1. Vai a **Configurazione** > **Clienti** > **Carrello acquisti persistente** e imposta su **Abilita**.
1. Vai a **Configurazione** > **Vendite** > **Metodi di pagamento** e disattiva tutti i metodi di pagamento eccetto **Assegno/vaglia postale** (dovrebbe essere abilitato).

<u>Passaggi da riprodurre</u>:

1. Accedi come cliente e aggiungi alcuni prodotti al carrello.
1. Controlla il carrello.
1. Attendi due minuti (impostati come condizione preliminare); la sessione dovrebbe scadere.
1. Fare clic su **Vai a pagamento** e non aggiornare la pagina.
1. Effettua il pagamento come ospite, compila l&#39;indirizzo di spedizione e scegli un metodo di spedizione.
1. Fai clic su **Avanti**.
1. Nella pagina **Verifica e pagamenti**, fai clic su **Inserisci ordine**. Poiché è consentito un solo metodo di pagamento, il cliente deve poter effettuare l&#39;ordine senza selezionare il metodo di pagamento.

<u>Risultati previsti</u>:

Il cliente deve essere in grado di effettuare l’ordine.

<u>Risultati effettivi</u>:

Il cliente riceve il seguente errore: *Convalida indirizzo non riuscita: formato dell&#39;e-mail errato*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
