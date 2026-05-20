---
title: criteri del ciclo di vita Adobe Commerce
description: Scopri i periodi di supporto di Adobe Commerce, le date di fine del supporto e di applicazione del cloud, le disposizioni transitorie e i percorsi verso una versione supportata.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 0%

---


# criteri del ciclo di vita Adobe Commerce

Adobe Commerce segue un criterio definito per il ciclo di vita del software per garantire che i clienti utilizzino versioni sicure e supportate. Se ti trovi su una release precedente, è fondamentale capire dove si colloca questo ciclo di vita (e agire prima delle scadenze di implementazione). Questo argomento tratta le definizioni dei livelli di supporto, le date di fine del supporto e di applicazione, le disposizioni transitorie per le versioni prossime alla fine del ciclo di vita e i percorsi per rimanere in una versione supportata.

>[!IMPORTANT]
>
>Adobe sta introducendo un criterio di aggiornamento della versione applicato per Adobe Commerce su Cloud (PaaS). A partire dal **1 giugno 2027**, Adobe interromperà la manutenzione degli ambienti Cloud che eseguono versioni di Commerce non supportate e si riserva il diritto di disattivarli. Se esegui su Cloud (PaaS), devi passare a una versione di Adobe Commerce supportata o eseguire la migrazione a [!DNL Adobe Commerce as a Cloud Service] prima della data di [fine del supporto esteso](lifecycle-policy.md#end-of-support-dates) pubblicata per la riga di rilascio. Consulta [Criteri di applicazione dell&#39;aggiornamento della versione cloud](version-upgrade-enforcement-policy.md) per le date di applicazione, le versioni interessate e ciò che accade se utilizzi una versione non supportata.

## Informazioni sui livelli di supporto

Adobe Commerce definisce tre livelli di supporto per le linee di rilascio. Le sezioni seguenti descrivono ogni livello.

### Supporto regolare

Il periodo di supporto standard di tre anni dalla data di disponibilità generale (General Availability, GA). Il supporto regolare include correzioni di qualità, patch di sicurezza e supporto Adobe Commerce on-call completo.

- **Correzioni di qualità** - I clienti possono accedere alle correzioni di qualità contattando [il supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o tramite [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) self-service.

- **Correzioni di sicurezza** - Adobe fornisce correzioni di sicurezza tramite patch di sicurezza cumulative e [file di patch di sicurezza isolati](versioning-policy.md#isolated-security-patch-file) non cumulativi per il periodo di supporto di tre anni.

- **Hotfix**: per problemi critici di sicurezza, ad esempio vulnerabilità a zero giorni, Adobe fornisce [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) per tutti i clienti che utilizzano una versione supportata, anche se non si trovano nell&#39;ultima versione della patch o della patch di sicurezza. Tieni presente che un hotfix non è completo e non risolve tutti i problemi di sicurezza che verrebbero risolti con l’aggiornamento alla versione più recente.

### Supporto esteso

Estensione di supporto di un anno disponibile per specifiche linee di rilascio oltre al supporto regolare. Include patch di qualità e sicurezza. Disponibile solo per i clienti Adobe Commerce, non disponibile per Magento Open Source.

### Periodo transitorio solo titolo

Un periodo transitorio unico e limitato nel tempo disponibile per specifiche versioni il cui supporto esteso è terminato nel 2025 o nel 2026. Il periodo transitorio riservato alla sicurezza prevede solo alcune correzioni isolate. Il supporto on-call di Adobe Commerce non è incluso. Questo periodo non equivale a un sostegno regolare o esteso e non verrà prorogato ulteriormente. Consideralo come un periodo di migrazione, non come un livello di supporto a lungo termine. Vedere [Disposizioni transitorie per la sola protezione](#security-only-transitional-provisions).

## Date di fine del supporto

La tabella seguente mostra l’intero ciclo di vita di ogni versione di Adobe Commerce, comprese le date di imposizione dell’aggiornamento della nuova versione per gli ambienti Adobe Commerce on Cloud (PaaS).

| Versione | Disponibilità generale | Fine del supporto regolare | Fine del supporto esteso | Fine del periodo di sola protezione | [Data di applicazione dell&#39;aggiornamento della versione (solo cloud)](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | 12 maggio 2026 | 31 maggio 2029 | TBD | N/D | TBD |
| Adobe Commerce 2.4.8 | 8 aprile 2025 | 31 maggio 2028 | TBD | N/D | TBD |
| Adobe Commerce 2.4.7 | 9 aprile 2024 | 31 maggio 2027 | 31 maggio 2028 | N/D | 1 giugno 2028 |
| Adobe Commerce 2.4.6 | 14 marzo 2023 | 11 agosto 2026 | 30 agosto 2027 | 31 maggio 2028 | 1 giugno 2028 |
| Adobe Commerce 2.4.5 | 9 agosto 2022 | 12 agosto 2025 | 12 agosto 2026 | 31 maggio 2027 | 1 giugno 2027 |
| Adobe Commerce 2.4.4 | 12 aprile 2022 | 12 aprile 2025 | 14 aprile 2026 | 31 maggio 2027 | 1 giugno 2027 |

{style="table-layout:auto"}

Se la tua riga di rilascio si avvicina o supera queste date, consulta [Opzioni di aggiornamento e migrazione](#upgrade-and-migration-options). Per informazioni dettagliate sull&#39;imposizione cloud, vedere [Criteri di applicazione dell&#39;aggiornamento della versione cloud](version-upgrade-enforcement-policy.md).

### Timeline di supporto per trimestre

Utilizzare questo grafico per visualizzare la sovrapposizione delle finestre di supporto tra le righe della versione. Per le date di fine esatte, consulta le tabelle precedenti. Il supporto esteso per 2.4.8 e 2.4.9 è da definire e non viene visualizzato.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
    <th colspan="4">2029</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
    <td>Q1</td>
    <td>Q2</td>
    <td>Q3</td>
    <td>Q4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Chiave**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Supporto regolare</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Supporto esteso</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Periodo transitorio solo titolo</td>
  </tr>
 </tbody>
</table>

## Disposizioni transitorie per il solo titolo {#security-only-transitional-provisions}

Come misura una tantum per le versioni 2.4.4, 2.4.5 e 2.4.6 con supporto esteso già terminate nel 2025 e 2026, Adobe fornisce le seguenti disposizioni transitorie per darti più tempo per pianificare ed eseguire la migrazione o l’aggiornamento. Queste disposizioni non sostituiscono [Applicazione dell&#39;aggiornamento della versione cloud](version-upgrade-enforcement-policy.md) per gli ambienti PaaS. È comunque necessario eseguire l’aggiornamento o la migrazione prima della data di applicazione pubblicata.

| Versione | Disposizione transitoria | Periodo | Cosa è incluso | Cosa non è incluso |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4 e 2.4.5 | Periodo transitorio solo titolo | Fino al 31 maggio 2027 | Limitate correzioni di sicurezza isolate, caso per caso | Supporto on-call per Adobe Commerce, correzioni di qualità, aggiornamenti delle dipendenze dalla piattaforma |
| 2.4.6 | Supporto esteso + periodo transitorio per il solo livello di sicurezza | Supporto esteso fino al 30 agosto 2027. Periodo di sola sicurezza fino al 31 maggio 2028. | Periodo di supporto esteso: patch di qualità e sicurezza. Periodo di sola sicurezza: correzioni di sicurezza isolate limitate. | Durante il periodo di sola sicurezza: supporto Adobe Commerce on-call, correzioni di qualità, aggiornamenti delle dipendenze dalla piattaforma |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>Il periodo transitorio riservato ai soli titoli costituisce un&#39;eccezione una tantum. Non verrà esteso oltre le date di pubblicazione. Considera il periodo di sola sicurezza come tempo di migrazione e non come livello di supporto a lungo termine.

## Dipendenze della piattaforma

L’utilizzo di una versione di Commerce supportata richiede anche dipendenze di piattaforma supportate. Adobe non fornisce correzioni di sicurezza e di qualità per servizi di terze parti e dipendenze software, come PHP, MariaDB, OpenSearch, Redis, Valkey, RabbitMQ e altri, che possono raggiungere la fine del ciclo di vita durante il periodo di supporto di tre anni o esteso per Adobe Commerce.

L’utente è responsabile della gestione di tutte le dipendenze di terze parti e dei servizi di piattaforma sulle versioni attivamente supportate. Consulta [Requisiti di sistema](../installation/system-requirements.md) per l&#39;elenco completo delle tecnologie di terze parti testate e supportate.

Adobe non fornisce supporto o assistenza per la sicurezza delle distribuzioni che eseguono versioni di dipendenza non supportate. Per informazioni dettagliate, vedere [Modello operativo e di sicurezza con responsabilità condivisa](../security-and-compliance/shared-responsibility.md).

>[!IMPORTANT]
>
>L’esecuzione di versioni di dipendenza non supportate può causare una vulnerabilità di sicurezza nell’istanza Cloud che Adobe non è in grado di risolvere. In questi casi, Adobe si riserva il diritto di applicare un aggiornamento della dipendenza software interessata o di disattivare il servizio se un aggiornamento non è possibile, indipendentemente dallo stato di supporto della versione di Adobe Commerce.

## Fine del ciclo di vita PHP e conformità PCI

È tua responsabilità monitorare lo stato di supporto delle versioni PHP utilizzate negli ambienti.

Le seguenti versioni PHP utilizzate dalle precedenti linee di rilascio di Commerce hanno raggiunto o raggiungeranno la fine del ciclo di vita, il che ha implicazioni dirette per la conformità PCI.

| Versione PHP | Data di fine del ciclo di vita | Versioni Commerce interessate | Impatto sulla conformità PCI |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | 31 dicembre 2025 | 2.4.4, 2.4.5 e 2.4.6 (dove si utilizza PHP 8.1) | Conformità PCI a rischio: l&#39;esecuzione di PHP 8.1 oltre la data di fine del ciclo di vita significa che le vulnerabilità di sicurezza in PHP potrebbero non ricevere correzioni, il che mette a rischio la conformità PCI. Valuta lo stato di conformità e assegna priorità all&#39;aggiornamento. |
| PHP 8.2 | 31 dicembre 2026 | 2.4.6 (se viene utilizzato PHP 8.2) | Conformità PCI a rischio a partire dalla fine del 2026 — pianificare l’aggiornamento o la migrazione prima della fine del 2026 per mantenere la conformità PCI. |

{style="table-layout:auto"}

### Avviso di conformità PCI

La conformità PCI è responsabilità dell&#39;esercente valutare. Adobe consiglia vivamente ai commercianti delle versioni interessate di consultare un valutatore della sicurezza qualificato e di privilegiare il passaggio a una versione di Commerce supportata e a una versione PHP supportata il prima possibile. Per le timeline di supporto PHP, vedere [Versioni supportate PHP](https://www.php.net/supported-versions.php) e [fine del ciclo di vita PHP](https://www.php.net/eol.php).

## Opzioni di aggiornamento e migrazione

Se ti trovi in una versione che si avvicina o che è scaduta le date di fine del supporto, puoi intervenire ora. Il mantenimento di una versione non supportata espone il tuo archivio al rischio di vulnerabilità di sicurezza, problemi di conformità e perdita del supporto. Per passare a una versione supportata, Adobe fornisce i seguenti percorsi.

### Percorso consigliato: migrazione ad Adobe Commerce as a Cloud Service (ACCS)

[!DNL Adobe Commerce as a Cloud Service] è la piattaforma di e-commerce ospitato di nuova generazione di Adobe e la destinazione a lungo termine consigliata da Adobe per tutti i clienti Adobe Commerce on Cloud.

- Adobe gestisce automaticamente tutte le infrastrutture, le patch e gli aggiornamenti.
- L&#39;azienda utilizza sempre un&#39;infrastruttura supportata e conforme alle normative, in modo che la situazione di fine del ciclo di vita non si ripeta.
- Puoi accedere alle funzionalità più recenti di Adobe: merchandising basato sull’intelligenza artificiale, architettura della vetrina componibile e integrazioni native di Adobe Experience Cloud.
- Vengono eliminati i cicli di aggiornamento ricorrenti.

Contatta il team del tuo account Adobe per iniziare una valutazione della migrazione. Per una panoramica del prodotto, consulta [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/it/docs/commerce/cloud-service/overview).

### Percorso alternativo: aggiornamento a una versione supportata di Adobe Commerce su cloud o on-premise

Se non riesci a eseguire immediatamente la migrazione a [!DNL Adobe Commerce as a Cloud Service], puoi eseguire l&#39;aggiornamento all&#39;ultima versione di Adobe Commerce on-premise o su cloud attualmente supportata. In questo modo si passa a uno stack di infrastruttura moderno completamente supportato, preservando al contempo il modello di distribuzione PaaS esistente.

Si noti che questo percorso non elimina gli obblighi di aggiornamento futuri. I clienti su PaaS devono continuare l’aggiornamento man mano che le linee di rilascio raggiungono le date di applicazione dell’aggiornamento della versione.
