---
title: 'ACSD-64532: la variabile ENV impostata su *false* viene trattata come stringa *false* invece di BOOLEAN *FALSE*'
description: Applica la patch ACSD-64532 per risolvere il problema di Adobe Commerce, dove una variabile "ENV" impostata su *false* viene trattata come una stringa *false* invece di un "BOOLEAN" *FALSE*.
feature: Variables
role: Admin, Developer
source-git-commit: 603b4f92ab3bbf4702d5373bd02dfdd770f57d5b
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# ACSD-64532: la variabile ENV impostata su &quot;false&quot; viene trattata come una stringa &quot;false&quot; invece di un BOOLEAN FALSE

La patch ACSD-64532 risolve il problema in cui la variabile `ENV` impostata su *false* viene trattata come stringa *false* invece di `BOOLEAN` *FALSE*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. L’ID della patch è ACSD-64532. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La variabile `ENV` impostata su *false* è trattata come stringa *false* invece di `BOOLEAN` *FALSE*.

<u>Passaggi da riprodurre</u>:
1. Aggiungi `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` con valore *false* alle variabili di ambiente in Adobe Commerce nell&#39;infrastruttura cloud.
1. Attendere la ridistribuzione.
1. Esegui lo script verificando il valore:

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>Risultati previsti</u>:
`$configParsedValue`, risultato del metodo `isUseApplicationLock()`, deve restituire un valore negativo per essere interpretato correttamente nel metodo `\Magento\Indexer\Model\Mview\View\State::getStatus()`.

<u>Risultati effettivi</u>:
`$configParsedValue` ha un valore di *`string(5) false`*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:
* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
