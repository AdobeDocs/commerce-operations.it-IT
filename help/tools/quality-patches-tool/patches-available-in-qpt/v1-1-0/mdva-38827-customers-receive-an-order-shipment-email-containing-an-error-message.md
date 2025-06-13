---
title: 'MDVA-38827: i clienti ricevono un errore di spedizione ordine tramite e-mail'
description: 'La patch di MDVA-38827 risolve il problema relativo alla ricezione da parte dei clienti di un''e-mail di spedizione dell''ordine contenente il seguente messaggio di errore: *Si è verificato un errore durante la generazione di questo contenuto*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. L''ID della patch è MDVA-38827. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.'
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827: i clienti ricevono un errore di spedizione ordine tramite e-mail

La patch di MDVA-38827 risolve il problema relativo alla ricezione da parte dei clienti di un&#39;e-mail di spedizione dell&#39;ordine contenente il seguente messaggio di errore: *Si è verificato un errore durante la generazione del contenuto*. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. L&#39;ID della patch è MDVA-38827. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando è selezionata l&#39;opzione Notifica ai clienti tramite posta elettronica per la spedizione, i clienti ricevono un&#39;e-mail contenente il seguente messaggio di errore: *Si è verificato un errore durante la generazione del contenuto*.

<u>Passaggi da riprodurre</u>:

1. Vai a **Marketing** > **Comunicazioni** > **Modelli e-mail** e seleziona **Aggiungi nuovo modello**.
   * Seleziona **Vendite Magento** > **Nuova spedizione**.
   * Fai clic su **Carica modello**.
   * Aggiungi un nome modello (ad esempio, Modello di spedizione principale) e fai clic su **Salva**.
1. Vai a **Store** > Impostazioni > **Configurazione** > **Vendite** > **E-mail vendite**:
   * Abilita **Commenti spedizione**.
   * Selezionare **Modello di spedizione principale** (fare riferimento alla parte &quot;Aggiungere un nome di modello&quot; del passaggio 1) in Modello e-mail commento spedizione e Modello e-mail commento spedizione per l&#39;ospite.
1. Effettua un ordine. Vai al pannello di amministrazione > **Vendite** > **Ordine**, fai clic su **Visualizza** e spedisci l&#39;ordine.
1. Lo stato dell’ordine passerà da In sospeso a In elaborazione.
1. Fai clic su **Spedizioni** nel menu della barra laterale a sinistra, quindi fai clic su **Visualizza** per visualizzare l&#39;ordine.
1. Aggiungi un commento in **Testo commento** sotto **Cronologia spedizione** e seleziona la casella di controllo **Notifica al cliente via e-mail**.
1. Fare clic su **Invia commento**.

<u>Risultati previsti</u>:

Viene generato un messaggio e-mail di vendita con commenti sulla spedizione.

<u>Risultati effettivi</u>:

Nell&#39;e-mail è stato ricevuto il seguente messaggio di errore: *Si è verificato un errore durante la generazione del contenuto.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
