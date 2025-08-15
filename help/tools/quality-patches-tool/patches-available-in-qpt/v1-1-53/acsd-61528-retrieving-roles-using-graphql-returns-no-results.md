---
title: 'ACSD-61528: il recupero dei ruoli tramite GraphQL non restituisce alcun risultato'
description: Applica la patch ACSD-61528 per risolvere il problema di Adobe Commerce per cui il recupero dei ruoli dall’amministratore dell’azienda tramite GraphQL restituisce sempre un risultato nullo.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 81d78746-e723-4b18-860c-d973158b469c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528: il recupero dei ruoli tramite GraphQL non restituisce alcun risultato

La patch ACSD-61258 risolve il problema per cui il recupero dei ruoli dall’amministratore dell’azienda tramite GraphQL restituisce sempre un risultato nullo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. L’ID della patch è ACSD-61528. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si recuperavano i ruoli dall’amministratore della società utilizzando GraphQL, il risultato del ruolo era sempre nullo.

<u>Prerequisiti:</u>:

Installare e abilitare i moduli B2B di Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Crea una società.
1. Accedi come amministratore dell’azienda su GraphQL con la seguente mutazione:

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Aggiungi il token risultante alle intestazioni di richiesta **Authorization** come token `Bearer` ed eseguilo sotto la query GraphQL:

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u>Risultati previsti</u>:

La query GraphQL restituisce il ruolo.

<u>Risultati effettivi</u>:

Il ruolo della società è nullo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
