---
title: Best practice per la configurazione dei crawler web
description: Scopri come trasmettere istruzioni sul tuo sito Adobe Commerce ai crawler web utilizzando i file "robots.txt" e "sitemap.xml".
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Best practice per la configurazione dei crawler web

Questo articolo fornisce le best practice per l&#39;utilizzo di `robots.txt` e `sitemap.xml` file in Adobe Commerce, incluse la configurazione e la sicurezza. Questi file forniscono istruzioni ai crawler (in genere robot di motori di ricerca) su come eseguire la ricerca per indicizzazione delle pagine di un sito Web. La configurazione di questi file può migliorare le prestazioni del sito e l’ottimizzazione dei motori di ricerca.

>[!NOTE]
>
>Queste best practice sono valide solo per i progetti che utilizzano la vetrina nativa di Adobe Commerce. Non si applicano ai progetti Adobe Commerce che utilizzano altre soluzioni di vetrina (ad esempio, Adobe Experience Manager, headless).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Adobe Commerce sull’infrastruttura cloud

Un progetto Adobe Commerce predefinito contiene una gerarchia che include una singola vista per siti web, store e store. Per implementazioni più complesse, puoi creare siti web, store e viste store aggiuntivi per una vetrina _multisito_.

### Vetrine di singoli siti

Seguire le procedure consigliate riportate di seguito durante la configurazione dei file `robots.txt` e `sitemap.xml` per gli storefront a sito singolo:

- Verificare che il progetto utilizzi [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versione 2002.0.12 o successiva.
- Utilizzare l&#39;applicazione Admin per aggiungere contenuto al file `robots.txt`.

  >[!TIP]
  >
  >Visualizza il file `robots.txt` generato automaticamente per il tuo archivio in `<domain.your.project>/robots.txt`.

- Utilizzare l&#39;applicazione Admin per generare un file `sitemap.xml`.

  >[!IMPORTANT]
  >
  >A causa del file system di sola lettura su Adobe Commerce nei progetti di infrastruttura cloud, è necessario specificare il percorso `pub/media` prima di generare il file.

- Utilizzare uno snippet Fastly VCL personalizzato per reindirizzare dalla directory principale del sito alla posizione `pub/media/` per entrambi i file:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Verifica il reindirizzamento visualizzando i file in un browser web. Ad esempio, `<domain.your.project>/robots.txt` e `<domain.your.project>/sitemap.xml`. Assicurati di utilizzare il percorso principale per il quale hai configurato il reindirizzamento e non un percorso diverso.

>[!INFO]
>
>Per istruzioni dettagliate, vedere [Aggiungere una mappa del sito e i robot dei motori di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html).


### Vetrine di negozi multisito

Puoi configurare ed eseguire diversi store con una singola implementazione di Adobe Commerce sull’infrastruttura cloud. Vedere [Configurare più siti Web o store](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Le stesse procedure consigliate per la configurazione dei file `robots.txt` e `sitemap.xml` per [storefront a sito singolo](#single-site-storefronts) si applicano a storefront multisito con due importanti differenze:

- Verificare che i nomi dei file `robots.txt` e `sitemap.xml` contengano i nomi dei siti corrispondenti. Ad esempio:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilizza uno snippet Fastly VCL personalizzato leggermente modificato per reindirizzare dalla directory principale dei siti alla posizione `pub/media` per entrambi i file nei siti:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce on-premise

Utilizzare l&#39;applicazione Admin per configurare i file `robots.txt` e `sitemap.xml` per impedire ai bot di eseguire la scansione e l&#39;indicizzazione di contenuto non necessario (vedere [Robot motore di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Per le distribuzioni locali, la posizione in cui vengono scritti i file dipende da come è stato installato Adobe Commerce. Scrivere i file in `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, a seconda di quale sia la scelta corretta per l&#39;installazione.

## Sicurezza

Non esporre il percorso amministratore nel file `robots.txt`. L’esposizione del percorso di amministrazione comporta una vulnerabilità ad attacchi di hacker al sito e potenziale perdita di dati. Rimuovere il percorso di amministrazione dal file `robots.txt`.

Per i passaggi per modificare il file `robots.txt` e rimuovere tutte le voci del percorso amministratore, vedere [Guida utente marketing > SEO e Ricerca > Robot motore di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se hai bisogno di assistenza, [invia un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informazioni aggiuntive

- [Informazioni su siti Web, archivi e visualizzazioni dello store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Aggiunta di siti Web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Utilizza Fastly per bloccare il traffico dannoso per i tuoi siti Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt restituisce un errore 404 in Adobe Commerce sull&#39;infrastruttura cloud 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
