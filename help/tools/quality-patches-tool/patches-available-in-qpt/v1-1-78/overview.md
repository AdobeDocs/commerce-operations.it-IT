---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.78.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: cc3bd15a0c11762812e4e51e4c01bfa64756421a
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.78

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 include le seguenti patch:
1. **ACP2E-4416**: è stato risolto il problema che impediva l&#39;inizializzazione dei punti premio cliente creati nell&#39;amministratore.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: è stato risolto il problema che impediva l&#39;applicazione corretta delle gift card al momento del pagamento dopo la convalida reCAPTCHA v2 (&#39;I am not a robot&#39;) nella vetrina.
1. **ACP2E-4431**: è stato risolto il problema che causava l&#39;eliminazione dei prodotti correlati corrispondenti alle regole di destinazione durante il processo di reindicizzazione.
1. **ACP2E-4448**: è stato risolto il problema che impediva la visualizzazione delle modifiche apportate alla configurazione durante le interruzioni di Redis dopo il ripristino di Redis, causando la persistenza di valori non aggiornati.
1. **ACP2E-4452**: è stato risolto il problema che determinava l&#39;inclusione dell&#39;imposta nei prezzi dei prodotti nella pagina Ordine rapido indipendentemente dalla configurazione della visualizzazione delle imposte.
1. **ACP2E-4456**: è stato corretto un problema a causa del quale l&#39;annullamento di un ordine tramite una mutazione GraphQL non comporta la transizione di un ordine pagato interamente con gift card allo stato Chiuso.
1. **ACP2E-4507**: è stato risolto il problema che impediva l&#39;applicazione della configurazione delle opzioni password per le richieste di reimpostazione della password dei clienti effettuate tramite mutazioni GraphQL.
1. **ACP2E-4513**: è stato risolto il problema che impediva l&#39;eliminazione dal sistema delle immagini CAPTCHA scadute.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: è stato risolto il problema relativo a un errore di chiave duplicata intermittente nella tabella quote_coupons quando vengono eseguite contemporaneamente più richieste di unione carrello o salvataggio preventivo.
1. **ACP2E-4528**: è stato risolto il problema relativo alla convalida della città negli indirizzi dei clienti, che ora consente l&#39;utilizzo del carattere barra (/) e rifiuta i caratteri non validi come !, &quot;, # e ?.
1. **ACP2E-4535**: è stato risolto un problema che causava l&#39;eliminazione o la rigenerazione della sessione (modifiche PHPSESSID) e l&#39;eliminazione del carrello guest.
1. **ACP2E-4540**: è stato risolto il problema che impediva il caricamento corretto della libreria Fotorama, rendendo visibile solo la prima immagine allegata.
1. **ACP2E-4555**: è stato risolto il problema relativo ai numeri di telefono moderni contenenti &quot;.&quot; o &quot;/&quot; non sono convalidati correttamente.
1. **ACP2E-4565**: è stato risolto il problema per cui la query GraphQL della società restituisce &quot;Il cliente corrente non è autorizzato&quot; quando viene utilizzata l&#39;intestazione X-Adobe-Company.
1. **ACP2E-4591**: è stato risolto il problema che impediva l&#39;aggiornamento dei segmenti cliente basati sul conteggio degli ordini, ad esempio &quot;Acquirenti nuovi&quot;, quando venivano effettuati gli ordini tramite l&#39;API REST.
1. **ACP2E-4609**: è stato risolto il problema che impediva la visualizzazione di virgolette nella pagina Le mie virgolette quando alcune virgolette contengono prodotti eliminati.
1. **ACP2E-4613**: è stato risolto il problema relativo alle strutture di directory multimediali di grandi dimensioni, che causava risposte lente e tempi di caricamento estesi della struttura di directory di Media Gallery.
1. **ACP2E-4628**: è stato corretto il problema per cui l&#39;importazione di clienti con indirizzi e-mail in maiuscolo causava l&#39;errore di chiave di matrice non definita quando Condivisione account era impostato su Globale.
1. **ACP2E-4665**: è stato risolto il problema che impediva l&#39;elenco dei prodotti secondari di prodotti configurabili contenenti video nelle raccolte prodotti, se richiesto tramite API REST.
1. **ACP2E-4732**: è stato risolto un problema che causava l&#39;interruzione dell&#39;indicizzazione parziale per i clienti con un numero elevato di aggiornamenti quando la colonna version_id nella tabella changelog raggiungeva il valore massimo.
1. **ACP2E-4763**: è stato risolto il problema che si verificava se la query GraphQL customerOrders restituiva valori gonfiati come original_price_included_tax e original_row_total_included_tax quando i prezzi del catalogo sono impostati su Includi imposta, a causa dell&#39;applicazione dell&#39;imposta due volte.
1. **ACSD-60989**: risolve il problema se la modifica di una colonna con una chiave esterna tramite uno schema dichiarativo causa errori in MariaDB.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
