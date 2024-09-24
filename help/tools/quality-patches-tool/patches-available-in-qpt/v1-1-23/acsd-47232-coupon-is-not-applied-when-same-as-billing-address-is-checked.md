---
title: "ACSD-47232: il coupon non viene applicato quando [!UICONTROL Same as Billing Address] è selezionato"
description: Applicare la patch ACSD-47232 per risolvere il problema Adobe Commerce in cui il coupon non viene applicato quando [!UICONTROL Same as Billing Address] è selezionato.
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: il coupon non viene applicato quando [!UICONTROL Same as Billing Address] è selezionato

La patch di ACSD-47232 risolve il problema relativo alla mancata applicazione del coupon quando viene selezionato **[!UICONTROL Same as Billing Address]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23. L’ID della patch è ACSD-47232. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il coupon non viene applicato quando **[!UICONTROL Same as Billing Address]** è selezionato.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Creare un prodotto semplice con peso = *8*.
1. Crea un nuovo cliente con indirizzo di fatturazione e spedizione predefinito.
1. Crea una regola di prezzo del carrello con un coupon.
   * Nelle sezioni **[!UICONTROL Conditions]**, aggiungi *Il peso totale è uguale o maggiore di 5*
1. Provare a creare un nuovo ordine nell&#39;amministratore [!UICONTROL Commerce].
   * Utilizza il cliente appena creato
   * Aggiungi un prodotto
   * Prova ad applicare il coupon

<u>Risultati previsti</u>:

Coupon applicato.

<u>Risultati effettivi</u>:

Viene visualizzato un errore simile al seguente: *Il codice coupon 123 non è valido. Verificare il codice e riprovare.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
