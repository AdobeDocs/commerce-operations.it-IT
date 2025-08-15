---
title: 'MDVA-39153: l''importo dello sconto non viene calcolato correttamente durante il riordino in Admin'
description: La patch MDVA-39153 risolve il problema relativo al calcolo errato dell'importo dello sconto durante il riordino in Admin. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. L'ID della patch è MDVA-39153. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153: l&#39;importo dello sconto non viene calcolato correttamente durante il riordino in Admin

La patch MDVA-39153 risolve il problema relativo al calcolo errato dell&#39;importo dello sconto durante il riordino in Admin. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. L&#39;ID della patch è MDVA-39153. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importo dello sconto viene calcolato in modo errato durante il riordino in Admin.

<u>Passaggi da riprodurre</u>:

1. Vai a **Amministratore** > **Archivi** > **Configurazione** > **Vendite** > **Tasse**.
1. Attiva l&#39;imposta per la spedizione che mostra l&#39;imposta nel carrello.
1. Abilita e configura il metodo di spedizione delle tariffe della tabella ($15).
1. Creare una regola fiscale per l&#39;aliquota predefinita (per CA).
1. Crea una regola di prezzo del carrello con uno sconto fisso di $5 applicato all’intero carrello e all’importo della spedizione.
1. Aggiungi al carrello un prodotto del prezzo di 12 $ e passa alla pagina Carrello acquisti.
1. Applica lo sconto al carrello.
1. Impostare il metodo di spedizione nella sezione &quot;Stime&quot; su &quot;Tariffa fissa&quot;.
1. Procedi attraverso il pagamento fino ai passaggi di revisione (non inserire l&#39;ordine).
1. Vai alla home page e poi torna al carrello.
1. Modificare il metodo di spedizione nella sezione &quot;Stime&quot; in &quot;Tariffa tabella&quot;.

<u>Risultati previsti</u>:

Lo sconto rimane lo stesso - $5.

<u>Risultati effettivi</u>:

Lo sconto è di 6,31 $.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
