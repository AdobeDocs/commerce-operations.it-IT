---
title: 'ACSD-65684: l’aggiornamento di Magento_Company in B2B 1.5.2 è lento con oltre 100.000 record in company_structure'
description: Applica la patch ACSD-65684 per risolvere il problema di Adobe Commerce per cui l’aggiornamento del modulo Magento_Company in B2B 1.5.2 richiede troppo tempo a causa dell’elaborazione di un numero elevato di record (~100.000+) nella tabella company_structure.
feature: B2B
role: Admin, Developer
source-git-commit: dbf1bf3483aa7e52f5d1c950ab82f504c44fc989
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACSD-65684: l&#39;aggiornamento di `Magento_Company` in [!DNL B2B] 1.5.2 è lento con oltre 100.000 record in `company_structure`

La patch ACSD-65684 risolve un problema di prestazioni per cui l&#39;aggiornamento del modulo `Magento_Company` in [!DNL B2B] 1.5.2 richiede troppo tempo quando si elaborano più di 100.000 record nella tabella `company_structure`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-65684. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce B2B (tutti i metodi di implementazione) 1.5.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce B2B (tutti i metodi di implementazione) 1.5.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problema di prestazioni in cui l&#39;aggiornamento del modulo `Magento_Company` in [!DNL B2B] 1.5.2 richiede troppo tempo quando si elaborano più di 100.000 record nella tabella `company_structure`.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce 2.4.7-p4 con [!DNL B2B].
1. Aggiungere 100.000 record alla tabella `company_structure`.
1. Esegui l’aggiornamento ad Adobe Commerce 2.4.7-p5 e al modulo [!DNL B2B] più recente (1.5.2).
1. Applicare la patch ACSD-65540.
1. Esegui:

```
bin/magento setup:upgrade
```

<u>Risultati previsti</u>:

`setup:upgrade` viene completato in un tempo ragionevole.

<u>Risultati effettivi</u>:

Il completamento di `setup:upgrade` richiede troppo tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
