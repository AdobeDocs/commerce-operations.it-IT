---
title: 'MDVA-39195: l''opzione Aggiungi al carrello non è attiva nella pagina Categoria'
description: La patch MDVA-39195 risolve il problema relativo all'inattività del pulsante **Aggiungi al carrello** nella pagina Categoria quando è abilitato il reindirizzamento al carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-39195. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: Categories, Orders, Shopping Cart
role: Admin
exl-id: 2c391f54-3b9e-4e72-944b-b003e4ade9b9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-39195: l&#39;opzione Aggiungi al carrello non è attiva nella pagina Categoria

La patch MDVA-39195 risolve il problema relativo all&#39;inattività del pulsante **Aggiungi al carrello** nella pagina Categoria quando è abilitato il reindirizzamento al carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-39195. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il pulsante **Aggiungi al carrello** non è attivo nella pagina Categoria quando è abilitato il reindirizzamento al carrello.

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Pagamento**.
1. Espandere la sezione **Carrello acquisti**.
1. Imposta **Dopo aver aggiunto un reindirizzamento prodotto al carrello** su Sì.
1. Visita la pagina Categoria.

<u>Risultati previsti</u>:

**Aggiungi al carrello** è attivo nella pagina categoria.

<u>Risultati effettivi</u>:

Il pulsante **Aggiungi al carrello** non è attivo nella pagina categoria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
