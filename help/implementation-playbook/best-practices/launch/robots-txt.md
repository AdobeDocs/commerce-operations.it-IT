---
title: Best practice per la configurazione dei file "robots.txt" e "sitemap.xml"
description: Scopri come trasmettere istruzioni sul tuo sito Adobe Commerce ai crawler web.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Best practice per la configurazione `robots.txt` e `sitemap.xml` file

Questo articolo fornisce best practice per l’utilizzo di `robots.txt` e `sitemap.xml` file in Adobe Commerce, incluse la configurazione e la sicurezza. Questi file spiegano ai robot web (in genere robot di motori di ricerca) come eseguire la ricerca per indicizzazione delle pagine di un sito web. La configurazione di questi file può migliorare le prestazioni del sito e l’ottimizzazione dei motori di ricerca.

>[!NOTE]
>
>Queste best practice sono valide solo per i progetti che utilizzano la vetrina nativa di Adobe Commerce. Non si applicano ai progetti Adobe Commerce che utilizzano altre soluzioni di vetrina (ad esempio, Adobe Experience Manager, headless).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Adobe Commerce sull’infrastruttura cloud

Un progetto Adobe Commerce predefinito contiene una gerarchia che include una singola vista per siti web, store e store. Per implementazioni più complesse, puoi creare siti web, store e viste store aggiuntivi per una _multisito_ vetrina.

### Vetrine di singoli siti

Segui queste best practice durante la configurazione di `robots.txt` e `sitemap.xml` file per vetrine a sito singolo:

- Assicurati che il progetto utilizzi [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versione 2002.0.12 o successiva.
- Utilizza l’applicazione amministratore per aggiungere contenuti al `robots.txt` file.

  >[!TIP]
  >
  >Visualizza il generato automaticamente `robots.txt` file per il tuo archivio in `<domain.your.project>/robots.txt`.

- Utilizza l’applicazione amministratore per generare un `sitemap.xml` file.

  >[!IMPORTANT]
  >
  >A causa del file system di sola lettura su Adobe Commerce nei progetti di infrastruttura cloud, è necessario specificare `pub/media` prima di generare il file.

- Utilizza uno snippet Fastly VCL personalizzato per reindirizzare dalla directory principale del sito al `pub/media/` percorso per entrambi i file:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Verifica il reindirizzamento visualizzando i file in un browser web. Ad esempio: `<domain.your.project>/robots.txt` e `<domain.your.project>/sitemap.xml`. Assicurati di utilizzare il percorso principale per il quale hai configurato il reindirizzamento e non un percorso diverso.

>[!INFO]
>
>Consulta [Aggiungi mappa del sito e robot per motori di ricerca](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) per istruzioni dettagliate.


### Vetrine di negozi multisito

Puoi configurare ed eseguire diversi store con una singola implementazione di Adobe Commerce sull’infrastruttura cloud. Consulta [Configurazione di più siti Web o store](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Le stesse best practice per la configurazione di `robots.txt` e `sitemap.xml` file per [vetrine di singoli siti](#single-site-storefronts) si applica alle vetrine multisito con due importanti differenze:

- Assicurati che il `robots.txt` e `sitemap.xml` i nomi dei file contengono i nomi dei siti corrispondenti. Ad esempio:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Utilizza uno snippet Fastly VCL personalizzato leggermente modificato per reindirizzare dalla directory principale dei siti a `pub/media` percorso di entrambi i file nei siti:

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

Utilizzare l&#39;applicazione Admin per configurare `robots.txt` e `sitemap.xml` file per evitare che i bot analizzino e indicizzino contenuti non necessari (consulta [Robot motore di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Per le distribuzioni locali, la posizione in cui vengono scritti i file dipende da come è stato installato Adobe Commerce. Scrivi i file in `/path/to/commerce/pub/media/` o `/path/to/commerce/media`, a seconda di quale sia la scelta giusta per l&#39;installazione.

## Sicurezza

Non esporre il percorso di amministrazione nel `robots.txt` file. L’esposizione del percorso di amministrazione comporta una vulnerabilità ad attacchi di hacker al sito e potenziale perdita di dati. Rimuovi il percorso di amministrazione da `robots.txt` file.

Per i passaggi per modificare `robots.txt` e rimuovere tutte le voci del percorso amministratore, vedi [Guida utente di Marketing > SEO e Ricerca > Robot motore di ricerca](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se hai bisogno di aiuto, [invia un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informazioni aggiuntive

- [Informazioni su siti Web, store e visualizzazioni dello store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Aggiunta di siti Web](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Utilizza Fastly per bloccare il traffico dannoso per i siti Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt restituisce un errore 404 in Adobe Commerce su infrastruttura cloud 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
