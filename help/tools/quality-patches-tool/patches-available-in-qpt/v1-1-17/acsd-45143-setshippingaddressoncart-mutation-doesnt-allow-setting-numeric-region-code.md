---
title: "ACSD-45143: la mutazione setShippingAddressesOnCart non imposta il codice di regione numerico come 'region'"
description: La patch ACSD-45143 risolve il problema per cui la mutazione setShippingAddressesOnCart non consente di impostare il codice di regione numerico come "region". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45143. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-45143: la mutazione setShippingAddressesOnCart non imposta il codice di regione numerico come &#39;region&#39;

La patch ACSD-45143 risolve il problema per cui la mutazione setShippingAddressesOnCart non consente di impostare il codice di regione numerico come &quot;region&quot;. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45143. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La mutazione setShippingAddressesOnCart non consente di impostare il codice di area numerico come &quot;region&quot;.

<u>Passaggi da riprodurre</u>:

1. Crea un carrello utilizzando la query seguente.

   <pre>
    <code class="language-graphql">
    mutation {
      createEmptyCart
    }
    </code>
    </pre>

1. Invia una richiesta per impostare l’indirizzo di spedizione sul carrello.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) {
      setShippingAddressesOnCart(
        input: {
          cart_id: $cartId
          shipping_addresses: {
            address: {
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            }
          }
        }
        ) {
          cart {
            shipping_addresses {
              firstname
              lastname
              company
              street
              city
              region {
                code
                label
              }
              postcode
              telephone
              country {
                code
                label
              }
            }
          }
        }
      }
      </code>
      </pre>

   Nota: in questo esempio, il codice paese è impostato su &quot;FR&quot; e il codice regione su &quot;58&quot;. In base alla tabella `directory_country_region` DB, il codice di regione 58 è &quot;Nièvre&quot;.

1. Controlla la risposta restituita.

<u>Risultati previsti</u>:

Adobe Commerce consente di impostare il codice di regione numerico nella richiesta GraphQL.

<u>Risultati effettivi</u>:

Il codice di regione viene modificato in 47.

<pre>
<code class="language-graphql">
{
  "data": {
    "setShippingAddressesOnCart": {
      "cart": {
        "shipping_addresses": [
        {
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": [
          "234 Rue de Rivoli"
          ],
          "city": "Lille",
          "region": {
            "code": "47",
            "label": "Lot-et-Garonne"
            },
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": {
              "code": "FR",
              "label": "FR"
            }
          }
        ]
      }
    }
  }
}
</code>
</pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].