---
title: 'ACSD-63325: Errore di sintassi: errore imprevisto &lt;EOF&gt; durante l''invio di una richiesta vuota [!DNL GraphQL] '
description: Applica la patch ACSD-63325 per risolvere il problema Adobe Commerce in cui si verifica un errore di sintassi durante l'invio di una richiesta [!DNL GraphQL] vuota.
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325: &quot;Errore di sintassi: errore &lt; EOF > imprevisto&quot; durante l’invio di una richiesta [!DNL GraphQL] vuota

La patch ACSD-63325 risolve il problema relativo a un errore di &quot;Sintassi Error: Unexpected &lt; EOF >&quot; e a un codice di risposta non 200 restituito durante l&#39;invio di una richiesta [!DNL GraphQL] vuota. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63325. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si invia una richiesta [!DNL GraphQL] vuota, si verifica un errore interno del server HTTP invece di un codice di risposta 200.

<u>Passaggi da riprodurre</u>:

1. Invia una richiesta GraphQL vuota

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>Risultati previsti</u>:

Il codice di risposta per la richiesta è 200.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>Risultati effettivi</u>:

Si verifica un errore interno del server 500, come illustrato di seguito:

```
HTTP/1.1 500 Internal Server Error
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
