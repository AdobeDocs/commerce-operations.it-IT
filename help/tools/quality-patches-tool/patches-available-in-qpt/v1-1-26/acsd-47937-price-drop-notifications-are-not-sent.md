---
title: 'ACSD-47937: notifiche di calo del prezzo non inviate a causa del caching a livello di applicazione'
description: Applica la patch ACSD-47937 per risolvere il problema di Adobe Commerce, in cui le notifiche di riduzione del prezzo non vengono sempre inviate a causa del caching a livello di applicazione.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: notifiche di calo del prezzo non inviate a causa del caching a livello di applicazione

La patch ACSD-47937 risolve il problema per cui le notifiche di riduzione del prezzo non vengono sempre inviate a causa del caching a livello di applicazione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. L’ID della patch è ACSD-47937. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 e 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4, 2.4.5 e 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti non ricevono l’e-mail di calo del prezzo del prodotto per le successive modifiche del prezzo del prodotto.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Product Alert]** per *[!UICONTROL Price Changes]* e *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Abilita **[!UICONTROL Display Out of Stock Products]**.
1. Creare un prodotto semplice (ABC) con qtà = 0.
1. Crea un cliente dalla vetrina e abbonati al prodotto sopra indicato per ricevere avvisi sui prodotti in caso di ribasso dei prezzi.
1. Avvia l’avviso sul prodotto per i clienti.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Abbassa il prezzo del prodotto ABC.
1. Attiva il cron di avviso del prodotto.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Abbassa di nuovo il prezzo del prodotto ABC.
1. Attiva il cron di avviso del prodotto.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Se non conosci lo strumento [!DNL n98], puoi eseguire `bin/magento cron:run command` come di consueto e monitorare la tabella `cron_schedule` per verificare che il processo `catalog_product_alert` ottenga lo stato di completamento.

<u>Risultati previsti</u>:

Viene inviata la seconda e-mail di riduzione del prezzo.

<u>Risultati effettivi</u>:

Il secondo messaggio e-mail di riduzione del prezzo non viene inviato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud

## Lettura correlata

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool]
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
