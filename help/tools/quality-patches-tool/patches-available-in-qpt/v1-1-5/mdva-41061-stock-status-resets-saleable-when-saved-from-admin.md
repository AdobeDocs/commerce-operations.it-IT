---
title: 'MDVA-41061: lo stato del magazzino viene reimpostato su vendibile quando il prodotto viene salvato dall''amministratore'
description: La patch MDVA-41061 risolve il problema se lo stato delle scorte viene reimpostato su vendibile quando il prodotto viene salvato dall'amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. L'ID della patch è MDVA-41061. La versione più recente della patch è disponibile in QPT 1.1.15 con ID di patch MDVA-41061-V3. Tieni presente che il problema è risolto in Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061: lo stato del magazzino viene reimpostato su vendibile quando il prodotto viene salvato dall&#39;amministratore

La patch MDVA-41061 risolve il problema se lo stato delle scorte viene reimpostato su vendibile quando il prodotto viene salvato dall&#39;amministratore. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. L&#39;ID della patch è MDVA-41061. La versione più recente della patch è disponibile in QPT 1.1.15 con ID di patch MDVA-41061-V3. Tieni presente che il problema è risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato delle scorte viene reimpostato su vendibile quando il prodotto viene salvato dall’amministratore.

<u>Prerequisiti</u>:

I moduli di inventario sono installati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto semplice con Qtà = 1.
1. Effettuare un ordine utilizzando il prodotto creato nel passaggio 1.
1. Esegui cron: verificare che la coda `inventory.reservations.updateSalabilityStatus` sia stata eseguita e che lo stato delle scorte di prodotto sia stato modificato a zero nella tabella `cataloginventory_stock_status`.
1. Controlla il prodotto sul front-end. Deve essere contrassegnato come **esaurito**.
1. Salva il prodotto nell’amministratore senza apportare modifiche.

<u>Risultati previsti</u>:

* Lo stato dello stock non deve essere aggiornato.
* Il prodotto deve essere **esaurito** sul front-end.

<u>Risultati effettivi</u>:

* Il prodotto semplice è contrassegnato come **In magazzino** sul front-end.
* Gli utenti ricevono *Il messaggio con la quantità richiesta non è disponibile* quando tentano di aggiungerla al carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
