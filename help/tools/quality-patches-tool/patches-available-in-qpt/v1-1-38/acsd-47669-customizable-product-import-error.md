---
title: 'ACSD-47669: Errore interno del server durante l’importazione di prodotti con opzioni personalizzabili'
description: Applica la patch ACSD-47669 per risolvere il problema di Adobe Commerce in caso di errore interno del server durante l’importazione di prodotti con opzioni personalizzabili.
feature: Products
role: Admin, Developer
exl-id: e1a3b3b4-0392-4325-9766-a83276c1a593
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47669: Errore interno del server durante l’importazione di prodotti con opzioni personalizzabili

La patch ACSD-47669 risolve il problema relativo a un errore interno del server durante l’importazione del prodotto, con opzioni personalizzabili. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.38. L’ID della patch è ACSD-47669. Il problema è già risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore interno del server durante l’importazione di prodotti con opzioni personalizzabili.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;ulteriore visualizzazione store. Assicurati di avere 2 visualizzazioni del negozio, ad es. en, UK.
1. Create due prodotti semplici, ad esempio prod1 e prod2.
1. Prepara un file CSV che aggiunge opzioni personalizzate per entrambi i prodotti in ogni visualizzazione archivio e per l&#39;ambito **Tutte le visualizzazioni archivio**. Importa questo file CSV.
1. Prepara un altro file CSV che include due record. Il primo record deve aggiornare le opzioni personalizzate di &#39;prod1&#39; specificatamente per l&#39;ambito di visualizzazione dell&#39;archivio nel Regno Unito, mentre il secondo record deve aggiornare le opzioni personalizzate di &#39;prod2&#39; per l&#39;ambito **All Store View**. Importa questo secondo file CSV.

<u>Risultati previsti</u>:

Dovresti essere in grado di personalizzare le opzioni senza errori.

<u>Risultati effettivi</u>:

Si è verificato un errore di violazione del vincolo di integrità.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
