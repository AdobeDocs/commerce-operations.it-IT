---
title: Best practice per la configurazione di file `robots.txt` e `sitemap.xml`
description: Scopri come trasmettere istruzioni sul sito Adobe Commerce ai Web crawler.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la configurazione `robots.txt` e `sitemap.xml` file

Questo articolo fornisce le best practice per l’utilizzo di `robots.txt` e `sitemap.xml` file in Adobe Commerce, inclusi configurazione e sicurezza. Questi file istruiscono i robot web (in genere i robot dei motori di ricerca) come eseguire ricerche per indicizzazione di pagine su un sito web. La configurazione di questi file può migliorare le prestazioni del sito e l’ottimizzazione del motore di ricerca.

>[!NOTE]
>
>Queste best practice si applicano solo ai progetti che utilizzano la vetrina nativa di Adobe Commerce. Non si applicano ai progetti Adobe Commerce che utilizzano altre soluzioni storefront (ad esempio, Adobe Experience Manager, headless).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Adobe Commerce su infrastruttura cloud

Un progetto Adobe Commerce predefinito contiene una gerarchia che include una singola visualizzazione sito web, store e store. Per implementazioni più complesse, puoi creare altri siti web, negozi e archiviare visualizzazioni per un _multisito_ vetrina.

### vetrine a sito singolo

Segui queste best practice per configurare il `robots.txt` e `sitemap.xml` file per vetrine a sito singolo:

- Assicurati che il progetto utilizzi [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versione 2002.0.12 o successiva.
- Utilizza l’applicazione Admin per aggiungere contenuti al `robots.txt` file.

   >[!TIP]
   >
   >Visualizza il generato automaticamente `robots.txt` file per il tuo negozio all&#39;indirizzo `<domain.your.project>/robots.txt`.

- Utilizza l’applicazione Admin per generare un `sitemap.xml` file.

   >[!IMPORTANT]
   >
   >A causa del file system di sola lettura su Adobe Commerce su progetti di infrastruttura cloud, è necessario specificare il `pub/media` prima di generare il file.

- Utilizza un frammento VCL personalizzato per reindirizzare dalla radice del sito al `pub/media/` posizione per entrambi i file:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- Testa il reindirizzamento visualizzando i file in un browser web. Ad esempio: `<domain.your.project>/robots.txt` e `<domain.your.project>/sitemap.xml`. Assicurati di utilizzare il percorso principale per il quale hai configurato il reindirizzamento e non un percorso diverso.

>[!INFO]
>
>Vedi [Aggiungi la mappa del sito e i robot dei motori di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) per istruzioni dettagliate.


### vetrine multisito

Puoi configurare ed eseguire diversi store con un’unica implementazione di Adobe Commerce sull’infrastruttura cloud. Vedi [Configurazione di più siti web o negozi](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Le stesse best practice per la configurazione di `robots.txt` e `sitemap.xml` file per [vetrine a sito singolo](#single-site-storefronts) si applica a vetrine multisito con due importanti differenze:

- Assicurati che il `robots.txt` e `sitemap.xml` i nomi dei file contengono i nomi dei siti corrispondenti. Ad esempio:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilizza un frammento VCL personalizzato leggermente modificato per reindirizzare dalla radice dei siti a `pub/media` posizione di entrambi i file nei siti:

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

Utilizza l’applicazione Admin per configurare l’ `robots.txt` e `sitemap.xml` file per impedire ai bot di eseguire la scansione e l&#39;indicizzazione di contenuti non necessari (vedi [Robot per motori di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Per le distribuzioni locali, la scrittura dei file dipende dalla modalità di installazione di Adobe Commerce. Scrivere i file in `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, a seconda di quale sia il diritto per l’installazione.

## Sicurezza

Non esporre il percorso amministratore nel `robots.txt` file. La visualizzazione del percorso amministratore è una vulnerabilità per l’hacking del sito e la potenziale perdita di dati. Rimuovi il percorso amministratore dal `robots.txt` file.

Per i passaggi da eseguire per modificare le `robots.txt` e rimuovi tutte le voci del percorso amministratore, vedi [Guida utente di marketing > SEO and Search > Search Engine Robots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se hai bisogno di aiuto, [inviare un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.md#submit-ticket).

## Informazioni aggiuntive

- [Informazioni su siti web, store e viste store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Aggiunta di siti web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Usa Flast per bloccare il traffico dannoso per i siti Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt fornisce un errore 404 in Adobe Commerce su infrastruttura cloud 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.md)
