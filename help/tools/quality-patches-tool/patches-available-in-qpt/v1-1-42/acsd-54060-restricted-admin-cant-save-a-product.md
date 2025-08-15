---
title: 'ACSD-54060: l’amministratore con restrizioni non può salvare il prodotto se è figlio di un altro prodotto'
description: Applica la patch ACSD-54060 per risolvere il problema di Adobe Commerce, a causa del quale un amministratore con restrizioni non è in grado di salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso.
feature: Admin Workspace, Roles/Permissions, Products
role: Admin, Developer
exl-id: 2af24cbf-65a1-4bd6-aad3-19b613bee7f2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-54060: l’amministratore con restrizioni non può salvare il prodotto se è figlio di un altro prodotto

La patch ACSD-54060 risolve il problema che impedisce a un amministratore con restrizioni di salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42. L’ID della patch è ACSD-54060. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un amministratore con restrizioni non è in grado di salvare un prodotto se è figlio di un altro prodotto assegnato a un ambito diverso.

<u>Passaggi da riprodurre</u>:

1. Crea un altro sito web.
1. Crea un prodotto semplice e assegnalo a entrambi i siti web.
1. Crea un prodotto configurabile con il prodotto semplice come unica variante e assegna il prodotto configurabile solo al sito Web predefinito.
1. Crea un utente amministratore con restrizioni con accesso solo al secondo sito Web.
1. Accedi come utente amministratore con restrizioni.
1. Prova a modificare il nome del prodotto semplice nel secondo ambito del sito web.

<u>Risultati previsti</u>:

L’amministratore con restrizioni può modificare il nome del prodotto.

<u>Risultati effettivi</u>:

Errore: *Per visualizzare l&#39;elemento sono necessarie altre autorizzazioni*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
