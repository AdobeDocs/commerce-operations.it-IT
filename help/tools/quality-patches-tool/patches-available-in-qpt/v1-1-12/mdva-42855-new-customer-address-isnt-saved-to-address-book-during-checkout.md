---
title: "MDVA-42855: il nuovo indirizzo del cliente non viene salvato nella rubrica durante l'estrazione"
description: La patch di MDVA-42855 risolve il problema che impedisce il salvataggio del nuovo indirizzo del cliente nella rubrica durante il pagamento. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-42855. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: il nuovo indirizzo del cliente non viene salvato nella rubrica durante il pagamento

La patch di MDVA-42855 risolve il problema che impedisce il salvataggio del nuovo indirizzo del cliente nella rubrica durante il pagamento. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-42855. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il nuovo indirizzo del cliente non viene salvato nella rubrica durante il pagamento.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente e aggiorna l’indirizzo predefinito di spedizione e fatturazione.
1. Aggiungi un prodotto al carrello e passa alla pagina di pagamento.
1. Alla spedizione, fare clic su **+ Nuovo indirizzo**.
1. Immettere il nuovo indirizzo e mantenere selezionata la casella di controllo **Salva nella Rubrica**.
1. Al momento del pagamento, contrassegnare la casella di controllo **Il mio indirizzo di fatturazione e di spedizione è uguale**.
1. Effettua l’ordine.
1. Controllare la rubrica.

<u>Risultati previsti</u>:

Il nuovo indirizzo di spedizione viene salvato nella rubrica.

<u>Risultati effettivi</u>:

Il nuovo indirizzo di spedizione non viene salvato nella rubrica.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
