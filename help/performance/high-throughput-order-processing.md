---
title: Elaborazione dell'ordine ad alta velocità
description: Ottimizza la posizione dell’ordine e l’esperienza di pagamento per la distribuzione Adobe Commerce o Magenti Open Source.
source-git-commit: c4c52baa9e04a4e935ccc29fcce2ac2745a454ee
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---


# Elaborazione dell&#39;ordine ad alta velocità

Puoi ottimizzare l’esperienza di posizionamento e di pagamento dell’ordine configurando il seguente set di moduli per **elaborazione dell&#39;ordine ad alta velocità**:

- [AsyncOrder](#asynchronous-order-placement)- Elabora in modo asincrono gli ordini utilizzando una coda.
- [Calcolo totale differito](#deferred-total-calculation)- Consente di trasferire i calcoli per i totali degli ordini fino all&#39;inizio del pagamento.
- [Controllo dell&#39;inventario al caricamento del preventivo](#disable-inventory-check)- Consente di saltare la convalida dell&#39;inventario degli articoli del carrello.

Tutte le funzioni - Ordine asincrono, Calcolo totale differito e Controllo scorte - funzionano in modo indipendente. È possibile utilizzare tutte e tre le funzioni contemporaneamente oppure attivare e disattivare le funzioni in qualsiasi combinazione.

## Posizionamento dell’ordine asincrono

La _Ordine asincrono_ il modulo abilita il posizionamento asincrono dell’ordine, che contrassegna l’ordine come `received`, inserisce l’ordine in una coda ed elabora gli ordini dalla coda in base al principio &quot;first in first out&quot;. AsyncOrder è **disattivato** per impostazione predefinita.

Ad esempio, un cliente aggiunge un prodotto al suo carrello e seleziona **[!UICONTROL Proceed to Checkout]**. Compilano **[!UICONTROL Shipping Address]** modulo, selezionare il modulo desiderato **[!UICONTROL Shipping Method]**, selezionare un metodo di pagamento e inserire l&#39;ordine. Il carrello è cancellato, l&#39;ordine è contrassegnato come **[!UICONTROL Received]**, ma la quantità del prodotto non viene ancora adeguata, né viene inviato un messaggio e-mail di vendita al cliente. L&#39;ordine viene ricevuto, ma i dettagli dell&#39;ordine non sono ancora disponibili perché l&#39;ordine non è stato completamente elaborato. Rimane in coda fino al `placeOrderProcess` il consumatore inizia, verifica l&#39;ordine con [controllo inventario](#disable-inventory-check) (abilitato per impostazione predefinita) e aggiorna l’ordine nel modo seguente:

- **Prodotto disponibile**- lo stato dell&#39;ordine cambia in _In sospeso_, la quantità del prodotto viene modificata, viene inviata al cliente un’e-mail con i dettagli dell’ordine e i dettagli dell’ordine con esito positivo diventano disponibili per la visualizzazione nel **Ordini e restituzioni** elenco con opzioni utilizzabili, ad esempio riordino.
- **Prodotto esaurito o a basso consumo**- lo stato dell&#39;ordine cambia in _Rifiutato_, la quantità di prodotto non viene modificata, viene inviata al cliente un’e-mail con i dettagli dell’ordine relativi al problema e i dettagli dell’ordine rifiutato diventano disponibili nella variabile **Ordini e restituzioni** elenco senza opzioni utilizzabili.

Utilizzare l&#39;interfaccia della riga di comando per abilitare queste funzionalità o modificare il `app/etc/env.php` file in base ai corrispondenti file README definiti nel [_Guida di riferimento del modulo_][mrg].

**Per abilitare AsyncOrder**:

È possibile abilitare AsyncOrder utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --checkout-async 1
```

La `set` scrive quanto segue nel `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Vedi [AsyncOrder] in _Guida di riferimento del modulo_.

**Per disabilitare AsyncOrder**:

>[!WARNING]
>
>Prima di disabilitare il modulo AsyncOrder, è necessario verificare che _tutto_ processi di ordine asincroni completati.

È possibile disabilitare AsyncOrder utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --checkout-async 0
```

La `set` scrive quanto segue nel `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilità AsyncOrder

AsyncOrder supporta un set limitato di [!DNL Commerce] funzionalità.

| Categoria | Funzione supportata |
|---------------- | -----------------------|
| Tipi di pagamento | Checkout di una pagina<br>Pagamento standard<br>Preventivo Negoziabile B2B |
| Metodi di pagamento | Ordine di pagamento<br>Contanti sulla consegna<br>Braintree<br>PayPal PayFlow Pro |
| Metodi di spedizione | Sono supportati tutti i metodi di spedizione. |

Le seguenti funzioni sono: **not** supportato da AsyncOrder, ma continua a funzionare in modo sincrono:

- Metodi di pagamento non inclusi nell&#39;elenco delle funzioni supportate
- Pagamento con più indirizzi
- Creazione di ordini di amministrazione

#### Supporto API web

Quando il modulo AsyncOrder è abilitato, i seguenti endpoint REST e le mutazioni GraphQL vengono eseguiti in modo asincrono:

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL non supporta il posizionamento asincrono di ordini di preventivo negoziabili.

#### Esclusione dei metodi di pagamento

Gli sviluppatori possono escludere esplicitamente alcuni metodi di pagamento dal posizionamento di ordini asincroni aggiungendoli al `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` array. Gli ordini che utilizzano metodi di pagamento esclusi vengono elaborati in modo sincrono.

### Ordine asincrono offerta negoziabile

La _Ordine asincrono offerta negoziabile_ Il modulo B2B consente di salvare gli elementi dell&#39;ordine in modo asincrono per il `NegotiableQuote` funzionalità. È necessario che AsyncOrder e NegotiableQuote siano abilitati.

## Calcolo totale differito

La _Calcolo totale differito_ Il modulo ottimizza il processo di pagamento rinviando il calcolo totale fino a quando non viene richiesto per il carrello o durante i passaggi di pagamento finali. Se abilitata, solo il subtotale calcola come cliente aggiunge prodotti al carrello.

DeferredTotalCalculation è **disattivato** per impostazione predefinita. Utilizzare l&#39;interfaccia della riga di comando per abilitare queste funzionalità o modificare il `app/etc/env.php` file in base ai corrispondenti file README definiti nel [_Guida di riferimento del modulo_][mrg].

**Per abilitare DeferredTotalCalculation**:

È possibile abilitare DeferredTotalCalculation utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

La `set` scrive quanto segue nel `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Per disabilitare DeferredTotalCalculation**:

È possibile disabilitare DeferredTotalCalculation utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

La `set` scrive quanto segue nel `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Vedi [CalcoloTotaleDifferito] in _Guida di riferimento del modulo_.

### Imposta sul prodotto

Quando DeferredTotalCalculation è abilitato, l’imposta sul prodotto fissa (FPT) non viene inclusa nel prezzo del prodotto e nel subtotale del carrello del mini carrello dopo l’aggiunta del prodotto al carrello. Il calcolo FPT viene differito quando si aggiunge un prodotto al mini carrello. Il FPT viene visualizzato correttamente nel carrello dopo aver effettuato il pagamento finale.

## Disattiva controllo inventario

La _Abilita inventario al caricamento del carrello_ l’impostazione globale determina se eseguire un controllo di inventario durante il caricamento di un prodotto nel carrello. La disattivazione del processo di controllo dell’inventario migliora le prestazioni di tutti i passaggi del checkout, in particolare quando si tratta di prodotti di massa nel carrello.

Se questa opzione è disabilitata, il controllo dell’inventario non viene eseguito quando si aggiunge un prodotto al carrello. Se questo controllo di inventario viene ignorato, alcuni scenari esauriti potrebbero generare altri tipi di errori. Controllo dell&#39;inventario _sempre_ si verifica nella fase di posizionamento dell&#39;ordine, anche se disabilitata.

**Abilita Controllo Inventario Al Carrello** è abilitato (impostato su Sì) per impostazione predefinita. Per disattivare il controllo dell&#39;inventario durante il caricamento del carrello, imposta **[!UICONTROL Enable Inventory Check On Cart Load]** a `No` in Admin UI **Negozi** > **Configurazione** > **Catalogo** > **Inventario** > **Opzioni stock** sezione . Vedi [Configurare le opzioni globali][global] e [Inventario del catalogo][inventory] in _Guida utente_.

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://devdocs.magento.com/guides/v2.4//mrg/intro.html
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[CalcoloTotaleDifferito]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
