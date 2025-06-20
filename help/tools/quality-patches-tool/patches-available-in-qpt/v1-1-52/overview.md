---
title: 'Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.52'
description: Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in  [!DNL Quality Patches Tool] (QPT) v1.1.52.
feature: Tools and External Services
role: Admin, Developer
exl-id: e6fc655e-0809-4b47-8be1-1fc36ae30753
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Panoramica: [!DNL Quality Patches Tool] (QPT) v1.1.52

Questa sottosezione fornisce una descrizione dettagliata dei problemi risolti dalle patch disponibili in [!DNL Quality Patches Tool] (QPT) v1.1.52.

QPT v1.1.52 include le seguenti patch:

1. **ACSD-59366**: è stato risolto il problema che si verificava in caso di errore durante l&#39;eliminazione di un team contenente utenti disattivati non visibili nell&#39;elenco dei team.
1. **ACSD-59865**: risolve il problema per cui [!UICONTROL Cart Price Rule] non annulla le regole applicate in precedenza se la quantità del prodotto nel carrello non è sufficiente per l&#39;applicazione delle regole.
1. **ACSD-59925**: è stato corretto il problema di ordinamento degli elementi nella raccolta multimediale in base alla posizione in GraphQL.
1. **ACSD-59952**: è stato corretto il problema che si verificava in caso di errore durante la creazione di un catalogo condiviso con un ID gruppo assegnato a un catalogo condiviso esistente.
1. **ACSD-60590**: migliora le prestazioni della generazione di *[!UICONTROL Bestsellers Aggregated Daily Reports]* per un grande volume di ordini effettuati.
1. **ACSD-60673**: è stato risolto il problema per cui [!UICONTROL Cart Price Rule] per più metodi di pagamento all&#39;atto dell&#39;estrazione non viene applicato in modo appropriato al metodo di pagamento specifico.
1. **ACSD-60684**: è stato risolto il problema che impediva l&#39;ordinamento dei prodotti GraphQL in base a più campi.
1. **ACSD-60788**: è stato risolto il problema che impediva l&#39;esecuzione degli script personalizzati per [!DNL Google Tag Manager] a causa di errori CSP (Content Security Policy).
1. **ACSD-61322**: è stato corretto il problema per cui Prodotti/Categorie non assegnati a [!UICONTROL Shared Catalog] per il gruppo predefinito (Gruppo generale) sono ancora inclusi in XML Sitemap.
1. **ACSD-61366**: è stato risolto il problema che causava l&#39;esecuzione del comando `setup:static-content:deploy --jobs 4` con più processi non riusciti. L&#39;errore *Port deve essere configurato nell&#39;errore del parametro host* quando la porta è specificata per la connessione DB.

Utilizza il menu a sinistra per passare a una pagina patch specifica.
