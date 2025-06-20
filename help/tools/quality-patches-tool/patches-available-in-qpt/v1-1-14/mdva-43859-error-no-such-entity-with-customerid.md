---
title: 'MDVA-43859: errore "Nessuna entità di questo tipo con customerId =" registrato al momento dell''accesso del cliente eliminato'
description: La patch di MDVA-43859 risolve il problema relativo all'errore *Nessuna entità con customerId =* viene registrata quando un cliente eliminato tenta di accedere. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L'ID della patch è MDVA-43859. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859: errore &quot;Nessuna entità di questo tipo con customerId =&quot; registrato al momento dell&#39;accesso del cliente eliminato

La patch di MDVA-43859 risolve il problema relativo all&#39;errore *Nessuna entità con customerId =* viene registrata quando un cliente eliminato tenta di accedere. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L&#39;ID della patch è MDVA-43859. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore *Nessuna entità di questo tipo con customerId =* viene registrata quando un cliente eliminato tenta di accedere.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente dal front-end.
1. Esci e accedi all&#39;account cliente creato nel passaggio 1.
1. Carica il backend in un altro browser e passa alla griglia del cliente.
1. Elimina il cliente creato nel passaggio 1.
1. Torna al primo browser e prova a disconnetterti.

<u>Risultati previsti</u>:

Il cliente viene reindirizzato alla pagina di accesso senza alcun errore.

<u>Risultati effettivi</u>:

Il cliente riceve il seguente errore: *Nessuna entità con customerId =*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
