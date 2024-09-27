---
title: "ACSD-50512: errore durante l’aggiornamento della data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto"
description: Applica la patch ACSD-51892 per risolvere il problema di prestazioni di Adobe Commerce, se l’errore *Il collegamento scaricabile non è relativo al prodotto.Verifica il collegamento e riprova*, si verifica quando si aggiorna la data di inizio di un aggiornamento della gestione temporanea del prodotto scaricabile.
feature: Products, Staging
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512: errore durante l’aggiornamento della data di inizio per l’aggiornamento scaricabile della gestione temporanea del prodotto

La patch ACSD-50512 risolve il problema se l&#39;errore *Il collegamento scaricabile non è correlato al prodotto. Verificare il collegamento e riprovare*, che si verifica quando si aggiorna la data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51502. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore *Il collegamento scaricabile non è correlato al prodotto. Verificare il collegamento e riprovare*, che si verifica quando si aggiorna la data di inizio per un aggiornamento scaricabile della gestione temporanea del prodotto.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto scaricabile, con *collegamenti scaricabili* e *collegamenti di esempio*.
1. Crea un aggiornamento pianificato per lo stesso prodotto e salva il prodotto.
1. Modifica l’aggiornamento pianificato preconfigurato (dal passaggio 2) e modifica la data di inizio.
1. Salva l’aggiornamento pianificato.

<u>Risultati previsti</u>:

Le modifiche all&#39;aggiornamento pianificato sono state salvate correttamente.

<u>Risultati effettivi</u>:

Errore: *Il collegamento scaricabile non è correlato al prodotto. Verifica il collegamento e riprova*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
