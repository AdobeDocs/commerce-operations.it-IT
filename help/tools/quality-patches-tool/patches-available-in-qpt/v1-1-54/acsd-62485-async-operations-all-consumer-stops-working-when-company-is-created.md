---
title: 'ACSD-62485: `async.operations.all` il consumatore smette di funzionare quando l’azienda viene creata'
description: Applica la patch ACSD-62485 per risolvere il problema di Adobe Commerce, in cui il consumatore "async.operations.all" smette di funzionare durante la creazione di un’azienda B2B.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '334'
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

   `bin/magento queue:consumer:start async.operations.all --max-messages=20000`

<u>Risultati previsti</u>:

Il consumatore elabora 20.000 messaggi e termina con successo.

<u>Risultati effettivi</u>:

Il consumatore smette di lavorare immediatamente al momento dell’esecuzione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
