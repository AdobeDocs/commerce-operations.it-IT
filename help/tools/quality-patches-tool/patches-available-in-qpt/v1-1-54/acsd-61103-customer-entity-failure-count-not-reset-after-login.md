---
title: 'ACSD-61103: il conteggio degli errori non viene reimpostato su zero dopo il corretto accesso del cliente tramite API'
description: Applica la patch ACSD-61103 per risolvere il problema di Adobe Commerce, in cui il conteggio degli errori nella tabella "customer_entity" non viene reimpostato su zero dopo che un cliente ha effettuato correttamente l’accesso tramite gli endpoint API.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%
---
# ACSD-61103: il conteggio degli errori non viene reimpostato su zero dopo il corretto accesso del cliente tramite API

La patch ACSD-61103 risolve il problema per cui il conteggio degli errori nella tabella `customer_entity` non viene reimpostato su zero dopo che un cliente ha effettuato correttamente l&#39;accesso tramite gli endpoint API. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61103. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il conteggio degli errori nella tabella `customer_entity` non viene reimpostato su zero anche dopo che un cliente ha eseguito correttamente l&#39;accesso tramite endpoint API.

<u>Passaggi da riprodurre</u>:

1. Crea un account cliente.
1. Genera un token cliente tramite API utilizzando dettagli non corretti.
1. Controllare la colonna `failures_num` nella tabella del database `customer_entity` per il cliente in alto.
1. Genera un token cliente tramite API, utilizzando i dettagli corretti.
1. Controllare la colonna `failures_num` nella tabella del database `customer_entity` per il cliente in alto.

<u>Risultati previsti</u>:

La colonna `failures_num` deve essere reimpostata su 0 dopo aver utilizzato le credenziali corrette per generare un token cliente tramite API.

<u>Risultati effettivi</u>:

La colonna `failures_num` non viene reimpostata su 0 dopo aver utilizzato le credenziali corrette per generare un token cliente tramite API.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
