---
title: 'ACSD-56226: le query READ restituiscono dati obsoleti con "synchronous_replication" abilitato'
description: Applica la patch ACSD-56226 per risolvere il problema di Adobe Commerce in cui le query READ restituiscono dati obsoleti quando il flag "synchronous_replication" è abilitato per la connessione slave su Cloud.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226: le query READ restituiscono dati obsoleti con `synchronous_replication` abilitato

La patch ACSD-56226 risolve il problema per cui le query READ restituiscono dati obsoleti quando il flag `synchronous_replication` è abilitato per la connessione slave su Cloud. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-56226. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le query READ restituiscono dati obsoleti quando il flag `synchronous_replication` è abilitato. Questo causa la disattivazione della connessione slave, con conseguente sovraccarico del database.

<u>Passaggi da riprodurre</u>:

1. Imposta `MYSQL_USE_SLAVE_CONNECTION` su *true* nelle variabili di ambiente in Adobe Commerce nell&#39;infrastruttura cloud.
1. Aggiungi la seguente configurazione a `.magento.env.yaml` per impostare `synchronous_replication` su *false*:

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Ridistribuisci ed esegui azioni front-end come accesso, aggiungi al carrello o effettua un ordine.

<u>Risultati previsti</u>:

La connessione slave rimane abilitata quando `synchronous_replication` è impostato su *false*.

<u>Risultati effettivi</u>:

La connessione slave è disabilitata quando `synchronous_replication` è impostato su *false*, causando un sovraccarico del database.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
