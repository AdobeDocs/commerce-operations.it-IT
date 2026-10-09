---
title: 'ACSD-61845: si verifica un errore per le richieste con intestazione di accettazione testo/html'
description: Applica la patch ACSD-61845 per risolvere il problema di Adobe Commerce, per cui l’invio di una richiesta HTTP con solo un’intestazione *text/html* accept causa un errore 500, con i moduli B2B installati.
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '356'
ht-degree: 0%
---
# ACSD-61845: si è verificato un errore per le richieste con *testo/html* intestazione di accettazione

La patch ACSD-61845 risolve il problema che causa un errore 500 a causa di una richiesta HTTP con solo un&#39;intestazione *text/html* accept a causa di mancata corrispondenza del tipo di file multimediale nella gestione delle risposte. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61845. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si invia una richiesta HTTP con solo *testo/html* nell&#39;intestazione Accept, si verifica un errore 500 a causa di una mancata corrispondenza nella configurazione del tipo di file multimediale.

<u>Prerequisiti</u>:

I moduli B2B vengono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Invia una richiesta con solo *testo/html* nell&#39;intestazione Accetta, come segue:

   ```shell
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Risultati previsti</u>:

La pagina viene restituita con un codice di stato *200*.

<u>Risultati effettivi</u>:

Viene restituito un errore 500 con il seguente messaggio di errore in `exception.log`:

```text
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
