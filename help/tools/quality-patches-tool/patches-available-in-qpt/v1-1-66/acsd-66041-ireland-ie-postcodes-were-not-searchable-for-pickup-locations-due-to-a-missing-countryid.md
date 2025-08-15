---
title: 'ACSD-66041: Irlanda (IE) codici postali non ricercabili per località di prelievo a causa di CountryID mancante'
description: Applica la patch ACSD-66041 per risolvere il problema di Adobe Commerce, a causa del quale non era possibile cercare le località di prelievo in Irlanda (IE) a causa di un CountryID mancante.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 4c33da14-38b2-4a3c-a680-849b62dfb896
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-66041: Irlanda (IE) non è possibile cercare i percorsi di prelievo perché mancano `CountryID`

La patch ACSD-66041 risolve il problema per cui i codici postali di Irlanda (IE) non sono ricercabili per le posizioni di prelievo a causa di un `CountryID` mancante. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. L’ID della patch è ACSD-66041. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile cercare le località di prelievo in Irlanda (IE) a causa di un elemento `CountryID` mancante.

<u>Passaggi da riprodurre</u>:

1. Esegui la seguente query GraphQL:

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. Utilizza le seguenti variabili:

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>Risultati previsti</u>:

I codici postali irlandesi sono disponibili per cercare località di prelievo.

<u>Risultati effettivi</u>:

* *Errore interno del server* restituito.
* `var/log/exception.log` contiene il seguente errore:

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
