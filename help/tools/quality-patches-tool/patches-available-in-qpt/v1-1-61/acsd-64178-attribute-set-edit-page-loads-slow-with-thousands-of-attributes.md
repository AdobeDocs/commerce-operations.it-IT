---
title: 'ACSD-64178: la pagina [!UICONTROL Edit Attribute Set] viene caricata lentamente con migliaia di attributi di prodotto'
description: Applicare la patch ACSD-64178 per risolvere il problema di Adobe Commerce, in cui la pagina [!UICONTROL Edit Attribute Set] viene caricata lentamente se sono presenti migliaia di attributi di prodotto.
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178: la pagina [!UICONTROL Edit Attribute Set] viene caricata lentamente con migliaia di attributi di prodotto

La patch ACSD-64178 risolve il problema relativo al caricamento lento della pagina **[!UICONTROL Edit Attribute Set]** se sono presenti migliaia di attributi di prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-64178. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La pagina **[!UICONTROL Edit Attribute Set]** viene caricata lentamente se sono presenti migliaia di attributi di prodotto.

<u>Passaggi da riprodurre</u>:

1. Creare almeno 4200 attributi non assegnati a nessuno dei set di attributi.
1. Nella barra laterale di amministrazione, vai a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]**. Fai clic su un set di attributi da modificare.

<u>Risultati previsti</u>:

La pagina viene caricata in un tempo ragionevole.

<u>Risultati effettivi</u>:

Il caricamento della pagina richiede diversi minuti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
