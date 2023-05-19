---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# Comunicazione server web sicura

In questo argomento viene illustrato un esempio di protezione della comunicazione tra il server Web e il motore di ricerca (Elasticsearch o OpenSearch) tramite una combinazione di crittografia Transport Layer Security (TLS) e [autenticazione HTTP di base](https://datatracker.ietf.org/doc/html/rfc2617). Facoltativamente puoi anche configurare altri tipi di autenticazione; forniamo i riferimenti per tali informazioni.

Un termine precedente, Secure Sockets Layer (SSL), viene spesso utilizzato in modo intercambiabile con TLS. In questo argomento, si fa riferimento a *TLS*.)

>[!WARNING]
>
>Se non diversamente specificato, tutti i comandi di questo argomento devono essere immessi come utente con `root` privilegi.

## Recommendations

Consigliamo quanto segue:

* Il server web utilizza TLS.

   TLS esula dall’ambito di questo argomento. Tuttavia, ti consigliamo vivamente di utilizzare un certificato reale in produzione e non un certificato autofirmato.

* Il motore di ricerca viene eseguito sullo stesso host di un server Web. L’esecuzione del motore di ricerca e del server web su host diversi esula dall’ambito di questo argomento.

   Il vantaggio di mettere il motore di ricerca e il server web sullo stesso host è che rende impossibile intercettare le comunicazioni crittografate. Il server web del motore di ricerca non deve essere necessariamente lo stesso di Adobe Commerce o del server web di Magento Open Source; ad esempio, Adobe Commerce può eseguire Apache e Elasticsearch/OpenSearch può eseguire nginx.

   Se il motore di ricerca è esposto al web pubblico, devi configurare l’autenticazione. Se l’istanza del motore di ricerca è protetta all’interno della rete, ciò potrebbe non essere necessario. Rivolgiti al provider di hosting per determinare le misure di sicurezza da implementare per proteggere l’istanza.

## Ulteriori informazioni su TLS

Consulta una delle risorse seguenti:

* Apache

   * [Procedure per la crittografia avanzata di Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Come creare un certificato SSL su Apache per Ubuntu 14.04 (tutorial Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configurazione di un server web protetto SSL con CentOS (wiki CentOS)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Terminazione SSL Nginx](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Come creare un certificato SSL su Nginx per Ubuntu 14.04 (tutorial Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Installazione certificato SSL Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
