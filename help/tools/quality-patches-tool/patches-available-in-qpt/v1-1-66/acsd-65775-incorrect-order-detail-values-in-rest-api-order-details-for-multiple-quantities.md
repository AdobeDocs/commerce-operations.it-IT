---
title: 'ACSD-65775: valori "base_row_total" e "row_total" errati nei dettagli dell’ordine API REST per quantità multiple'
description: Applica la patch ACSD-65775 per risolvere il problema di Adobe Commerce, in cui i dettagli dell’ordine API REST restituiscono valori "base_row_total" e "row_total" errati quando vengono ordinate più quantità dello stesso articolo.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: c2a8f4ef-3998-4e73-af9e-69b17a10d684
source-git-commit: ce5a136dd59c52d5fa5b555b3ee74fe14d7e53a4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-65775: valori `base_row_total` e `row_total` non corretti nei dettagli dell&#39;ordine API REST per più quantità

La patch ACSD-65775 risolve il problema per cui i dettagli dell’ordine REST API restituiscono valori `base_row_total` e `row_total` errati quando vengono ordinate più quantità dello stesso elemento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACSD-65775. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I valori `base_row_total` e `row_total` nella risposta REST API per i dettagli dell&#39;ordine mostrano il prezzo unitario anziché il prezzo totale quando vengono ordinate più quantità dello stesso articolo.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti semplici: simple1 con prezzo di 10 $ e simple2 con prezzo di 15 $.
1. Crea un nuovo account cliente.
1. Aggiungere simple1 al carrello con quantità 2 e simple2 con quantità 3.
1. Effettuare l&#39;ordine utilizzando il conto cliente.
1. Ottenere un token di amministrazione inviando una richiesta POST a `/rest/V1/integration/admin/token` con il seguente payload:

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Recuperare i dettagli dell&#39;ordine utilizzando una richiesta GET a `/rest/default/V1/orders/1`.

<u>Risultati previsti</u>:

`base_row_total` e `row_total` devono riflettere il prezzo totale calcolato come quantità moltiplicata per il prezzo dell&#39;articolo (ad esempio, 2 × $10 = $20 per simple1).

<u>Risultati effettivi</u>:

`base_row_total` e `row_total` restituiscono solo il prezzo unitario (ad esempio, $10 per simple1 anziché $20).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
