---
title: 'ACSD-64732: controller di terze parti non memorizzati correttamente nella cache con i segmenti dei clienti'
description: Applica la patch ACSD-64732 per risolvere il problema di Adobe Commerce, a causa del quale i controller di terze parti non vengono memorizzati correttamente nella cache con i segmenti dei clienti.
feature: Cache
role: Admin, Developer
source-git-commit: 047de42098f711036f1f5252d2cbc4a329ebbfb2
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---


# ACSD-64732: controller di terze parti non memorizzati correttamente nella cache con i segmenti dei clienti

La patch ACSD-64732 risolve il problema che impediva la corretta memorizzazione nella cache dei controller di terze parti con i segmenti dei clienti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. L’ID della patch è ACSD-64732. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I controller di terze parti non vengono memorizzati correttamente nella cache con i segmenti dei clienti.

<u>Passaggi da riprodurre</u>:

1. Passa al controller personalizzato (/catalog/category/vary).
1. Vai alla scheda **[!UICONTROL Network]** e controlla il valore di **[!DNL X-Magento-Vary]**.

<u>Risultati previsti</u>:

Il valore **[!UICONTROL X-Magento-Vary]** deve essere lo stesso nel controller personalizzato.

<u>Risultati effettivi</u>:

Il valore di **[!UICONTROL X-Magento-Vary]** è diverso e ciò causa mancati riscontri nella cache. Ciò significa che la cache generata in precedenza non può essere utilizzata quando si visita il controller personalizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
