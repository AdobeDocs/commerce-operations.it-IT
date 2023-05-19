---
title: Il [!UICONTROL bots] scheda
description: Scopri di più su [!UICONTROL bots] scheda di [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
source-git-commit: 043389dc6d86228e459ac2c3592f391e85aa8f68
workflow-type: tm+mt
source-wordcount: '1862'
ht-degree: 0%

---

# Il [!UICONTROL bots] scheda

Questa scheda contiene informazioni che spiegano come identificare se e cosa [!DNL bots] stanno causando problemi al sito.

## Panoramica di alto livello di [!DNL bots]:

* A [!DNL bot] è un componente software che esegue operazioni automatizzate ripetitive. Con l&#39;evoluzione dell&#39;intelligenza artificiale e dell&#39;apprendimento automatico, le attività, i metodi e le interazioni di [!DNL bots] stanno cambiando. Ci sono *buono* [!DNL bots] che traggono vantaggio dai siti effettuando ricerche per indicizzazione e aggiungendoli ai motori di ricerca internet. In questo modo gli utenti di Internet vengono guidati al sito attraverso i risultati dei motori di ricerca. A *buono* [!DNL bot] in genere rispetta i limiti posizionati sul [!DNL bot] da un `robots.txt` file o impostazioni in una console del motore di ricerca. I limiti possono limitare l&#39;accesso al sito o a parti del sito.
* Malizioso [!DNL bots] ignora `robots.txt` file o possono falsificare una [!DNL bot] tramite il campo request user agent (agente utente richiesta) dei dati della richiesta HTTP. Alcune cose dannose [!DNL bots] eseguire le operazioni seguenti:
   * Aggiungi il carico a un sito per negare l’accesso al sito agli utenti legittimi.
   * Eliminare e riutilizzare i contenuti senza autorizzazione.
   * Registrare account falsi per inondare i servizi e-mail o gli indirizzi o reindirizzare ad altri siti ([!DNL SPAM bots]).
   * Creare visualizzazioni false ([!DNL Viewbots]).
   * Acquista prodotti o biglietti ([!DNL Focused bots]).
* Gestione [!DNL bots]
   * [!DNL Observation for Adobe Commerce] ha visualizzazioni di [!DNL bot] traffico:
      * Mostra il totale dei messaggi non memorizzati in cache [!DNL bot] attività che visualizza il carico che un [!DNL bot] sta aggiungendo a un sito e quando si verifica tale caricamento.
      * Mostra la [!DNL bots] che generano errori. In genere, se un [!DNL bot] : aggiunta di carico che causa problemi al sito, che [!DNL bot] L&#39;indirizzo IP o ha la frequenza più elevata di errori.
      * Mostra [!DNL bot] nomi (valori dei campi dell’agente utente della richiesta) e indirizzi IP da gestire tramite:
         * [!DNL Fastly] (limitando la velocità o [!DNL VCLs] che bloccano indirizzi IP, intervalli o [!DNL bots] per nome (valore).
         * Aggiunta di buone [!DNL bot] informazioni al `robots.txt field` per limitare o limitare la velocità di accesso al sito.
         * Gestione [!DNL Bing] o [!DNL Google bots] tramite la console dei motori di ricerca.

## [!UICONTROL Total Bot traffic by bot name]:

![Traffico bot totale per nome bot durante il periodo di tempo selezionato:](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

* Il **[!UICONTROL Total Bot traffic by bot name during selected time period]** contiene il conteggio aggregato delle richieste non memorizzate in cache in cui [!UICONTROL request_user_agent] il campo ha una stringa di [!DNL bots] nel valore. Questo può essere o meno il nome [!DNL bot] come [!UICONTROL request_user_agent] il valore del campo può essere oggetto di spoofing. Il valore sotto [!UICONTROL Count] è la colonna più importante.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![Traffico bot totale per nome bot/indirizzo IP durante il periodo di tempo selezionato Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

* Il **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** mostra gli stessi dati della tabella precedente, ma aggiunge indirizzi IP che effettuano le richieste per conto del [!DNL bot]. Come dannoso [!DNL bots] parodia buona [!DNL bots], gli indirizzi IP devono essere verificati tramite siti web che identificano gli indirizzi IP abusivi o tramite *chiosco* servizi o [!DNL DNS lookups]. Ad esempio: [!DNL Google] pubblica i propri [[!DNL googlebot] Indirizzi IP](https://developers.google.com/search/apis/ipranges/googlebot.json) e [!DNL Microsoft] dispone di uno strumento di verifica per [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![Grafico: bot con errori di stato HTTP durante il periodo di tempo selezionato Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

* Il **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** il grafico mostra gli errori su [!DNL bots] che si dichiarano nel campo request user agent (richiede agente utente). Ciò non significa necessariamente che l’errore sia causato dal volume proveniente da [!DNL bot] o altro traffico. Gli errori potrebbero essere [!DNL bot] sta richiedendo informazioni inesistenti o si è verificato un altro problema nella richiesta.
* Se si verifica un picco di errori sugli indirizzi IP durante l’instabilità o l’interruzione del sito, potrebbero essere sospettati di un problema del sito.

## [!UICONTROL Table - IPs that do not identify as bots]

![Tabella: IP che non si identificano come bot con errori di stato HTTP durante il periodo di tempo selezionato Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

* Il **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** La tabella mostrerà le richieste IP con codici di stato http diversi da 200 che NON si autoidentificano come [!DNL bots] nel campo richiedi agente utente. Questi indirizzi IP potrebbero essere indirizzi IP dannosi, soprattutto se il conteggio è elevato per il periodo di tempo selezionato.
* Se il numero di codici di stato http diversi da 200 è basso e gli intervalli di indirizzi IP non sono simili, gli indirizzi potrebbero non contribuire ai problemi del sito.

## [!UICONTROL Table – Cache Status 'ERROR']

![Tabella: tabella di dettaglio &#39;ERROR&#39; dello stato della cache (cosa fanno questi IP?) Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

* Quando gli indirizzi IP generano una frequenza elevata di errori, chiedi cosa stanno facendo? Il **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** La tabella mostra l’URL richiesto e il valore dello stato HTTP per le richieste con uno stato della cache [!UICONTROL ERROR] valore. La frequenza è influenzata dall’URL, pertanto il conteggio potrebbe essere basso. Ricorda che l’indirizzo IP potrebbe effettuare migliaia di richieste durante il periodo di tempo selezionato. Si tratta di una visualizzazione rispetto a un massimo di 2000 richieste durante l’intervallo di tempo (il limite di visualizzazione dei record).

## [!UICONTROL Show 5XX status distribution]

![Mostra distribuzione dello stato 5XX tra gli indirizzi IP (primi 200 indirizzi) Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

* Il **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** è potente. Mostra gli indirizzi IP che hanno codici di stato http 5XX durante il periodo di tempo selezionato. Se un indirizzo IP effettua un elevato volume di richieste e il sito è interessato al punto tale da non essere in grado di gestire il traffico, gli indirizzi IP che effettuano la frequenza più elevata di richieste avranno in genere il maggior volume di errori. I codici di stato http 5XX indicano in genere un sito che ha difficoltà a rispondere alle richieste.
* Più è ampia la barra, maggiore è la percentuale di errori che l’indirizzo IP ha nel numero totale di errori 5xx durante quel periodo di tempo. Nota: un indirizzo IP può avere più segmenti nel grafico se dispone di più codici di stato http (ad esempio, stati http 502 e 503).
* La distribuzione tipica sarebbe indicata verso il lato destro della barra in cui gli indirizzi IP sono uguali in larghezza oppure ci sarebbero alcune barre larghe con conteggi molto bassi.
* Se passi il cursore del mouse sul segmento della barra, viene visualizzato il numero di errori indicati durante il periodo di tempo selezionato.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![Stato della cache IP (MISS, PASS, ERROR) e stato http durante il periodo di tempo selezionato Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

* Questo **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** mostra il conteggio dei codici di stato HTTPS e le richieste non memorizzate in cache per IP nell’intervallo di tempo selezionato. Indica il carico proporzionale da ciascun indirizzo IP e il volume totale. Mostrerà gli indirizzi IP con il maggior numero di richieste.

## [!UICONTROL Fastly Cache Summary for selected time period]

![Riepilogo Fastly Cache per il periodo di tempo selezionato](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

* Se si fa clic sul pulsante [!UICONTROL Error] nel grafico seguente, puoi confrontare gli ultimi due grafici tra loro. Questo può aiutare a indicare dove il caricamento contribuisce ai problemi del sito.

![Controllo rapido degli errori](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![IP che non si identificano come bot senza errori durante il periodo di tempo selezionato Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

* Il **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** Il frame mostra il campo dell’agente utente della richiesta, l’indirizzo IP e il codice di stato per le richieste in cui il campo dell’agente utente della richiesta non indica un [!DNL bot]. Questo frame può mostrare richieste ad alta frequenza da qualsiasi indirizzo IP, ma prestare attenzione alle richieste ad alta frequenza, soprattutto durante un periodo di tempo in cui il sito può avere problemi.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![Traffico non bot sospetto durante il periodo di tempo selezionato](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

* Il **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** Il grafico cerca il valore Go-http-client dell’agente utente della richiesta, ma verrà esteso per esaminare altri valori sospetti dell’agente utente della richiesta. Questo valore dell&#39;agente utente della richiesta viene utilizzato dai siti per la connessione dai servizi e può essere valido, ma è utilizzato anche da utenti malintenzionati [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![Grafico: traffico bot per nome bot durante il periodo di tempo selezionato)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

* Il **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** mostra gli stessi dati del traffico Bot totale per [!DNL Bot] nome durante la tabella del periodo di tempo selezionato nella parte superiore della scheda. Mostra i dati tramite la timeline in modo da poter vedere quando le richieste di [!DNL bots] e la loro distribuzione.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![Primi 250 nomi di bot e indirizzi IP durante il periodo di tempo selezionato Come bloccare il traffico da bot a livello Fastly O gestire i bot tramite il file robots.txt Best practice per i robot Adobe Commerce.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

* Il **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** Il fotogramma mostra gli stessi dati del totale [!DNL Bot] Traffico per nome bot/indirizzo IP durante la tabella del periodo di tempo selezionata nella parte superiore della scheda. Mostra i dati tramite la timeline e facet per indirizzo IP. Questo mostra quando le richieste di [!DNL bots] vengono effettuate, l’IP che effettua le richieste e le distribuzioni delle richieste.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![Nome bot/indirizzi IP bloccati (in Fastly) durante il periodo di tempo selezionato. Questo grafico mostra il traffico da bot e gli IP che hanno restituito il codice di stato HTTP 403 non consentito](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

* Il **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** mostra il nome bot e gli indirizzi IP bloccati. Questo grafico mostra come tutte le richieste sono bloccate in [!DNL Fastly] avanti.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![Nome/indirizzo IP non bot bloccato (in Fastly) durante il periodo di tempo selezionato. Questo grafico mostra il traffico non-bot e gli IP che hanno restituito il codice di stato HTTP 403 non consentito ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

* Il **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** mostra gli indirizzi IP che non si identificano come [!DNL bot] che sono stati bloccati tramite [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![Questa tabella mostra il numero di agenti utente per indirizzo IP e il numero di richieste riuscite, non riuscite e bloccate:](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

* Malizioso [!DNL bots] spesso spoof altro [!DNL bots] attraverso il valore del [!UICONTROL Request User Agent] campo. Questa tabella mostra quanti valori univoci ha l’indirizzo IP in quel campo. Più alto è il valore in [!UICONTROL Request User Agent] più l’indirizzo IP è sospetto.

## [!UICONTROL IP with non-200 status errors]

![IP con errori di stato non 200 - senza stato 403](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

* Il **[!UICONTROL IP with non-200 status errors – without 403 status]** Il frame mostra la distribuzione nell’arco temporale selezionato di indirizzi IP con codici di stato HTTP diversi da 200. I valori più elevati che si osservano su un singolo IP o gruppo di indirizzi IP richiedono ulteriori indagini.

## [!UICONTROL IP with 403 status codes:]

![IP con codici di stato 403:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

* Il **[!UICONTROL IP with 403 status codes]** il fotogramma mostra le richieste non memorizzate in cache senza [!UICONTROL cache_status=ERROR] che hanno uno stato HTTP 403. Questo può mostrare che il server di origine è l’origine del 403 (non autorizzato) piuttosto che un blocco da [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![Primi 5 con codici di stato diversi da 200 che mostrano cache_status:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

* Il **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** tabella mostra a livello di IP / stato i conteggi di ciascuno con il [!UICONTROL cache_status] valore.

## [!UICONTROL Pageview Latency will show as spikes]

![La latenza di Pageview verrà visualizzata come picchi in questo grafico:](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

* Il **[!UICONTROL Pageview Latency will show as spikes on this graph:]** mostra la latenza di caricamento pagina/risposta API che potrebbe essere in linea con il [!DNL bot] traffico.

## [!UICONTROL Experimental Potential Malicious Bots] frame

![Potenziale sperimentale Bots dannosi frame](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame.jpg)

Il **[!UICONTROL Experimental Potential Malicious Bots]** frame esegue dieci query separate e complesse. Rileva le firme di richieste IP dannose e quindi aggrega i risultati, le somme e li ordina in base al conteggio in ordine decrescente. Le query contengono una moltitudine di firme di dati di exploit CVE e altre richieste dannose. Anche quando gli exploit sono bloccati da correzioni/patch di sicurezza e non rappresentano una minaccia per il sito, la richiesta deve ancora essere gestita dal sito web. Il volume delle richieste può diventare significativo in un breve periodo di tempo. Questo frame non mostra il totale delle richieste provenienti dall’indirizzo IP, ma le richieste che presentano segnali che indicano che le richieste avevano un intento sospetto.

Assicurati di verificare che il traffico sia sospetto e non provenga da un indirizzo CDN (Content Distributed Network) che potrebbe anche fornire richieste valide. Se le richieste provengono da un indirizzo IP CDN, contatta il fornitore del servizio per aiutarti a bloccare il traffico sospetto attraverso la rete. Se devi bloccare l’indirizzo o richiedere l’URL, consulta [Blocca traffico dannoso per Adobe Commerce su [!DNL Fastly] livello](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) nella Knowledge Base di supporto di Adobe Commerce.
