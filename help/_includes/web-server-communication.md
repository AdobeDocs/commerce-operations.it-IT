---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# Comunicazione server web sicura

Questo argomento illustra un esempio di protezione della comunicazione tra il server web e il motore di ricerca (Elasticsearch o OpenSearch) utilizzando una combinazione di crittografia TLS (Transport Layer Security) e [Autenticazione di base HTTP](https://datatracker.ietf.org/doc/html/rfc2617). È possibile configurare anche altri tipi di autenticazione; forniamo riferimenti a tali informazioni.

(Un termine precedente, SSL (Secure Sockets Layer), viene spesso utilizzato in modo intercambiabile con TLS. In questo argomento, ci riferiamo a *TLS*.)

>[!WARNING]
>
>Salvo diversa indicazione, tutti i comandi in questo argomento devono essere immessi come utente con `root` privilegi.

## Recommendations

Si consiglia quanto segue:

* Il tuo server web utilizza TLS.

   TLS va oltre lo scopo di questo argomento; tuttavia, consigliamo vivamente di utilizzare un certificato reale in produzione e non un certificato autofirmato.

* Il motore di ricerca viene eseguito sullo stesso host di un server web. L’esecuzione del motore di ricerca e del server web su host diversi va oltre l’ambito di questo argomento.

   Il vantaggio di mettere il motore di ricerca e il server web sullo stesso host è che rende impossibile intercettare la comunicazione crittografata. Il server web del motore di ricerca non deve necessariamente corrispondere al server web Adobe Commerce o Magenti Open Source; ad esempio, Adobe Commerce può eseguire Apache e Elasticsearch/OpenSearch può eseguire nginx.

   Se il motore di ricerca è esposto al Web pubblico, devi configurare l’autenticazione. Se l’istanza del motore di ricerca è protetta all’interno della rete, potrebbe non essere necessario. Collabora con il provider di hosting per determinare quali misure di sicurezza devi implementare per proteggere la tua istanza.

## Ulteriori informazioni su TLS

Consulta una delle risorse seguenti:

* Apache

   * [Procedura dettagliata sulla crittografia avanzata di Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Come creare un certificato SSL su Apache per Ubuntu 14.04 (tutorial DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configurazione di un server Web protetto SSL con CentOS (wiki CentOS)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Nginx terminazione SSL](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Come creare un certificato SSL sull&#39;indice Nginx per Ubuntu 14.04 (esercitazione Digitaloceanica)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Installazione certificato SSL Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
