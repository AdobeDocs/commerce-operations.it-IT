---
title: 'ACSD-61969: necessario per digitare il codice coupon come configurato in maiuscolo o minuscolo'
description: Applica la patch ACSD-61969 per risolvere il problema Adobe Commerce, in cui a un utente viene richiesto di digitare il codice del coupon esattamente come configurato in maiuscolo o minuscolo.
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: necessario per digitare il codice coupon come configurato in maiuscolo o minuscolo

La patch ACSD-61969 risolve il problema che impone all’utente di digitare il codice del coupon esattamente come configurato in maiuscolo o minuscolo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. L’ID della patch è ACSD-61969. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando applichi il codice del coupon dal backend, devi digitare esattamente come configurato in maiuscolo o in minuscolo. Per la creazione dell’ordine amministratore, fanno distinzione tra maiuscole e minuscole, ma non per la vetrina.

<u>Passaggi da riprodurre</u>:

1. Creare un *[!UICONTROL Cart Price Rule]* con un coupon specifico *TEST*. Assicurati che il codice del coupon sia in maiuscolo.
1. Crea un ordine in Amministratore.
1. Aggiungi *test* al campo *[!UICONTROL Apply Coupon Code]* e fai clic sulla freccia accanto al campo per applicare il coupon.
1. Osserva il risultato.

<u>Risultati previsti</u>:

Il coupon viene applicato correttamente. Nel campo coupon non viene fatta distinzione tra maiuscole e minuscole.

<u>Risultati effettivi</u>:

Il coupon non viene applicato. Viene visualizzato il seguente errore:

*Il codice coupon &quot;test&quot; non è valido. Verificare il codice e riprovare.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
