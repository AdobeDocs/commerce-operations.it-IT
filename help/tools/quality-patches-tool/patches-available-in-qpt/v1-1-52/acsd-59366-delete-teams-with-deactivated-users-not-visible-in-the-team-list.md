---
title: 'ACSD-59366: eliminare i team con utenti disattivati non visibili nell’elenco dei team'
description: Applica la patch ACSD-59366 per risolvere il problema di Adobe Commerce che si verifica quando si tenta di eliminare un team contenente utenti disattivati non visibili nell’elenco dei team.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: eliminare i team con utenti disattivati non visibili nell’elenco dei team

La patch ACSD-59366 risolve il problema relativo alla presenza di un errore quando si tenta di eliminare un team contenente utenti disattivati non visibili nell&#39;elenco dei team. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52. L’ID della patch è ACSD-59366. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore quando si elimina un team contenente utenti disattivati non visibili nell&#39;elenco dei team.

<u>Prerequisiti</u>:

I moduli B2B di Adobe Commerce sono installati e le aziende sono abilitate.

<u>Passaggi da riprodurre</u>:

1. Crea e accedi con un utente dell’azienda.
1. Crea un nuovo team sotto la struttura aziendale.
1. Crea un nuovo utente nel nuovo team.
1. Modifica il nuovo utente e disattiva.
1. Seleziona il team ed elimina.

<u>Risultati previsti</u>:

Il team ha uno o più utenti inattivi. Se si elimina il team, verrà annullata l’assegnazione di questi utenti. Gli utenti inattivi sono disponibili nella sezione [!UICONTROL Company Users].

<u>Risultati effettivi</u>:

Si verifica un errore quando si tenta di eliminare un team con un utente disattivato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
