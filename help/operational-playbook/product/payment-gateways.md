---
title: Gateway di pagamento
description: Scegli un provider di gateway di pagamento per il progetto di e-commerce in base alle esigenze della tua azienda.
exl-id: eab50191-0744-41da-99ba-2e06ea61da27
feature: Best Practices, Payments
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Gateway di pagamento

C&#39;è stato un tempo in cui il contante era la principale fonte di transazioni, ma il mondo online ha preso il sopravvento e i metodi di pagamento online stanno sostituendo i vecchi metodi di pagamento. Tutto è ora online, il che rende le cose più facili e accessibili, comprese le carte di credito, gli e-wallet e i bonifici bancari.

![Loghi dei provider di gateway di pagamento](../../assets/playbooks/payment-gateways.png)

Un gateway di pagamento è un fornitore di servizi che collega ed elabora i pagamenti per i siti Web di e-commerce. Svolgono un ruolo fondamentale nell&#39;esperienza di acquisto del cliente e nei tassi di conversione. I sistemi di pagamento complicati tendono a far abbandonare ai clienti i loro carrelli. È importante fornire ai clienti un sistema di pagamento facile e utente in cui lineare se un metodo di pagamento fallisce hanno un metodo alternativo per motivarli a completare l&#39;acquisto.

## Rivedere i requisiti

I rivenditori devono selezionare il miglior gateway di pagamento che soddisfi le loro esigenze. Ci sono molti gateway di pagamento in mercato, like Braintree e Stripe, ma prima di decidere su un gateway di pagamento, poniti le seguenti domande:

- Qual è il mio requisito aziendale?
- Rientra nel mio budget?
- Quanto è forte la sicurezza sul gateway di pagamento?
- Ci sarà un impatto sulla mia interfaccia utente/interfaccia utente di storefront?
- Quali sono le prestazioni del gateway di pagamento?
- Com&#39;è il servizio di supporto del gateway di pagamento dopo l&#39;acquisto?
- Quale fornitore di gateway di pagamento mi si addice meglio?
- Il gateway di pagamento offre altre funzioni, come il calcolo delle imposte, l&#39;utilizzo di geolocalizzazioni e il calcolo delle commissioni di servizio?

Esistono alcune limitazioni dei gateway di pagamento di cui è necessario essere a conoscenza, tra cui:

- Non tutti i tipi di carte sono accettati dai gateway di pagamento.
- Alcune opzioni di pagamento potrebbero non essere disponibili per gli acquirenti internazionali.
- Scappatoie di sicurezza nel gateway di pagamento. I clienti tendono a esitare a effettuare ordini online per motivi di sicurezza.

Quando un’azienda decide di integrare un gateway di pagamento con la propria piattaforma, è sempre meglio vedere come appare sul punto vendita, che tipo di esperienza offre ai clienti e se è di facile utilizzo. Inoltre, assicurati che la sicurezza del pagamento non possa essere compromessa. Un buon gateway di pagamento funzionante e sicuro offre una migliore esperienza del cliente.

## Considerazioni B2B e B2C

Le aziende B2B e B2C hanno sistemi di pagamento simili, ma le aziende B2B hanno più regole, normative e processi. B2B aziende tendono a trattare volumi maggiori rispetto alle aziende B2C.

B2C clienti acquistano prodotti o servizi per uso individuale. I clienti di solito pagano lo stesso prezzo degli altri clienti e non vi è alcuna contrattazione. B2B clienti includono vari
parti interessate, il che rende l&#39;approvazione più complessa e costosa.

B2B clienti hanno ordini e requisiti diversi, che devono essere elaborati e approvati dal rappresentante di vendita o un rappresentante di vendita deve essere coinvolto quando un cliente acquista online utilizzando un richiesta per la proposta (RFP) o un ordine di acquisto (PO).

B2C pagamenti possono essere una tantum e di valore inferiore. I clienti aggiungono prodotti al carrello e effettuano il checkout utilizzando un pagamento sicuro utilizzando un scheda di credito o un portafoglio elettronico.

A causa dell&#39;elevato valore di acquisto delle transazioni B2B, le aziende B2B offrono più opzioni di pagamento oltre alle opzioni standard, tra cui assegni, bonifici bancari e ordini di acquisto.

L&#39;implementazione delle opzioni di pagamento più adatte dipende dal tipo di requisiti aziendali e aziendali.
