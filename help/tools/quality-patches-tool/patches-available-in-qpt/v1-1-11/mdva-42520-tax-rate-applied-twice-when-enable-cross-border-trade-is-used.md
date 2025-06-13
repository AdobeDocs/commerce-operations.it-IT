---
title: 'MDVA-42520: aliquota applicata due volte quando si utilizza "Abilita commercio transfrontaliero"'
description: La patch MDVA-42520 risolve il problema dell'applicazione dell'aliquota due volte quando si utilizza **Abilita commercio transfrontaliero**. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11. L'ID della patch è MDVA-42520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# MDVA-42520: aliquota applicata due volte quando si utilizza &quot;Abilita commercio transfrontaliero&quot;

La patch di MDVA-42520 risolve il problema relativo all&#39;applicazione dell&#39;aliquota due volte quando si utilizza **Abilita commercio transfrontaliero**. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11. L&#39;ID della patch è MDVA-42520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aliquota viene applicata due volte quando si utilizza **Abilita commercio transfrontaliero**.

<u>Passaggi da riprodurre</u>:

1. Abilita **Società**, **Catalogo condiviso** e **Citazione**
1. Configura le imposte in base alla schermata. Assicurati di abilitare **il commercio transfrontaliero**.

   ![impostazioni imposta](/help/assets/tools/tax_settings_1.png){width="700"}

1. Creare un&#39;aliquota fiscale per la Germania (10%).
1. Creare una regola fiscale per applicare l&#39;aliquota.
1. Crea una società e un catalogo condiviso personalizzato.
1. Crea un prodotto con un prezzo di 100 e includilo nel catalogo condiviso personalizzato con uno sconto del 20%.
1. Crea un cliente con un indirizzo in tedesco e assegnalo all’azienda
1. Aggiungi 10 prodotti alla scheda come cliente.
1. Vai al carrello e richiedi un preventivo.
1. Apri questo preventivo sul backend e prova ad aggiungere un ulteriore sconto del 10%.

<u>Risultati previsti</u>:

Subtotale preventivo (imposte incluse) e Totale complessivo preventivo (imposte incluse) = $ 720

<u>Risultati effettivi</u>:

Subtotale preventivo (imposte incluse) e Totale complessivo preventivo (imposte incluse) = 649,50 $.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
