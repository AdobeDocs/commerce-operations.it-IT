---
title: 'AC-14985: Errore durante l’invio di e-mail SMTP tramite TLS'
description: Applica la patch AC-14985 per risolvere il problema Adobe Commerce che si verifica quando si invia un’e-mail SMTP (Simple Mail Transfer Protocol) tramite Transport Layer Security (TLS).
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# AC-14985: Errore durante l’invio di e-mail SMTP tramite TLS

La patch AC-14985 risolve un problema che si verificava durante l’invio di e-mail SMTP (Simple Mail Transfer Protocol) tramite Transport Layer Security (TLS). Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è AC-14985. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore durante l’invio di e-mail tramite SMTP con TLS abilitato.

<u>Passaggi da riprodurre</u>:

1. Imposta la configurazione SMTP come segue:
* Trasporto: SMTP
* Host: url.to.smtp.host
* Porta: 587
* SSL: TLS

<u>Risultati previsti</u>:

L’e-mail viene inviata correttamente senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
