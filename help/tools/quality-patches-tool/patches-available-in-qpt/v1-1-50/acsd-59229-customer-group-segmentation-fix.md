---
title: "ACSD-59229: allocazione errata dei dati del gruppo di clienti a causa di un valore X-Magento-Vary obsoleto"
description: Applica la patch ACSD-59229 per risolvere il problema di Adobe Commerce, a causa del quale le informazioni relative al Magento del cliente vengono salvate nel segmento errato a causa di un valore X-Group-Vary obsoleto nella richiesta.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229: allocazione errata dei dati del gruppo di clienti a causa di un valore X-Magento-Vary obsoleto

La patch di ACSD-59229 risolve il problema relativo al salvataggio delle informazioni sul Magento del cliente nel segmento errato a causa di un valore X-Group-Vary obsoleto nella richiesta. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50. L’ID della patch è ACSD-59229. Il problema è risolto nella versione 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le informazioni relative al gruppo di clienti vengono salvate nel segmento errato a causa di un valore X-Magento-Vary obsoleto nella richiesta.

<u>Prerequisiti</u>:

Verificare che Adobe Commerce B2B con i dati di esempio sia installato e che [!DNL Varnish] sia configurato.

<u>Passaggi da riprodurre</u>:

1. Imposta prezzi avanzati per [!DNL SKU 24-MB01]:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Ingrosso* = *$200*
      * *Rivenditore* = *$30*

1. Crea due account cliente.
1. Assegna entrambi i clienti al gruppo **Ingrosso**.
1. Apri due diverse sessioni del browser e accedi con ciascun cliente.
1. Passare alla pagina del prodotto **[!UICONTROL 24-MB01]** per ogni cliente e verificare che il prezzo visualizzato sia *$200*.
1. Cambia il gruppo di clienti per uno dei clienti in **Vendita al dettaglio**.
1. Cancellare la cache utilizzando il comando: `bin/magento cache:flush full_page`.
1. Aggiorna la pagina del prodotto per ogni cliente.

<u>Risultati previsti</u>:

1. Il cliente al dettaglio può visualizzare il prezzo corretto di *$30* per il prodotto.
1. Il cliente all&#39;ingrosso può visualizzare il prezzo corretto di *$200* per il prodotto.

<u>Risultati effettivi</u>:

1. Il cliente al dettaglio può visualizzare il prezzo corretto di *$30* per il prodotto.
1. Il cliente all&#39;ingrosso ha rilevato un prezzo errato di *$30* (prezzo al dettaglio) per il prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
