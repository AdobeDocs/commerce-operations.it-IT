---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# Verificare che la comunicazione sia sicura

In questa sezione vengono descritti due modi per verificare il funzionamento dell&#39;autenticazione HTTP Basic:

* Utilizzo di un comando `curl` per verificare che sia necessario immettere un nome utente e una password per ottenere lo stato del cluster
* Configurazione dell’autenticazione HTTP Basic in Admin

## Utilizza un comando `curl` per verificare lo stato del cluster

Immetti il comando seguente:

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Ad esempio, se immetti il comando sul server del motore di ricerca e il proxy utilizza la porta 8080:

```bash
curl -i http://localhost:8080/_cluster/health
```

Viene visualizzato il seguente messaggio per indicare che l’autenticazione non è riuscita:

```
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Ora prova il seguente comando:

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Ad esempio:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Questa volta il comando ha esito positivo e viene visualizzato un messaggio simile al seguente:

```
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Configurare l’autenticazione HTTP Basic in Admin

Eseguire le stesse attività descritte nella [configurazione del motore di ricerca](../configuration/search/configure-search-engine.md) *eccetto* fare clic su **[!UICONTROL Yes]** dall&#39;elenco **[!UICONTROL Enable HTTP Auth]** e immettere il nome utente e la password nei campi specificati.

Fare clic su **[!UICONTROL Test Connection]** per verificare che funzioni, quindi fare clic su **[!UICONTROL Save Config]**.

Prima di continuare, è necessario svuotare la cache e reindicizzare.
