---
title: Configurare più siti web, store e visualizzazioni dello store in Admin
description: Configura altri siti web, store e visualizzazioni dello store in Commerce Admin.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# Configurare più visualizzazioni in Amministrazione

Questa attività richiede di creare una categoria principale (e categorie aggiuntive, se desiderato) per ogni archivio. Le attività descritte in questo argomento consentono di impostare più archivi. Per ulteriori informazioni, vedere le risorse seguenti nella Guida utente di Commerce:

- [Categorie](https://experienceleague.adobe.com/it/docs/commerce-admin/catalog/categories/categories)
- [Aggiunta di siti Web](https://experienceleague.adobe.com/it/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Archivia URL](https://experienceleague.adobe.com/it/docs/commerce-admin/stores-sales/site-store/store-urls)
- [Contenuto](https://experienceleague.adobe.com/it/docs/commerce-admin/content-design/content-menu)

>[!INFO]
>
>Solo ad esempio, in questo argomento viene utilizzato un sito Web francese con codice `french`. Per esercitazioni dettagliate, consulta [Esercitazione: configurare più siti Web con Apache](ms-apache.md) e [Esercitazione: configurare più siti Web con nginx](ms-nginx.md)

## Passaggio 1: creare categorie principali

La creazione di una categoria principale è facoltativa, ma in questo tutorial viene illustrato come farlo se desideri che ogni sito web abbia una categoria principale univoca. Puoi creare altre categorie, se lo desideri.

Per creare una categoria radice:

1. Accedi all’amministratore come utente autorizzato a creare categorie.
1. Fai clic su **Catalogo** > **Categorie**.
1. Fare clic su **Aggiungi categoria principale**.
1. Nel campo **Nome categoria** immettere un nome univoco per identificare la categoria.
1. Assicurarsi che Abilita categoria sia impostato su **Sì**.

   Per informazioni sulle altre opzioni disponibili in questa pagina, vedere [Categorie principali](https://experienceleague.adobe.com/it/docs/commerce-admin/catalog/categories/category-root).

   Nella figura seguente viene illustrato un esempio.

   ![Creare e abilitare una categoria radice](../../assets/configuration/add-root-category.png)

1. Fai clic su **Salva**.
1. Ripeti queste attività il numero di volte necessario per creare categorie principali per i tuoi store.

## Passaggio 2: creare siti Web

Per creare un sito Web:

1. Accedi all’amministratore come utente autorizzato a creare siti web, store e visualizzazioni dello store.
1. Fai clic su **Archivi** > **Impostazioni** > **Tutti gli archivi**.
1. Nella pagina _Archivi_ fare clic su **Crea sito Web**.

   - **Nome** - Immettere un nome per identificare il sito Web.
   - **Codice**—Immettere un codice univoco; ad esempio, se si dispone di un negozio francese, è possibile immettere `french`
   - **Ordinamento** - Immettere un ordinamento numerico facoltativo.

   Nella figura seguente viene illustrato un esempio.

   ![Aggiungi sito Web](../../assets/configuration/multi-site-website.png)

1. Fare clic su **Salva sito Web**.
1. Ripetere queste attività il numero di volte necessario per creare i siti Web.

## Passaggio 3: creare i negozi

Per creare un archivio:

1. Nel pannello _Amministratore_, fai clic su **Archivi** > **Impostazioni** > **Tutti gli archivi**.
1. Nella pagina _Archivi_, fai clic su **Crea archivio**.

   - **Sito Web** - Fare clic sul nome del sito Web a cui associare l&#39;archivio.
   - **Nome** - Immettere un nome per identificare l&#39;archivio.
   - **Codice** - Immettere un codice univoco per identificare l&#39;archivio.
   - **Categoria principale** - Fare clic sul nome della categoria principale per questo archivio.

   Nella figura seguente viene illustrato un esempio.

   ![Aggiungi un archivio](../../assets/configuration/multi-site-store.png)

1. Fai clic su **Salva archivio**.
1. Ripeti queste attività il numero di volte necessario per creare i tuoi store.

## Passaggio 4: creare visualizzazioni dello store

Per creare una visualizzazione dello store:

1. Nel pannello _Amministratore_, fai clic su **Archivi** > **Impostazioni** > **Tutti gli archivi**.
1. Nella pagina Negozi, fare clic su **Crea visualizzazione archivio**.

   - **Archivio**: fare clic sul nome dell&#39;archivio a cui associare la visualizzazione dell&#39;archivio.
   - **Nome** - Immettere un nome per identificare la visualizzazione dell&#39;archivio.
   - **Codice** - Immettere un nome univoco per identificare la visualizzazione dell&#39;archivio.
   - **Stato**—Selezionare **Abilitato**.

   Nella figura seguente viene illustrato un esempio.

   ![Aggiungi un archivio](../../assets/configuration/multi-site-storeview.png)

1. Fai clic su **Salva visualizzazione archivio**.
1. Ripeti queste attività il numero di volte necessario per creare le visualizzazioni dello store.

## Passaggio 5: modificare l’URL di base del sito web

Per accedere a un sito Web utilizzando un URL univoco come `http://french.magento.mg`, è necessario modificare l&#39;URL di base di ciascun sito nell&#39;amministratore.

Per modificare l&#39;URL di base del sito Web:

1. Nel pannello _Amministratore_, fai clic su **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Nell&#39;elenco **Visualizzazione store** nella parte superiore della pagina, fare clic sul nome di uno dei siti Web, come illustrato nella figura seguente.

   ![Selezionare un ambito](../../assets/configuration/multi-site-scope.png)

1. Nel riquadro di destra espandere **URL di base**.
1. Nella sezione _URL di base_, cancella **Usa valore di sistema**.
1. Immettere l&#39;URL `http://french.magento.mg` nei campi **URL base** e **URL collegamento base**.

1. Ripeti il passaggio precedente nella sezione _URL di base (protetti)_.

   >[!INFO]
   >
   >Se imposti un URL di base per la distribuzione di Adobe Commerce sull’infrastruttura cloud, devi sostituire il primo punto con tre trattini. Ad esempio, se l&#39;URL di base è `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, immettere `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Se stai impostando un URL di base per i test locali, utilizza un punto.

1. Fai clic su **Salva configurazione**.

1. Ripetere queste operazioni per altri siti Web.

## Passaggio 6: aggiungi il codice dello store all’URL di base

Commerce consente di aggiungere il codice del punto vendita all&#39;URL della base del sito, semplificando così la configurazione di più punti vendita. Utilizzando questa opzione, non è necessario creare directory nel file system di Commerce per archiviare `index.php` e `.htaccess`.

Ciò impedisce a `index.php` e `.htaccess` di uscire dalla sincronizzazione con il codebase di Commerce negli aggiornamenti futuri.

Consulta la [Guida utente di Commerce](https://experienceleague.adobe.com/it/docs/commerce-admin/stores-sales/site-store/store-urls).

Per aggiungere il codice store all&#39;URL di base:

1. Nel pannello _Amministratore_, fai clic su **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Dall&#39;elenco **Visualizzazione archivio** nella parte superiore della pagina, fare clic su **Configurazione predefinita** come illustrato nella figura seguente.

   ![Selezionare l&#39;ambito di configurazione predefinito](../../assets/configuration/multi-site-default.png)

1. Nel riquadro di destra espandere **Opzioni URL**.
1. Deselezionare la casella di controllo **Usa valore di sistema** accanto a _Aggiungi codice archivio agli URL_.
1. Nell&#39;elenco _Aggiungi codice archivio agli URL_ fare clic su **Sì**.

   ![Aggiungere il codice dello store all&#39;URL di base dello store](../../assets/configuration/multi-site-add-store-url.png)

1. Fai clic su **Salva configurazione**.
1. Se richiesto, svuotare la cache. (**Sistema** > **Gestione cache**).

## Passaggio 7: modificare l’URL di base predefinito per la visualizzazione archivio

È necessario eseguire questo passaggio per ultimo perché non sarà più possibile accedere all&#39;amministratore; l&#39;accesso verrà restituito dopo la configurazione degli host virtuali, come descritto negli argomenti specifici del server Web.

Per modificare l&#39;URL di base predefinito per la visualizzazione archivio:

1. Nel pannello _Amministratore_, fai clic su **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.

1. Dall&#39;elenco _Visualizzazione archivio_ nella parte superiore della pagina, fare clic su **Configurazione predefinita**.

   ![Selezionare l&#39;ambito di configurazione predefinito](../../assets/configuration/multi-site-default.png)

1. Nel riquadro di destra espandere **URL di base**.
1. Nella sezione _URL di base_, cancella **Usa valore di sistema**.
1. Immettere l&#39;URL `http://magento.mg` nei campi **URL base** e **URL collegamento base**.

1. Ripeti il passaggio precedente nella sezione **URL di base (protetti)**.

   >[!INFO]
   >
   >Se imposti un URL di base per Adobe Commerce sull’infrastruttura cloud, devi sostituire il primo punto con tre trattini. Ad esempio, se l&#39;URL di base è `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, immettere `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Fai clic su **Salva configurazione**.

>[!INFO]
>
>Il codice di visualizzazione del sito Web, dello store e dello store può includere solo lettere (a-z o A-Z), numeri (0-9) e caratteri di sottolineatura (_). Inoltre, il primo carattere deve essere una lettera. Se si utilizzano maiuscole o minuscole, internamente la corrispondenza non distingue tra maiuscole e minuscole per consentire l’override delle impostazioni di configurazione tramite le variabili di ambiente. Vedere [Utilizzare le variabili di ambiente per sostituire le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables).