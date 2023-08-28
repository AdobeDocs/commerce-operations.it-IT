---
title: Best practice per il ridimensionamento delle immagini del catalogo
description: Scopri come evitare il deterioramento delle prestazioni prima dell’avvio della produzione del tuo sito Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# Best practice per il ridimensionamento delle immagini del catalogo

Tutte le immagini del catalogo devono essere ridimensionate prima che un archivio entri in produzione. Il mancato ridimensionamento delle immagini prima della produzione forza il ridimensionamento delle immagini durante il caricamento della pagina, riducendo in modo significativo la velocità del sito e aumentando il carico del server nei primi giorni o settimane dopo il lancio.

## Il modo lento

Utilizzare il comando CLI predefinito per ridimensionare tutte le immagini:

```bash
bin/magento catalog:images:resize
```

Gli svantaggi di questo approccio comprendono:

- Il processo è a thread singolo
- Il processo ridimensiona le immagini già ridimensionate
- Il processo non può essere interrotto e ciò può richiedere giorni

## La modalità veloce

Il ridimensionamento asincrono delle immagini è stato introdotto in Adobe Commerce 2.4 e può ridimensionare le immagini più rapidamente.

1. Su ogni server web, avvia temporaneamente alcuni gestori di code aggiuntivi (il doppio del numero di processori fisici per server):

   ```bsh
   for i in {1.."$((2 * `nproc --all`))"};do bin/magento queue:consumers:start media.storage.catalog.image.resize &;done;
   ```

1. Verificare che i gestori delle code siano in esecuzione:

   ```bash
   pgrep -fl media.storage.catalog.image.resize
   ```

1. Compila la coda con tutte le richieste di ridimensionamento immagini:

   ```bash
   bin/magento catalog:images:resize --async
   ```

1. Dopo aver ridimensionato tutte le immagini, terminare il processo:

   ```bash
   pkill -f media.storage.catalog.image.resize
   ```

## La via veloce

Esiste un altro modo per ridimensionare le immagini utilizzando il front-end.

I vantaggi di questo approccio includono:

- Il processo è multithread
- Il processo è multiserver (se sono presenti più nodi Web, un load balancer e uno spazio su disco condiviso per `media/` directory)
- Il processo ignora le immagini già ridimensionate

Questo approccio consente di ridimensionare 100.000 immagini in meno di 8 ore, mentre il completamento del comando CLI richiede 6 giorni.

1. Accedi al server.
1. Accedi a `pub/media/catalog/product` e annota uno degli hash (ad esempio, 0047d83143a5a3a4683afdf1116df680).
1. Negli esempi seguenti, sostituisci `www.example.com` con il dominio del tuo archivio e sostituisci l’hash con quello indicato.

>[!BEGINTABS]

>[!TAB sed]

```bash
cd pub/
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' > images.txt
```

>[!TAB assedio]

Lo svantaggio di `siege` visita tutti gli URL nelle 10 volte se la concorrenza è impostata su 10.

```bash
siege --file=./images.txt --user-agent="image-resizer" --no-follow --no-parser --concurrent=10 --reps=once
```

>[!TAB ricciolo]

```bash
xargs -0 -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n" < <(tr \\n \\0 <images.txt)
```

Il `-P` determina il numero di thread.

>[!TAB bash one-liner]

Una riga per il `find/curl` esempio, nel caso in cui sia possibile eseguire `curl` dalla stessa macchina su cui si trovano le immagini:

```bash
find ./media/catalog/product -path ./media/catalog/product/cache -prune -o -type f -print | sed 's~./media/catalog/product/~https://www.example.com/media/catalog/product/cache/0047d83143a5a3a4683afdf1116df680/~g' | xargs -n 1 -P 10 curl -X HEAD -s -w "%{http_code} %{time_starttransfer} %{url_effective}\n"
```

Di nuovo, sostituisci `www.example.com` con il dominio e il set del sito web `-P` al numero di thread che il server può gestire senza arresti anomali.

>[!ENDTABS]

L’output restituisce un elenco di tutte le immagini del prodotto presenti nell’archivio. È possibile eseguire la ricerca per indicizzazione delle immagini `siege` o qualsiasi altro crawler) utilizzando tutti i server e i core del processore disponibili e generando la cache di ridimensionamento a una velocità notevolmente superiore rispetto ad altri approcci.

Se si visita un URL della cache delle immagini, vengono generate in background tutte le dimensioni delle immagini, se non esistono ancora. Inoltre, ignora i file che sono già stati ridimensionati.

>[!NOTE]
>
>- I progetti Adobe Commerce su infrastrutture cloud possono scaricare il ridimensionamento dell’immagine del prodotto sul servizio Fastly. Consulta [Ottimizzazione immagine profonda](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization.html?lang=en#deep-image-optimization) nel _Guida a Cloud_.
>- Se utilizzi il modulo di archiviazione remota, puoi anche provare a scaricare il ridimensionamento dell&#39;immagine su nginx. Consulta [Configurare il ridimensionamento delle immagini per l&#39;archiviazione remota](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-image-resize.html) nel _Guida alla configurazione_.
