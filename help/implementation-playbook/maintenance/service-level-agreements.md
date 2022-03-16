---
title: Accordi a livello di servizio
description: Scopri gli accordi sui livelli di servizio e come utilizzarli per supportare l’implementazione Adobe Commerce.
exl-id: 5da42dfa-e165-4142-a863-6f3ce7689478
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---

# Accordi a livello di servizio (SLA)

Il contratto a livello di servizio (SLA) definisce il livello di servizio atteso da un cliente del fornitore di servizi, con semplici metriche in base alle quali viene misurato il servizio, nonché i rimedi o le eventuali sanzioni in caso di mancato raggiungimento dei livelli di servizio concordati.

Gli SLA per diversi tipi di criticità di incidenti possono essere contratti, mantenuti e misurati. Inoltre, il tipo di risposta può avere più standard (Gold, Platinum), in base al livello di servizio richiesto dal cliente.

La tabella seguente descrive una suddivisione metrica SLA tipica con più livelli di servizio:

<table>
<thead>
  <tr>
    <th>Tipo di problema</th>
    <th>Impatto</th>
    <th>Esempio</th>
    <th colspan="2">Tempo di risposta/ripristino durante l'orario di lavoro supportato</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>Oro</td>
    <td>Platino</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Impatto critico</td>
    <td>Servizio inattivo o inutilizzabile</td>
    <td>1 ora / 4 ore</td>
    <td>1 ora / 4 ore</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Servizio non disponibile</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Servizio inutilizzabile nell'intera base utente finale</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>Impatto elevato</td>
    <td>Servizio gravemente compromesso</td>
    <td>2 ore / 12 ore</td>
    <td>2 ore / 8 ore</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Le prestazioni del servizio sono degradate</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Servizio disponibile, ma che genera messaggi di errore significativi</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>Impatto medio</td>
    <td>Servizio parzialmente compromesso</td>
    <td>8 ore / 16 ore</td>
    <td>8 ore / 12 ore</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Messaggi di errore generati, nessun impatto notevole sull'utente finale</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Domande sulle funzioni utilizzate nel lancio del cliente</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## Opzioni di copertura

Le opzioni di copertura per gli SLA impegnati variano in base ai diversi tipi di offerta. In genere, l’ambito dei servizi di supporto Gold e Platinum ha un aspetto simile al seguente:

![Infografica che mostra le opzioni di copertura SLA](../../assets/playbooks/sla-coverage-options.svg)
