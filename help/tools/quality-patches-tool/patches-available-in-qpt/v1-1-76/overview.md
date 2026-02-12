---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.76.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: aeda6ddd9bac7e5f81329d9bd05ab8957ef2fb76
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.76

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.76.

QPT v1.1.76 include le seguenti patch:
1. **ACSD-67091**: corregge l&#39;errore relativo alle dimensioni massime del set di scrittura per garantire la pulizia dell&#39;indice del prodotto della regola del catalogo implementando due strategie di eliminazione basate sul volume dei dati.
1. **ACSD-67370**: sono stati risolti diversi problemi a causa dei quali venivano visualizzati prezzi non corretti per i prodotti Bundle su PDP/PLP e per la pagina del carrello per gli archivi multivaluta.
1. **ACSD-68410**: è stato corretto un problema a causa del quale l&#39;inserimento di un ordine per un preventivo negoziabile aggiungeva o univa erroneamente righe aggiuntive del carrello al preventivo. I prodotti vengono ora aggiunti correttamente al carrello dopo aver lasciato l’ultimo passaggio del pagamento delle offerte negoziabili.
1. **ACSD-69086**: è stato risolto il problema che impediva al processo cron di cancellare le tabelle del registro delle modifiche, causando [!DNL Galera Cluster] arresti anomali durante la gestione di grandi quantità di dati.
1. **ACSD-69115**: è stato risolto un problema che impediva la visualizzazione degli errori del carrello all&#39;utente amministratore durante la gestione del carrello per un cliente assegnato a un sito Web non predefinito.
1. **ACSD-69129**: è stato risolto un problema che causava l&#39;eliminazione del sito Web di base predefinito e l&#39;utilizzo del sito Web secondario come sito Web predefinito, causando un errore durante il tentativo di aggiornamento del prezzo del sito Web secondario tramite l&#39;API [!DNL REST].
1. **ACSD-69203**: è stato risolto un problema a causa del quale il widget **[!UICONTROL Products List]** restituiva risultati non corretti quando più categorie erano elencate nella condizione di categoria.
1. **ACSD-69261**: è stato risolto un problema che causava il riutilizzo più volte di un coupon della regola di prezzo del carrello configurato per l&#39;uso singolo per cliente a causa di una gestione non corretta dell&#39;attributo `times_used` nella fattura parziale e negli scenari di annullamento della quantità rimanenti.
1. **ACSD-69308**: è stato corretto un problema a causa del quale le regole del prezzo di catalogo non venivano applicate quando `special_price` era impostato solo a livello di sito Web (non a **[!UICONTROL All Store Views]**). Dopo la correzione, le regole del prezzo del catalogo vengono applicate correttamente controllando prima il negozio predefinito del sito web.
1. **ACSD-69319**: è stato corretto un problema a causa del quale i prezzi dei bundle non venivano indicizzati correttamente quando i prodotti secondari disponevano di scorte in origini personalizzate.
1. **ACSD-69325**: è stato risolto un problema che causava la mancata disponibilità del prodotto nella vetrina a causa della modifica del case SKU.
1. **ACSD-69331**: è stato risolto un problema che impediva ai creatori di contenuto nella raccolta multimediale di creare cartelle con l&#39;autorizzazione `create_folder`. Dopo la correzione, può creare le cartelle come previsto.
1. **ACSD-69333**: è stato risolto un problema che consentiva le modifiche SKU per i prodotti con un aggiornamento pianificato attivo. Dopo la correzione, le modifiche SKU non sono consentite durante gli aggiornamenti attivi; il salvataggio non riesce e viene visualizzato un errore di cancellazione e il campo SKU amministratore è disabilitato. Questo impedisce a MSI di:
1. **ACSD-69541**: è stato corretto un problema a causa del quale la riduzione della quantità di un prodotto nell&#39;amministratore a un livello inferiore a quello esistente in un carrello impediva la modifica della quantità di prodotto nel carrello tramite GraphQL.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
