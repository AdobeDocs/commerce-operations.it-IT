---
title: "ACSD-53998: il blocco dinamico basato sul segmento del cliente funziona in modo errato dopo la disconnessione"
description: Applica la patch ACSD-53998 per risolvere il problema di Adobe Commerce, in cui un blocco dinamico basato su un segmento del cliente non funziona correttamente dopo la disconnessione da un account del cliente.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-53998: il blocco dinamico basato sul segmento del cliente funziona in modo errato dopo la disconnessione

La patch ACSD-53998 risolve il problema relativo al malfunzionamento di un blocco dinamico basato su un segmento del cliente dopo la disconnessione da un account cliente. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-53998. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un blocco dinamico basato su un segmento di cliente non funziona correttamente dopo la disconnessione da un account cliente.

<u>Prerequisiti</u>:

Installa e abilita [!DNL Page Builder] moduli.

<u>Passaggi da riprodurre</u>:

1. Crea due segmenti di clienti senza condizioni.
1. Crea due blocchi dinamici per ciascun segmento.
1. Creare un blocco che includa i due blocchi dinamici come [!DNL Page Builder] blocchi dinamici.
1. Crea un widget che includa il blocco precedente e rendi visibile il blocco sotto la sezione piè di pagina di tutte le pagine.
1. Cancella le cache.
1. Apri la home page.
1. Accedi come cliente.
1. Disconnetti.

<u>Risultati previsti</u>:

Il banner creato per i clienti connessi non viene visualizzato per gli utenti guest.

<u>Risultati effettivi</u>:

Il banner creato per il segmento di clienti connesso viene visualizzato anche dopo la disconnessione dall&#39;account cliente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
