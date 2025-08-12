---
title: 'ACSD-66301: lo spostamento di prodotti da un ordine al carrello in Commerce Admin determina una mancata corrispondenza della quantità'
description: Applica la patch ACSD-66301 per risolvere il problema di Adobe Commerce per cui, durante la creazione di un ordine dal pannello di amministrazione, i prodotti nel carrello del cliente non vengono rimossi dopo l’aggiunta all’ordine.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9a4224c02634514a9428dc6b0daf4c1d5f5c7c43
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-66301: lo spostamento di prodotti da un ordine al carrello in Commerce Admin determina una mancata corrispondenza della quantità

La patch ACSD-66301 risolve il problema della mancata corrispondenza delle quantità dovuta allo spostamento di prodotti da un ordine al carrello nell’Admin. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66301. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p10, 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo spostamento di prodotti da un ordine al carrello in Commerce Admin genera una mancata corrispondenza della quantità.

<u>Passaggi da riprodurre</u>:

1. Crea un utente tramite la vetrina.
2. Aggiungi un prodotto al carrello con quantità = *5*.
3. Vai al pannello Amministratore e apri l’account utente in cui è stato aggiunto il prodotto.
4. Fare clic su **[!UICONTROL Create Order]**.
5. Nel pannello a sinistra puoi visualizzare le attività del cliente, incluso il prodotto e la quantità aggiunti.
6. Aggiungi il prodotto all’ordine.
7. Aggiornare la quantità = *4* nella sezione dell&#39;ordine principale.
8. Fare clic sul pulsante **[!UICONTROL Update Items and Quantities]**.
9. Trasferisci gli articoli selezionati dall’ordine al carrello del cliente.

<u>Risultati previsti</u>:

Prodotto aggiunto al carrello con la nuova quantità = *4*.

<u>Risultati effettivi</u>:

Prodotto aggiunto al carrello con la quantità precedente = *5*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
