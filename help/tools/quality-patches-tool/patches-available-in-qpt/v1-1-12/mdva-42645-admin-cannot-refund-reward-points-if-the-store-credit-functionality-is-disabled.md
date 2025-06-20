---
title: 'MDVA-42645: l''amministratore non può rimborsare i punti premio per il credito dell''archivio disabilitato'
description: La patch MDVA-42645 risolve il problema per cui l'amministratore non può rimborsare i punti premio se la funzionalità di credito all'archivio è disabilitata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-42645. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645: l&#39;amministratore non può rimborsare i punti premio per il credito dell&#39;archivio disabilitato

La patch MDVA-42645 risolve il problema per cui l&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito all&#39;archivio è disabilitata. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-42645. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito dell&#39;archivio è disabilitata.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea un nuovo account cliente e aggiungi alcuni punti premio.
1. Disattiva la funzionalità di credito dello store andando in **Store** > Impostazioni > **Configurazione** > **Cliente** > **Configurazione cliente** > **Opzioni di credito dello store**.
1. Accedi come cliente a cui sono assegnati i punti premio.
1. Aggiungi un prodotto al carrello e passa a pagamento.
1. Utilizza i punti premio nella sezione pagamento e inserisci l’ordine.
1. Aprire l&#39;ordine nell&#39;amministratore e fatturarlo.
1. Fare clic sul collegamento **Nota di credito** per creare una nuova nota di credito.
1. Selezionare l&#39;opzione Rimborsa punti premio nella parte inferiore e fare clic su **Rimborso non in linea**.

<u>Risultati previsti</u>:

* Creazione della nota di credito completata.
* I punti premio vengono rimborsati correttamente.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Non è possibile utilizzare un credito per l&#39;archivio superiore all&#39;importo dell&#39;ordine.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
