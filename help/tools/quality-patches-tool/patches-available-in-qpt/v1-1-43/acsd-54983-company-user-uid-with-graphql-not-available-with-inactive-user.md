---
title: 'ACSD-54983: Utente aziendale UID con GraphQL non disponibile con utente inattivo'
description: Applica la patch ACSD-54983 per risolvere il problema di Adobe Commerce, se non è possibile ottenere la richiesta dell’utente aziendale UID con GraphQL quando lo stato utente è impostato su inattivo.
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: Utente aziendale UID con GraphQL non disponibile con utente inattivo

La patch ACSD-54983 risolve il problema quando non è possibile ottenere la richiesta dell’utente dell’azienda UID con GraphQL quando lo stato dell’utente è impostato su inattivo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. L’ID della patch è ACSD-54983. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile ottenere la richiesta dell’utente aziendale UID con GraphQL quando lo stato dell’utente è impostato su inattivo.

<u>Passaggi da riprodurre</u>:

1. Crea un’azienda con un utente amministratore. Ad esempio, company@test.com.
1. Crea un nuovo cliente.
1. Assegnare il nuovo cliente a una società.
1. Ottieni **[!UICONTROL company admin token]**.
1. Utilizzando **[!UICONTROL company admin token]**, recupera la struttura aziendale. Consulta [Restituire la struttura aziendale](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) nella documentazione per gli sviluppatori.
1. La risposta contiene solo *ACTIVE* clienti con i loro ID.
1. Aggiorna l&#39;utente della società a *INACTIVE*.
1. Recupera di nuovo la struttura aziendale.

<u>Risultati previsti</u>:

È possibile ottenere l’utente aziendale UID quando lo stato è impostato su inattivo.

<u>Risultati effettivi</u>:

I clienti inattivi non sono presenti nell&#39;elenco. Impossibile ottenere l’UID dell’utente della società quando lo stato è impostato su inattivo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
