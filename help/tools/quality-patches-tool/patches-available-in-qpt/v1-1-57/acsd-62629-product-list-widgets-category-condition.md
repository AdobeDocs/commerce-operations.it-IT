---
title: 'ACSD-62629: l’elenco dei prodotti nei widget mostra categorie errate'
description: Applicare la patch ACSD-62629 per risolvere il problema Adobe Commerce, se un elenco di prodotti utilizzato nei widget non rispetta la condizione della categoria.
feature: Page Content
role: Admin, Developer
exl-id: a7d6bd43-4b8b-48c4-ae9a-4093ac3a4110
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-62629: l’elenco dei prodotti nei widget mostra categorie errate

La patch ACSD-62629 risolve il problema per cui l’elenco dei prodotti utilizzati nei widget non rispetta la condizione della categoria. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62629. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’elenco dei prodotti utilizzati nei widget non rispetta la condizione della categoria.

<u>Passaggi da riprodurre</u>:

1. Creare un [!UICONTROL simple product] denominato TEST e aggiungerlo alla categoria 1.
1. Crea un aggiornamento della gestione temporanea senza una data di fine per il prodotto TEST. Attendi che l’aggiornamento diventi attivo.
1. Creare un [!UICONTROL configurable product] denominato TEST 2 con due prodotti secondari e aggiungerlo alla categoria 2.
1. Creare un altro [!UICONTROL simple product] denominato TEST 5 e aggiungerlo alla categoria 1.
1. Esegui una reindicizzazione completa.
1. Passa a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** e modifica la home page.
1. Aggiungere un widget [!UICONTROL Products] con *[!UICONTROL Appearance]* impostato su *[!UICONTROL Product Carousel]* e *[!UICONTROL Category]* impostato su Category 2. Salva la pagina.
1. Vai al front-end e apri la pagina principale.

<u>Risultati previsti</u>:

Sulla pagina deve essere presente solo il prodotto TEST 2 (configurabile).

<u>Risultati effettivi</u>:

Sia i prodotti TEST 5 (semplice) che TEST 2 (configurabile) sono presenti nella pagina.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
