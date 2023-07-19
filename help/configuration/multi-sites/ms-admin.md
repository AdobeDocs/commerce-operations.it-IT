---
title: Configurare più siti web, store e visualizzazioni dello store in Admin
description: Configura ulteriori siti web, store e visualizzazioni dello store nell’amministratore di Commerce.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 78a7e99ecaba6a6f7982123f5bd67efc740ec2ef
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 0%

---

# Configurare più visualizzazioni in Amministrazione

Questa attività richiede di creare una categoria principale (e categorie aggiuntive, se desiderato) per ogni archivio. Le attività descritte in questo argomento consentono di impostare più archivi. Per ulteriori informazioni, consulta le seguenti risorse nella Guida utente di Commerce:

- [Categorie](https://docs.magento.com/user-guide/catalog/categories.html)
- [Aggiunta di siti Web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [URL store](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Contenuto](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Solo ad esempio, utilizziamo un sito web francese con codice del sito web `french` in questo argomento. Per esercitazioni dettagliate, consulta [Tutorial: configurare più siti web con Apache](ms-apache.md) e [Tutorial: configurare più siti web con nginx](ms-nginx.md)

## Passaggio 1: creare categorie principali

La creazione di una categoria principale è facoltativa, ma in questo tutorial viene illustrato come farlo se desideri che ogni sito web abbia una categoria principale univoca. Puoi creare altre categorie, se lo desideri.

Per creare una categoria radice:

1. Accedi all’amministratore come utente autorizzato a creare categorie.
1. Clic **Catalogo** > **Categorie**.
1. Clic **Aggiungi categoria principale**.
1. In **Nome categoria** , immettere un nome univoco per identificare questa categoria.
1. Assicurati che Abilita categoria sia impostato su **Sì**.

   Per informazioni sulle altre opzioni disponibili in questa pagina, consulta [Categorie principali](https://docs.magento.com/user-guide/catalog/category-root.html).

   Nella figura seguente viene illustrato un esempio.

   ![Creare e abilitare una categoria principale](../../assets/configuration/add-root-category.png)

1. Clic **Salva**.
1. Ripeti queste attività il numero di volte necessario per creare categorie principali per i tuoi store.

## Passaggio 2: creare siti Web

Per creare un sito Web:

1. Accedi all’amministratore come utente autorizzato a creare siti web, store e visualizzazioni dello store.
1. Clic **Negozi** > **Impostazioni** > **Tutti i Negozi**.
1. Il giorno _Negozi_ pagina, fai clic su **Crea sito Web**.

   - **Nome**- Immettere un nome per identificare il sito Web.
   - **Codice**- Immettere un codice univoco; ad esempio, se si dispone di un negozio francese, è possibile immettere `french`
   - **Ordinamento**- Consente di immettere un ordinamento numerico facoltativo.

   Nella figura seguente viene illustrato un esempio.

   ![Aggiungere un sito Web](../../assets/configuration/multi-site-website.png)

1. Clic **Salva sito Web**.
1. Ripetere queste attività il numero di volte necessario per creare i siti Web.

## Passaggio 3: creare i negozi

Per creare un archivio:

1. In _Amministratore_ , fare clic su **Negozi** > **Impostazioni** > **Tutti i Negozi**.
1. Il giorno _Negozi_ pagina, fai clic su **Crea store**.

   - **Sito Web**- Fare clic sul nome del sito Web a cui associare il negozio.
   - **Nome**- Immettere un nome per identificare l&#39;archivio.
   - **Codice**- Immettere un codice univoco per identificare l&#39;archivio.
   - **Categoria principale**- Fare clic sul nome della categoria principale per questo archivio.

   Nella figura seguente viene illustrato un esempio.

   ![Aggiungi un archivio](../../assets/configuration/multi-site-store.png)

1. Clic **Salva store**.
1. Ripeti queste attività il numero di volte necessario per creare i tuoi store.

## Passaggio 4: creare visualizzazioni dello store

Per creare una visualizzazione dello store:

1. In _Amministratore_ , fare clic su **Negozi** > **Impostazioni** > **Tutti i Negozi**.
1. Nella pagina Archivi, fai clic su **Crea visualizzazione store**.

   - **Archivia**- Fare clic sul nome dell&#39;archivio a cui associare la visualizzazione archivio.
   - **Nome**- Immettere un nome per identificare la visualizzazione del punto vendita.
   - **Codice**- Immettere un nome univoco per identificare la visualizzazione del punto vendita.
   - **Stato**- Seleziona **Abilitato**.

   Nella figura seguente viene illustrato un esempio.

   ![Aggiungi un archivio](../../assets/configuration/multi-site-storeview.png)

1. Clic **Salva visualizzazione store**.
1. Ripeti queste attività il numero di volte necessario per creare le visualizzazioni dello store.

## Passaggio 5: modificare l’URL di base del sito web

Per accedere a un sito web utilizzando un URL univoco come `http://french.magento.mg`, è necessario modificare l’URL di base di ciascun sito in Admin.

Per modificare l&#39;URL di base del sito Web:

1. In _Amministratore_ , fare clic su **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Dalla sezione **Visualizzazione store** nella parte superiore della pagina, fare clic sul nome di uno dei siti Web, come illustrato nella figura seguente.

   ![Seleziona un ambito](../../assets/configuration/multi-site-scope.png)

1. Nel riquadro di destra, espandere **URL di base**.
1. In _URL di base_ sezione, cancella **Usa valore di sistema**.
1. Inserisci il `http://french.magento.mg` URL in **URL di base** e **URL collegamento base** campi.

1. Ripeti il passaggio precedente in _URL di base (protetto)_ sezione.

   >[!INFO]
   >
   >Se imposti un URL di base per la distribuzione di Adobe Commerce sull’infrastruttura cloud, devi sostituire il primo punto con tre trattini. Ad esempio, se l’URL di base è `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, immetti `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Se stai impostando un URL di base per i test locali, utilizza un punto.

1. Clic **Salva configurazione**.

1. Ripetere queste operazioni per altri siti Web.

## Passaggio 6: aggiungi il codice dello store all’URL di base

Commerce offre la possibilità di aggiungere il codice dello store all’URL della base del sito, semplificando così il processo di configurazione di più store. Utilizzando questa opzione, non è necessario creare directory nel file system di Commerce per archiviare `index.php` e `.htaccess`.

Questo impedisce `index.php` e `.htaccess` dalla mancata sincronizzazione con il codebase Commerce negli aggiornamenti futuri.

Consulta la [Guida utente di Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

Per aggiungere il codice store all&#39;URL di base:

1. In _Amministratore_ , fare clic su **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Dalla sezione **Visualizzazione store** nella parte superiore della pagina, fai clic su **Configurazione predefinita** come illustrato nella figura seguente.

   ![Seleziona l’ambito di configurazione predefinito](../../assets/configuration/multi-site-default.png)

1. Nel riquadro di destra, espandere **Opzioni Url**.
1. Cancella **Usa valore di sistema** casella di controllo accanto a _Aggiungi codice store agli URL_.
1. Dalla sezione _Aggiungi codice store agli URL_ , fare clic su **Sì**.

   ![Aggiungi il codice dello store all&#39;URL della base dello store](../../assets/configuration/multi-site-add-store-url.png)

1. Clic **Salva configurazione**.
1. Se richiesto, svuotare la cache. (**Sistema** > **Gestione cache**).

## Passaggio 7: modificare l’URL di base predefinito per la visualizzazione archivio

È necessario eseguire questo passaggio per ultimo perché non sarà più possibile accedere all&#39;amministratore; l&#39;accesso verrà restituito dopo la configurazione degli host virtuali, come descritto negli argomenti specifici del server Web.

Per modificare l&#39;URL di base predefinito per la visualizzazione archivio:

1. In _Amministratore_ , fare clic su **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.

1. Dalla sezione _Visualizzazione store_ nella parte superiore della pagina, fai clic su **Configurazione predefinita**.

   ![Seleziona l’ambito di configurazione predefinito](../../assets/configuration/multi-site-default.png)

1. Nel riquadro di destra, espandere **URL di base**.
1. In _URL di base_ sezione, cancella **Usa valore di sistema**.
1. Inserisci il `http://magento.mg` URL in **URL di base** e **URL collegamento base** campi.

1. Ripeti il passaggio precedente in **URL di base (protetto)** sezione.

   >[!INFO]
   >
   >Se imposti un URL di base per Adobe Commerce sull’infrastruttura cloud, devi sostituire il primo punto con tre trattini. Ad esempio, se l’URL di base è `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, immetti `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Clic **Salva configurazione**.
