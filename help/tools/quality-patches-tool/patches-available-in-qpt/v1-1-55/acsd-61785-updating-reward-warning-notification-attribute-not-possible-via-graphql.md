---
title: 'ACSD-61785: impossibile aggiornare l’attributo reward_warning_notification tramite la mutazione GraphQL e le chiamate API REST'
description: Applica la patch ACSD-61785 per risolvere il problema di Adobe Commerce per cui l’aggiornamento dell’attributo "reward_warning_notification" non è possibile tramite la mutazione GraphQL e le chiamate API REST.
feature: REST, GraphQL, Rewards
role: Admin, Developer
source-git-commit: 87ce6004a632f860447d55c13c08f78533ab093e
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: impossibile aggiornare l’attributo reward_warning_notification tramite la mutazione GraphQL e le chiamate API REST

La patch ACSD-61785 risolve il problema per cui l&#39;aggiornamento dell&#39;attributo `reward_warning_notification` non è possibile tramite la mutazione GraphQL e le chiamate REST API. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-61785. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento dell&#39;attributo `reward_warning_notification` non è possibile tramite la mutazione GraphQL e le chiamate API REST.

<u>Passaggi da riprodurre</u>:

1. Controlla lo schema/documentazione API GraphQL e REST per *Abbonati per aggiornamenti saldo* e *Abbonati per notifiche di scadenza punti*.

<u>Risultati previsti</u>:

È possibile sottoscrivere *Aggiornamenti dei saldi dei premi* e *Notifiche di scadenza dei punti* tramite GraphQL e REST API.

<u>Risultati effettivi</u>:

GraphQL e REST API non dispongono di questa funzionalità.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
