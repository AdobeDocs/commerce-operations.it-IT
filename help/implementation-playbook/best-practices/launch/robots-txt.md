---
title: Procedure consigliate per la configurazione dei crawler Web
description: Scopri come trasmettere istruzioni sul tuo sito Adobe Systems Commerce ai web crawler utilizzando i file 'robots.txt' e 'mappa del sito.xml'.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Best practice per la configurazione dei crawler web

Questo articolo fornisce le best practice per l&#39;utilizzo di `robots.txt` e `sitemap.xml` file in Adobe Commerce, incluse la configurazione e la sicurezza. Questi file forniscono istruzioni ai crawler (in genere robot di motori di ricerca) su come eseguire la ricerca per indicizzazione delle pagine di un sito Web. La configurazione di questi file può migliorare le prestazioni del sito e l’ottimizzazione dei motori di ricerca.

>[!NOTE]
>
>Queste best practice sono valide solo per i progetti che utilizzano la vetrina nativa di Adobe Commerce. Non si applicano ai progetti Adobe Systems Commerce che utilizzano altre soluzioni di vetrina (ad esempio, Adobe Experience Manager, headless).

## Prodotti e versioni interessati

[Tutte le versioni](../../../release/versions.md) supportate di:

- Adobe Systems Commerce su infrastruttura cloud
- Adobe Systems Commerce locale

## Adobe Systems Commerce su infrastruttura cloud

Un progetto Adobe Systems Commerce predefinito contiene una gerarchia che include un singolo sito Web, una singola visualizzazione store e store. Per implementazioni più complesse, è possibile creare siti Web, archivi e visualizzazioni store aggiuntive per una _vetrina multisito_ .

### Vetrine di singoli siti

Seguire le procedure consigliate riportate di seguito durante la configurazione dei file `robots.txt` e `sitemap.xml` per gli storefront a sito singolo:

- Verificare che il progetto utilizzi [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) versione 2002.0.12 o successiva.
- Utilizzare l&#39;applicazione Admin per aggiungere contenuto al file `robots.txt`.

  >[!TIP]
  >
  >Visualizza il file generato `robots.txt` automaticamente per il store in .`<domain.your.project>/robots.txt`

- Utilizza l&#39;applicazione amministrazione per generare un `sitemap.xml` file.

  >[!IMPORTANT]
  >
  >A causa del file system di sola lettura in Adobe Systems Commerce nei progetti infrastruttura cloud, è necessario specificare il `pub/media` percorso prima di generare il file.

- Utilizza uno snippet Fastly VCL personalizzato per reindirizzare dalla radice del tuo sito alla posizione di entrambi i `pub/media/` file:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Verificare il reindirizzare visualizzando i file in un browser Web. Ad esempio, `<domain.your.project>/robots.txt` e `<domain.your.project>/sitemap.xml`. Assicurati di utilizzare il percorso radice per il quale hai configurato il reindirizzare e non un percorso diverso.

>[!INFO]
>
>Per istruzioni dettagliate, vedere [Aggiungere la mappa del](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) sito e ricerca robot motore.


### Vetrine di negozi multisito

Puoi configurare ed eseguire diversi store con una singola implementazione di Adobe Commerce sull’infrastruttura cloud. Vedere [Configurare più siti Web o store](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

Le stesse procedure consigliate per la configurazione dei file `robots.txt` e `sitemap.xml` per [storefront a sito singolo](#single-site-storefronts) si applicano a storefront multisito con due importanti differenze:

- Assicurarsi che i `robots.txt` nomi dei file e `sitemap.xml` contengano i nomi dei siti corrispondenti. Ad esempio:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilizza uno snippet Fastly VCL personalizzato leggermente modificato per reindirizzare dalla radice dei tuoi siti alla `pub/media` posizione di entrambi i file nei tuoi siti:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Systems Commerce locale

Utilizza l&#39;applicazione Admin per configurare i file AND `sitemap.xml` in modo da impedire ai bot di eseguire la scansione e l&#39;indicizzazione `robots.txt` di contenuto non necessari (consulta [Search Engine Robots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Per le distribuzioni locali, la posizione in cui si scrivono i file dipende da come è stato installato Adobe Systems Commerce. Scrivere i file in `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, a seconda di quale sia giusto per l&#39;installazione.

## Sicurezza

Non esporre il percorso amministratore nel file `robots.txt`. L’esposizione del percorso di amministrazione comporta una vulnerabilità ad attacchi di hacker al sito e potenziale perdita di dati. Rimuovere il percorso di amministrazione dal file `robots.txt`.

Per i passaggi per modificare il file `robots.txt` e rimuovere tutte le voci del percorso amministratore, vedere [Guida utente marketing > SEO e Ricerca > Robot motore di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se hai bisogno di assistenza, [invia un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informazioni aggiuntive

- [Informazioni su siti Web, archivi e visualizzazioni dello store](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Aggiunta di siti Web](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Utilizza Fastly per bloccare il traffico dannoso per i tuoi siti Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt restituisce un errore 404 in Adobe Commerce sull&#39;infrastruttura cloud 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
