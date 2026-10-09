---
title: 'MDVA-39163: metodi di spedizione non disponibili per gli utenti appena registrati con i prodotti della sessione ospite'
description: La patch MDVA-39163 risolve il problema se i metodi di spedizione non sono disponibili quando viene registrato un nuovo utente e i prodotti nel carrello provengono dalla sessione ospite. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. L'ID della patch è MDVA-39163. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 0%
---
# MDVA-39163: metodi di spedizione non disponibili per gli utenti appena registrati con i prodotti della sessione ospite

La patch MDVA-39163 risolve il problema se i metodi di spedizione non sono disponibili quando viene registrato un nuovo utente e i prodotti nel carrello provengono dalla sessione ospite. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-39163. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I metodi di spedizione non sono disponibili quando il nuovo utente è registrato e i prodotti nel carrello provengono dalla sessione ospite.

<u>Passaggi da riprodurre</u>:

1. Vai a **Amministratore** > **Archivi** > **Configurazione** > **Vendite** > **Metodi di consegna**. Abilita solo il metodo di spedizione **Tariffa fissa** e disabilita tutto il resto.
1. Nel metodo di spedizione **Tariffa fissa**, seleziona l&#39;opzione di paese **Specifico** disponibile nell&#39;impostazione **Spedisci a paesi applicabili** e seleziona un paese dall&#39;elenco (ad esempio, Stati Uniti).
1. Vai a **Amministratore** > **Archivi** > **Configurazione** > **Cliente** > **Configurazione cliente** e imposta **Richiedi conferma e-mail** su _Sì_.
1. Crea un nuovo Modello e-mail in **Amministratore** > **Marketing** > **Modelli e-mail** e carica il modello `Footer (magento/luma)` e sostituisci il contenuto del modello con un blocco CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Vai a **Amministratore** > **Contenuto** > **Progettazione** > **Configurazione** e seleziona il tema relativo al tuo sito Web front-end. Imposta il &quot;Modello piè di pagina&quot; sul nuovo modello e-mail creato.
1. Vai al front-end e aggiungi un prodotto al carrello.
1. Crea un cliente; riceverai un’e-mail per confermare l’indirizzo e-mail. Fai clic sul collegamento di verifica. Verrà effettuato l&#39;accesso al sito Web.
1. Vai a **Il mio account** e aggiungi un indirizzo. Impostare il paese dell&#39;indirizzo sul paese di spedizione impostato in precedenza nella configurazione amministratore.
1. Vai al pagamento.

<u>Risultati previsti</u>:

Il metodo di spedizione è disponibile, in quanto il cliente ha un indirizzo compatibile con il paese di spedizione.

<u>Risultati effettivi</u>:

Metodo di spedizione non disponibile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
