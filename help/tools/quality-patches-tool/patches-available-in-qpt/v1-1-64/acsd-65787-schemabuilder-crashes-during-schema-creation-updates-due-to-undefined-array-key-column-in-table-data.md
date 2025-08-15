---
title: 'ACSD-65787: SchemaBuilder si blocca durante la creazione o l’aggiornamento dello schema a causa di una "colonna" della chiave di array non definita nei dati della tabella'
description: Applica la patch ACSD-65787 per risolvere il problema di Adobe Commerce in cui la classe SchemaBuilder si blocca durante la creazione dello schema o gli aggiornamenti a causa di una "colonna" di chiave di array non definita durante l’elaborazione dei dati della tabella.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787: `SchemaBuilder` si blocca durante la creazione o l&#39;aggiornamento dello schema a causa di una &quot;colonna&quot; della chiave di array non definita nei dati della tabella

La patch ACSD-65787 risolve il problema relativo agli arresti anomali della classe `SchemaBuilder` durante la creazione dello schema o gli aggiornamenti a causa di una &quot;colonna&quot; di chiave di matrice non definita durante l&#39;elaborazione dei dati della tabella. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-65787. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La classe `SchemaBuilder` si blocca durante la creazione dello schema o gli aggiornamenti a causa di una &quot;colonna&quot; di chiave di matrice non definita durante l&#39;elaborazione dei dati della tabella.

<u>Passaggi da riprodurre</u>:

1. Esegui il comando seguente:

```
bin/magento setup:upgrade
```

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
