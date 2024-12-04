---
title: 'ACSD-60344: e-mail di conferma dell''ordine duplicate all''utilizzo di [!UICONTROL Purchase Order] con approvazione automatica'
description: Applicare la patch ACSD-60344 per risolvere il problema Adobe Commerce relativo all'invio di e-mail di conferma dell'ordine duplicate quando si utilizza [!UICONTROL Purchase Order] con approvazione automatica.
feature: Purchase Orders
role: Admin, Developer
source-git-commit: afa03b31e4af0be1ebc0d12aabd4f9d8be17d1fe
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: e-mail di conferma dell&#39;ordine duplicate all&#39;utilizzo di *[!UICONTROL Purchase Order]* con approvazione automatica

La patch ACSD-60344 risolve il problema relativo all&#39;invio di e-mail di conferma dell&#39;ordine duplicate quando si utilizza *[!UICONTROL Purchase Order]* con l&#39;approvazione automatica. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-60344. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le e-mail di conferma dell&#39;ordine duplicate vengono inviate quando si utilizza *[!UICONTROL Purchase Order]* con l&#39;approvazione automatica.

<u>Prerequisiti</u>

Abilita moduli B2B e *[!UICONTROL Purchase Order]*.

<u>Passaggi da riprodurre</u>:

1. Creare un account aziendale e abilitare *[!UICONTROL Purchase Order]* per tale account.
1. Crea un account utente normale e aggiungilo all&#39;account aziendale come utente aziendale.
1. Effettua un ordine utilizzando questo account.
1. Esegui cron e controlla le e-mail.

<u>Risultati previsti</u>:

Viene ricevuta una sola e-mail di conferma dell’ordine per ogni ordine.

<u>Risultati effettivi</u>:

Vengono ricevute due e-mail di conferma dell’ordine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
