---
title: 'MDVA-44533: sconto applicato in modo errato al prodotto figlio in bundle'
description: La patch MDVA-44533 risolve il problema relativo all'applicazione errata di uno sconto a un prodotto figlio in bundle. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15. L'ID della patch è MDVA-44533. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Orders, Personalization, Products
role: Admin
exl-id: 150fe577-a61a-451e-838a-d60be7754bf4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-44533: sconto applicato in modo errato al prodotto figlio in bundle

La patch MDVA-44533 risolve il problema relativo all&#39;applicazione errata di uno sconto a un prodotto figlio in bundle. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15. L&#39;ID della patch è MDVA-44533. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.3-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo sconto non viene applicato correttamente a un prodotto secondario in bundle.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice al prezzo di 50$.
1. Crea un prodotto in bundle e assegna il prodotto semplice come unica opzione per il prodotto in bundle.
1. Crea una regola prezzo carrello con:

   * Condizione: se l’importo totale è superiore a 130$
   * Azione: viene applicato uno sconto di importo fisso di 10$

1. Vai alla vetrina e aggiungi il prodotto del bundle al carrello con qtà = 1.
1. Vai al carrello e controlla che il costo totale del prodotto del bundle è di 50$ e lo sconto non si applica.
1. Cambia la quantità in 2 e aggiorna il carrello. Il costo totale del prodotto in bundle ora dovrebbe essere di 100$.

<u>Risultati previsti</u>:

Lo sconto non viene applicato perché il subtotale è 100\$, che è inferiore a 130\$ nella condizione della regola.

<u>Risultati effettivi</u>:

Viene applicato lo sconto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
