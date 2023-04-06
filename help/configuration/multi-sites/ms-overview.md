---
title: Più siti web o negozi
description: Scopri come avviare più siti web o implementare le viste store con diverse opzioni, domini e contenuti.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---


# Più siti web o negozi

Una singola istanza del software Adobe Commerce consente di avviare più siti web o di memorizzare viste che utilizzano attributi e contenuti diversi, ad esempio:

- Lingue predefinite
- Nomi di dominio
- Categorie
- Prodotti
- Valute

Questa soluzione flessibile consente a una base di codice Commerce e all’amministratore di amministrare e visualizzare diversi store. Puoi configurare i siti web, gli archivi e le viste Store nell’amministratore. Utilizza alcune variabili negli host virtuali per avviare l’applicazione Commerce utilizzando questi siti web o le viste Store.

Un utilizzo tipico consiste nell&#39;impostare archivi con opzioni diverse nei diversi domini. Ad esempio, puoi avere un set di categorie e prodotti su un dominio e un altro set di categorie e prodotti su un dominio separato in una lingua diversa.

Puoi configurare i siti web, gli archivi e le viste Store nell’amministratore Commerce. Utilizza la `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` variabili negli host virtuali per avviare l’applicazione Commerce utilizzando questi siti web o le viste Store.

Considera i seguenti termini:

- **Sito Web**- è il contenitore principale per siti, metodi di consegna, metodi di pagamento e altro ancora. Per creare siti completamente separati che non condividono carrello, metodi di consegna o altri, è necessario creare siti web separati.

   Gli account cliente del sito web possono essere condivisi tra più siti web all’interno di una singola istanza Commerce. Un sito web contiene almeno un negozio. I prezzi del catalogo devono essere gestiti a livello di sito web.

- **Store**—è contenuto in un sito web. A sua volta, un negozio contiene almeno un *vista store*.

   Più negozi possono condividere carrello, sessioni utente, gateway di pagamento e altro, ma hanno strutture di catalogo separate e prezzo del catalogo.

   Impossibile gestire la quantità del catalogo (inventario) a livello di archivio. L’inventario è gestito solo a livello di sito web o globale.

   Le viste Store modificano il modo in cui le pagine vengono presentate e vengono in genere utilizzate per visualizzare un negozio con layout o lingue diverse. È possibile gestire valute diverse per visualizzazione store.

   Ogni sito web e ogni visualizzazione store devono avere un identificatore univoco. Questo identificatore è necessario per utilizzare il `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` variabili come segue:

- `MAGE_RUN_TYPE` può essere `store` o `website`

   - Utilizzo `website` per caricare un sito web nella vetrina.
   - Utilizzo `store` per caricare qualsiasi vista store nella vetrina.

- `MAGE_RUN_CODE` è il codice univoco della visualizzazione del sito web o del negozio che corrisponde a `MAGE_RUN_TYPE`

Di seguito è riportato un riepilogo delle attività da eseguire:

1. [Configura i siti web, gli archivi e le visualizzazioni store nell’Admin.](ms-admin.md)
1. Crea un host virtuale per caricare molti siti web o un host virtuale per sito Web Commerce o per visualizzazione store per consentire direttive specifiche per ogni negozio.
1. Passa i valori di `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` al server web.
