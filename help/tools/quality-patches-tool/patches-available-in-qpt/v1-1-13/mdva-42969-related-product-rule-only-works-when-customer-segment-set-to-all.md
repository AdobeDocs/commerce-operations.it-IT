---
title: 'MDVA-42969: la regola di prodotto correlata funziona solo quando il segmento del cliente è impostato su tutti'
description: La patch MDVA-42969 risolve il problema relativo al funzionamento della regola prodotto correlata solo quando il segmento cliente è impostato su all. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L'ID della patch è MDVA-42969. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Customer Service, Marketing Tools, Products
role: Admin
exl-id: 121da040-4541-468a-aeaf-cf98094e1918
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# MDVA-42969: la regola di prodotto correlata funziona solo quando il segmento del cliente è impostato su tutti

La patch MDVA-42969 risolve il problema relativo al funzionamento della regola prodotto correlata solo quando il segmento cliente è impostato su all. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L&#39;ID della patch è MDVA-42969. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola di prodotto correlata funziona solo quando il segmento del cliente è impostato su tutti.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > **Configurazione** > **Catalogo** > **Relazioni prodotto basate su regole** e imposta **Mostra prodotti correlati** = **Solo basati su regole**.
1. Vai a **Clienti** > **Segmenti** e crea un nuovo segmento: **Applica a** = **Visitatori e Clienti registrati**.
1. Vai a **Marketing** > **Regole prodotto correlate** e crea una nuova regola.

   ```code block
   Apply To = Related Products
   Customer Segments = All
   Products to Match = SKU = <select a SKU>
   Products to Display = SKU +is one of+ Constant Value (specify 1-3 products)
   ```

1. Apri il prodotto corrispondente nella vetrina e verifica che siano visualizzati i Prodotti da visualizzare.
1. Modifica la regola creata nel passaggio tre e imposta **Segmenti cliente** = **Specifici** > **Segmento** dal passaggio due.
1. Apri il prodotto corrispondente nella vetrina.

<u>Risultati previsti</u>:

I prodotti correlati basati su regole vengono visualizzati nella vetrina per i visitatori del prodotto, perché il segmento del cliente viene creato con la seguente configurazione:

**Applica a** = **Visitatori e Clienti registrati**

<u>Risultati effettivi</u>:

Non vengono visualizzati prodotti correlati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
