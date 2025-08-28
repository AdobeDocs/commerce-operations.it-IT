---
title: 'ACSD-58108: si verificano errori SQL nell’estensione del modulo personalizzato della griglia dell’ordine a causa di un nome di tabella di join mancante'
description: Applica la patch ACSD-58108 per risolvere il problema Adobe Commerce, se un nome di tabella di join mancante nell’estensione del modulo personalizzato della griglia dell’ordine causa errori SQL durante il filtraggio di determinate colonne.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108: si verificano errori SQL nell’estensione del modulo personalizzato della griglia dell’ordine a causa di un nome di tabella di join mancante

La patch ACSD-58108 risolve il problema relativo a un nome di tabella di join mancante nell&#39;estensione del modulo personalizzato della griglia dell&#39;ordine che causa errori SQL durante il filtraggio di determinate colonne. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-58108. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il nome della tabella di join mancante nella tabella di recupero originale causa errori SQL nella griglia dell&#39;ordine quando si utilizza un&#39;estensione del modulo personalizzato. Questo problema si verifica perché la funzione `addFilterToMap` non funziona per alcune colonne dopo l&#39;unione alla tabella **[!UICONTROL sales_order_item]**, causando errori durante il filtraggio.

<u>Passaggi da riprodurre</u>:

&#x200B;01. Installa un’istanza di sviluppo 2.4.
&#x200B;02. Crea un nuovo ordine.
&#x200B;03. Installare un modulo personalizzato con un&#39;estensione SQL.
&#x200B;04. Passa a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
&#x200B;05. Applica il filtro **[!UICONTROL Purchase Date]** e attendi il risultato.
&#x200B;06. Applica filtro **[!UICONTROL Product SKU]**.

<u>Risultati previsti</u>:

Il filtro degli ordini nella griglia degli ordini funziona senza errori.

<u>Risultati effettivi</u>:

Si verifica un errore durante l’applicazione di filtri nella griglia dell’ordine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
