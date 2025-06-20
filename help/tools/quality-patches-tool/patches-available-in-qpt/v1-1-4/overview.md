---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.4'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.4.
feature: Tools and External Services
role: Admin
exl-id: 67e87ea1-196a-4bc1-ae9d-f3f1184b4986
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Panoramica di [!DNL Quality Patches Tool] (QPT) v1.1.4

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.4.

QPT v1.1.4 include le seguenti patch:

1. **MC-42528**: è stato corretto il problema per cui la query GraphQL `categoryList` restituisce sia le categorie assegnate che quelle non assegnate.
1. **MDVA-25631**: migliora le prestazioni per la modifica e il salvataggio di segmenti di clienti che contengono un numero elevato di clienti.
1. **MDVA-26005**: è stato risolto il problema che impediva la selezione di una categoria in una struttura di categorie per le condizioni della regola Prezzo carrello.
1. **MDVA-29400**: è stato risolto il problema relativo agli ordini duplicati inseriti con [!DNL PayPal Express Checkout].
1. **MDVA-37725**: è stato risolto il problema che determinava l&#39;inserimento di URL del logo nel sito Web predefinito nelle e-mail di ordine asincrono inviate da siti Web non predefiniti.
1. **MDVA-39482**: risolve il problema relativo all&#39;esaurimento delle scorte per un prodotto importato con quantità pari a &quot;0&quot; quando gli ordini inevasi sono abilitati.
1. **MDVA-40101**: è stato risolto il problema che impediva la rimozione degli elementi dal mini-carrello dopo il corretto inserimento dell&#39;ordine mediante l&#39;estrazione di [!DNL PayPal Express].
1. **MDVA-40399**: è stato risolto il problema che impediva la creazione simultanea di fatture parziali per lo stesso ordine tramite API REST.
1. **MDVA-40401**: è stato risolto il problema che causava la modifica del valore di utilizzo del coupon anche in caso di esito negativo dell&#39;ordine.
1. **MDVA-40435**: corregge il problema con uno sconto non corretto sui prodotti bundle con prezzi dinamici quando applicati tramite GraphQL.
1. **MDVA-40537**: è stato risolto il problema che causava un errore durante la creazione di una visualizzazione archivio se erano presenti più pagine CMS con la stessa chiave URL.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
