---
title: 'AC-14984: Problema di connessione SSL con php-amqplib/php-amqplib ^3.2.0'
description: Applica la patch AC-14984 per risolvere il problema Adobe Commerce, se la connessione SSL non riesce, con un errore, quando utilizzi php-amqplib/php-amqplib versione ^3.2.0.
feature: System
role: Admin, Developer
type: Troubleshooting
exl-id: cf46cd16-ef09-406a-835a-e5973887248f
source-git-commit: a934b02d42a5b9d2de722ebb6ef379ccca54649c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# AC-14984: Problema di connessione SSL con php-amqplib/php-amqplib ^3.2.0

La patch AC-14984 risolve il problema relativo all&#39;errore di connessione SSL quando si utilizza la versione `php-amqplib/php-amqplib` di `^3.2.0`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è AC-14984. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p10

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p10 - 2.4.6-p11

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La connessione SSL non riesce con un errore durante l&#39;utilizzo di `php-amqplib/php-amqplib` versione `^3.2.0`.

<u>Passaggi da riprodurre</u>:

1. Configurare la connessione SSL in `app/env.php`:

```
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
        'verify_peer' => true,
        'verify_peer_name' => false
      ],
    ),
  ),
```

1. Eseguire `bin/magento setup:upgrade` se questa è la prima volta che si configura la coda.
1. Esegui qualsiasi consumer di coda, ad esempio: `bin/magento queue:consumers:start async.operations.all`

<u>Risultati previsti</u>:

Il consumatore della coda avvia ed elabora i messaggi senza errori.

<u>Risultati effettivi</u>:

Nei registri viene visualizzato un messaggio di errore:

```
{
  "message": "Invalid frame type 21",
  "context": {},
  "level": "error",
  "level_name": "ERROR",
  "channel": "report",
  "datetime": "2025-05-14T07:00:00.000000+00:00",
  "extra": {},
  "@timestamp": "2025-05-14T07:00:00.000000X",
  "severity": "ERROR",
  "original_level": 400,
  "full_message": "Invalid frame type 21\n#0 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(651): PhpAmqpLib\\Connection\\AbstractConnection->wait_frame(3.0)\n#1 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(235): PhpAmqpLib\\Connection\\AbstractConnection->wait_channel(0, 3.0)\n#2 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(352): PhpAmqpLib\\Channel\\AbstractChannel->next_frame(3.0)\n#3 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(264): PhpAmqpLib\\Channel\\AbstractChannel->..."
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
