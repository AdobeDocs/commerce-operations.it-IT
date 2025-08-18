---
title: 'ACSD-67264: layout delle pagine dei prodotti in bundle e scaricabili non coerenti tra i dispositivi'
description: Applica la patch ACSD-67264 per risolvere i problemi di layout riscontrati nel bundle Adobe Commerce e nelle pagine scaricabili a causa di una ridisposizione del blocco multimediale con informazioni sul prodotto.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: layout delle pagine dei prodotti in bundle e scaricabili non coerenti tra i dispositivi

La patch ACSD-67264 risolve il problema che causa l’incoerenza tra il layout del bundle e quello delle pagine dei prodotti scaricabili nei diversi dispositivi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-67264. Questo problema è stato risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problemi di layout riscontrati nelle pagine dei prodotti bundle e scaricabili a causa di una ridisposizione del blocco multimediale di informazioni sui prodotti.

<u>Passaggi da riprodurre</u>:

1. Installa i dati di esempio.
1. Apri la pagina del prodotto del bundle e controlla il layout sul desktop.
1. Aggiungi la pagina del prodotto bundle alla lista dei desideri, passa alla lista dei desideri, fai clic sull’icona Modifica e controlla il layout.
1. Ripeti i passaggi 2 e 3 per un prodotto scaricabile.

<u>Risultati previsti</u>:

Viene eseguito il rendering del PDP del prodotto bundle senza alcun problema.

<u>Risultati effettivi</u>:

Viene eseguito il rendering del PDP del prodotto bundle con spazi casuali.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti
