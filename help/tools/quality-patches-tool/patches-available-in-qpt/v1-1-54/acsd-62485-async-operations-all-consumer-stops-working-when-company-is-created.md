---
title: '"ACSD-62485: "async.operations.all" il consumatore smette di funzionare durante la creazione dell’azienda"'
description: Applica la patch ACSD-62485 per risolvere il problema di Adobe Commerce, in cui il consumatore "async.operations.all" smette di funzionare durante la creazione di un’azienda B2B.
feature: B2B, Companies
role: Admin, Developer
source-git-commit: 8061f6df01c3c308b46e6164300192b01359ce94
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: il consumatore `async.operations.all` smette di funzionare al momento della creazione della società

La patch ACSD-62485 risolve il problema relativo alla cessazione del funzionamento del consumer `async.operations.all` al momento della creazione di un&#39;azienda B2B. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-62485. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il consumer `async.operations.all` interrompe l&#39;elaborazione dei messaggi se una società B2B viene creata in modo asincrono mentre il consumer è ancora in esecuzione.

<u>Prerequisiti</u>:

I moduli B2B vengono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Crea due clienti.
1. Invia una richiesta REST in blocco per creare due società, assegnando i clienti creati come amministratori aziendali.
1. Avvia il consumer utilizzando il comando seguente:

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Risultati previsti</u>:

Il consumatore elabora 20.000 messaggi e termina con successo.

<u>Risultati effettivi</u>:

Il consumatore smette di lavorare immediatamente al momento dell’esecuzione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
