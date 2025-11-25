---
title: 'ACSD-63139: l’esportazione del prodotto non riesce quando gli attributi del prodotto contengono migliaia di valori di opzione'
description: Applica la patch ACSD-63139 per risolvere il problema di Adobe Commerce, in cui l’esportazione del prodotto non riesce se gli attributi del prodotto contengono migliaia di valori di opzione.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139: l’esportazione del prodotto non riesce quando gli attributi del prodotto contengono migliaia di valori di opzione

La patch ACSD-63139 risolve il problema se l’esportazione del prodotto non riesce quando gli attributi del prodotto contengono migliaia di valori di opzione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-63139. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione del prodotto ha esito negativo quando gli attributi del prodotto contengono migliaia di valori di opzione.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con il modulo B2B.
1. Importa un dump di database di grandi dimensioni con:
   - circa 7.000 prodotti
   - circa 450 attributi di prodotto
   - Alcuni attributi con più di 100 opzioni
1. Eseguire il comando seguente per installare cron (se non è già installato):

   ```
   bin/magento cron:install
   ```

1. Configura [!DNL RabbitMQ] seguendo le istruzioni in [[!DNL RabbitMQ] prerequisiti](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/message-brokers/rabbitmq).
1. Aprire il file `php.ini`, impostare il limite di memoria su 4G e riavviare il servizio PHP.
1. Nel pannello di amministrazione, vai a **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**.
1. Nella sezione *[!UICONTROL Export Settings]*, imposta **[!UICONTROL Entity Type]** su *Prodotti*, scorri verso il basso e fai clic su **[!UICONTROL Continue]**.
1. Esegui il comando seguente per avviare il processore di esportazione:

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>Risultati previsti</u>:

L’esportazione del prodotto deve essere completata correttamente.

<u>Risultati effettivi</u>:

Il processo di esportazione del prodotto non riesce e restituisce il seguente errore irreversibile:

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
