---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.62'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.62.
feature: Tools and External Services
role: Admin, Developer
exl-id: be8ffedc-b589-4a30-ba9a-eed705696825
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.62

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.62.

QPT v1.1.62 include le seguenti patch:

1. **ACSD-63406**: è stato corretto il problema per cui le virgolette persistenti scadute non vengono cancellate da alcun processo cron durante l&#39;esecuzione del processo cron `persistent_clear_expired`.
1. **ACSD-63520**: è stato corretto il problema per cui le immagini aggiunte tramite **[!UICONTROL Configurations]** nel pannello di amministrazione non rispettano il limite di dimensioni massime per il caricamento.
1. **ACSD-64523**: è stato risolto il problema che impediva la creazione di nuovi prodotti senza un nome tramite il processo di importazione (tramite Admin o API), interrompendo l&#39;interfaccia di amministrazione e causando la creazione di prodotti non validi.
1. **ACSD-64532**: è stato corretto il problema per cui una variabile ENV impostata su *false* viene trattata come stringa *false* invece di un valore booleano false.
1. **ACSD-64592**: è stato risolto il problema che causava il reindirizzamento della richiesta di risarcimento dal sito Web predefinito da parte del collegamento della richiesta di rimborso presente nell&#39;e-mail di una gift card in negozi non predefiniti.
1. **ACSD-65164**: è stato risolto il problema relativo al messaggio di errore *Alcune delle opzioni selezionate per l&#39;elemento non sono attualmente disponibili* si verifica quando si riordina un prodotto configurabile con una singola opzione selezionata per la casella di controllo personalizzata.
1. **ACSD-64732**: è stato risolto il problema che impediva la corretta memorizzazione nella cache dei controller di terze parti con i segmenti dei clienti.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
