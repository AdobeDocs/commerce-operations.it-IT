---
title: Più siti Web o store
description: Scopri come avviare più siti web o implementare visualizzazioni store con opzioni, domini e contenuti diversi.
exl-id: 724d75d9-13fc-40f9-951a-69aa407adb6f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Più siti Web o store

Una singola istanza del software Adobe Commerce consente di avviare più siti web o visualizzazioni di store che utilizzano attributi e contenuti diversi, ad esempio:

- Lingue predefinite
- Nomi di dominio
- Categorie
- Prodotti
- Valute

Questa soluzione flessibile consente a un unico codebase Commerce e all&#39;amministratore di amministrare e visualizzare diversi store. Puoi configurare i siti web, gli store e le visualizzazioni dello store nell’Amministratore. Utilizza determinate variabili negli host virtuali per avviare l’applicazione Commerce utilizzando questi siti web o le visualizzazioni dello store.

Un uso tipico consiste nel configurare archivi con opzioni diverse in domini diversi. Ad esempio, puoi avere un set di categorie e prodotti su un dominio e un altro set di categorie e prodotti su un dominio separato in una lingua diversa.

Puoi configurare i siti web, gli store e le visualizzazioni dello store in Commerce Admin. Utilizzare le variabili `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` negli host virtuali per avviare l&#39;applicazione Commerce utilizzando questi siti Web o le visualizzazioni dello store.

Considera i seguenti termini:

- **Sito Web**: è il contenitore principale per siti, metodi di consegna, metodi di pagamento e altro ancora. Per creare siti completamente separati che non condividono il carrello, i metodi di consegna o altri, è necessario creare siti web separati.

  Gli account cliente del sito web possono essere condivisi tra più siti web all’interno di una singola istanza di Commerce. Un sito web contiene almeno un negozio. I prezzi del catalogo devono essere gestiti a livello di sito web.

- **Store**—è contenuto in un sito Web. A sua volta, un archivio contiene almeno una *visualizzazione archivio*.

  Più negozi possono condividere carrello, sessioni utente, gateway di pagamento e altro ancora, ma hanno strutture di catalogo e prezzo di catalogo separati.

  Impossibile gestire la quantità di catalogo (inventario) a livello di archivio. L&#39;inventario viene gestito solo a livello di sito Web o globale.

  Le visualizzazioni del Negozio modificano il modo in cui vengono presentate le pagine e in genere vengono utilizzate per visualizzare un Negozio con layout o lingue diversi. Puoi gestire valute diverse per ogni visualizzazione del Negozio.

  Ogni sito web e ogni visualizzazione store deve avere un identificatore univoco. Questo identificatore è necessario per utilizzare le variabili `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` come segue:

- `MAGE_RUN_TYPE` può essere `store` o `website`

   - Utilizza `website` per caricare un sito Web nella vetrina.
   - Utilizza `store` per caricare qualsiasi visualizzazione dello store nella tua vetrina.

- `MAGE_RUN_CODE` è il codice univoco di visualizzazione del sito Web o dello store che corrisponde a `MAGE_RUN_TYPE`

Di seguito è riportato un riepilogo delle attività da eseguire:

1. [Configura siti web, store e visualizzazioni dello store in Admin.](ms-admin.md)
1. Crea un host virtuale per caricare molti siti Web o un host virtuale per sito Web Commerce o vista store per consentire direttive specifiche per ogni store.
1. Trasmettere i valori di `MAGE_RUN_TYPE` e `MAGE_RUN_CODE` al server Web.
