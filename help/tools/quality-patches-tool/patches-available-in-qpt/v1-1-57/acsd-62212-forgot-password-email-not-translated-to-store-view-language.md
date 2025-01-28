---
title: 'ACSD-62212: l''e-mail [!UICONTROL Forgot Password] non è stata tradotta nella lingua di visualizzazione dello store'
description: Applica la patch ACSD-62212 per risolvere il problema Adobe Commerce per cui il contenuto dell'e-mail *[!UICONTROL Forgot Password]* non viene tradotto nella lingua della visualizzazione archivio.
feature: GraphQL
role: Admin, Developer
exl-id: 29e6f2fa-574f-4ab1-82f5-88e1eb1de83e
source-git-commit: 8f39f7838d5c98a1dcc584edf766393012ec8820
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-62212: l&#39;e-mail *[!UICONTROL Forgot Password]* non è stata tradotta nella lingua di visualizzazione dello store

La patch ACSD-62212 risolve il problema per cui il contenuto dell&#39;e-mail *[!UICONTROL Forgot Password]* non viene tradotto nel linguaggio di visualizzazione dello store. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57. L’ID della patch è ACSD-62212. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si reimposta la password tramite GraphQL in una visualizzazione diversa da quella registrata, il collegamento di reimpostazione della password non corrisponde alla visualizzazione dello store da cui è stata avviata.

<u>Passaggi da riprodurre</u>:

1. Creare una visualizzazione archivio secondario in *[!UICONTROL Main Website Store]*.
1. Passa da *[!UICONTROL Locale]* a *[!UICONTROL French (France)]* nell&#39;ambito di visualizzazione dell&#39;archivio secondario.
1. Installa il Language Pack per le traduzioni in francese.
1. Crea un account cliente.
1. Utilizza la seguente mutazione di GraphQL con intestazione *store* con il codice di visualizzazione dell&#39;archivio secondario.

   ```
   mutation {
       requestPasswordResetEmail(
           email: "test@gmail.com"
       )
   }
   ```

1. Controlla l’e-mail.

<u>Risultati previsti</u>:

* La lingua dell’oggetto, del collegamento e del contenuto dell’e-mail è coerente con la lingua della visualizzazione archivio.
* La richiesta di reimpostazione della password viene inviata dallo store in cui è effettivamente registrato l’account del cliente, indipendentemente dall’intestazione dello store nella richiesta.

<u>Risultati effettivi</u>:

Nell’e-mail si è osservato quanto segue:

* Il collegamento per reimpostare la password contiene il codice di archiviazione &quot;predefinito&quot;.
* L&#39;argomento è in inglese.
* Il contenuto è in francese.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
