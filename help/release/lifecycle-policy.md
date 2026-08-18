---
title: Regole sul ciclo di vita del software
description: Scopri le date chiave per la fine del supporto software per le versioni di Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
nudge: true
last-update: 2026-08-17T00:00:00Z
source-git-commit: 7ba189685721799de047bc8d0e7108fa512f7120
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 1%

---


# criteri del ciclo di vita Adobe Commerce

Per semplificare la politica sul ciclo di vita di Adobe Commerce e supportare le esigenze mission-critical dei clienti, Adobe offre una finestra di supporto standard di tre anni dalla data di disponibilità generale (GA) per ogni versione e rilascia correzioni di qualità durante questo periodo. Per le date e i dettagli sulla fine del supporto software per ogni versione, vedere la tabella [Date di fine supporto](#end-of-support-dates).

Adobe non fornisce correzioni di sicurezza e di qualità per servizi di terze parti e dipendenze software (come PHP e MySQL) che possono raggiungere la fine del ciclo di vita mentre i clienti sono nel periodo di supporto di tre anni o esteso per Adobe Commerce. Consulta [requisiti di sistema](../installation/system-requirements.md) per un elenco completo delle tecnologie di terze parti testate e supportate.

## Supporto standard

Il periodo di supporto standard di tre anni dalla data di disponibilità generale (General Availability, GA). Il supporto standard include correzioni di qualità, patch di sicurezza e supporto Adobe Commerce on-call completo.

- **Correzioni di qualità** - I clienti possono accedere alle correzioni di qualità contattando [il supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o tramite [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) self-service.

- **Correzioni di sicurezza** - Adobe fornisce correzioni di sicurezza tramite patch di sicurezza cumulative e [file di patch di sicurezza isolati](versioning-policy.md#isolated-security-patch-file) non cumulativi per il periodo di supporto di tre anni.

- **Hotfix**: per problemi critici di sicurezza, ad esempio vulnerabilità a zero giorni, Adobe fornisce [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) per tutti i clienti che utilizzano una versione supportata, anche se non si trovano nell&#39;ultima versione della patch o della patch di sicurezza. Tieni presente che un hotfix non è completo e non risolve tutti i problemi di sicurezza che verrebbero risolti con l’aggiornamento alla versione più recente.

## Supporto esteso

Adobe incoraggia i clienti ad effettuare l’aggiornamento il prima possibile. Tuttavia, per fornire maggiore flessibilità nell’allineamento con i piani di aggiornamento e le esigenze aziendali, nelle versioni 2.4.6 e 2.4.7 Adobe offre ai clienti Adobe Commerce un anno di supporto aggiuntivo senza costi aggiuntivi. L’estensione per il supporto include patch di qualità e sicurezza per l’applicazione core. Il supporto esteso per le versioni Adobe Commerce 2.4.4 e 2.4.5 termina ad aprile e agosto 2026 come pianificato.

>[!NOTE]
>
>Adobe sta introducendo una policy di aggiornamento della versione applicata per Adobe Commerce su Cloud per aiutare ogni cliente a rimanere su una piattaforma sicura e supportata. A partire dal **1 giugno 2027**, Adobe non manterrà più gli ambienti Cloud che eseguono versioni di Commerce non supportate e sarà costretta a intraprendere azioni appropriate per garantire la sicurezza della piattaforma Adobe Commerce e dei suoi clienti. Ciò include la sospensione del traffico verso l&#39;infrastruttura interessata. Di conseguenza, la vetrina dell’e-commerce sarà offline. Se esegui su Cloud, devi passare a una versione di Adobe Commerce supportata o eseguire la migrazione a [!DNL Adobe Commerce as a Cloud Service] prima della data di [fine del supporto esteso](lifecycle-policy.md#end-of-support-dates) pubblicata per la riga di rilascio. Se utilizzi le versioni da 2.4.4 a 2.4.9, consulta l&#39;[Avviso sulla sicurezza e la conformità](security-enforcement-policy.md) per le azioni e le scadenze specifiche applicabili al tuo ambiente.

## Periodo transitorio solo titolo

Un periodo transitorio una tantum e limitato nel tempo disponibile solo per le versioni 2.4.4, 2.4.5 e 2.4.6 il cui supporto esteso è terminato nel 2025 o nel 2026. Il periodo transitorio riservato alla sicurezza fornisce solo correzioni di sicurezza isolate limitate (nessuna correzione di qualità).

>[!IMPORTANT]
>
>Il periodo transitorio riservato ai soli titoli costituisce un&#39;eccezione una tantum. Non verrà esteso oltre le date di pubblicazione. Considera il periodo di sola sicurezza come tempo di migrazione e non come livello di supporto a lungo termine. Contatta il team del tuo account per aiutarti a creare un piano di migrazione.

## Date di fine del supporto

La tabella seguente mostra l’intero ciclo di vita di ogni versione di Adobe Commerce, comprese le date di imposizione dell’aggiornamento della nuova versione per gli ambienti Adobe Commerce on Cloud.

{{$include /help/_includes/templated/release/end-of-support-dates.md}}

## Timeline del supporto

Le mappe della timeline di supporto supportano i periodi trimestre per trimestre per ogni riga di rilascio di Adobe Commerce. Utilizzare le tabelle fornite in precedenza in questo argomento per le date di fine esatte.

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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="2"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
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
   <td>Supporto standard</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Supporto esteso</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Correzioni di sicurezza estese</td>
  </tr>
 </tbody>
</table>

## Dipendenze della piattaforma

L’utilizzo di una versione di Commerce supportata richiede anche dipendenze di piattaforma supportate. Adobe non fornisce correzioni di sicurezza e di qualità per servizi di terze parti e dipendenze software, come MariaDB, OpenSearch, Redis, Valkey, RabbitMQ e altri, che possono raggiungere la fine del ciclo di vita durante il periodo di supporto di tre anni o esteso per Adobe Commerce. Per informazioni dettagliate, vedere [Modello operativo e di sicurezza con responsabilità condivisa](../security-and-compliance/shared-responsibility.md).

L’utente è responsabile della gestione di tutte le dipendenze di terze parti e dei servizi di piattaforma sulle versioni attivamente supportate. Consulta [Requisiti di sistema](../installation/system-requirements.md) per l&#39;elenco completo delle tecnologie di terze parti testate e supportate.

>[!IMPORTANT]
>
>L’esecuzione di versioni di dipendenza non supportate può causare una vulnerabilità di sicurezza nell’istanza Cloud che Adobe non è in grado di risolvere. In questi casi, Adobe sarà costretta ad adottare le misure appropriate per mantenere la sicurezza della piattaforma Adobe Commerce e dei suoi clienti. Ciò include la sospensione del traffico verso l&#39;infrastruttura interessata. Di conseguenza, la vetrina dell’e-commerce sarà offline.
>
>Se un ambiente continua a non essere conforme dopo la sospensione del traffico, Adobe può interrompere i servizi cloud, avviando il processo di disattivazione. Con la disattivazione, tutti i dati e le risorse all’interno dell’ambiente di e-commerce ospitato, incluse tutte le istanze, gli ambienti e i rami, verranno eliminati definitivamente e non potranno essere ripristinati. Per informazioni sulla pianificazione di questi aggiornamenti e sul supporto disponibile durante l&#39;intero processo, vedere le [azioni necessarie e scadenze per proteggere gli ambienti Commerce](security-enforcement-policy.md).

## Fine del ciclo di vita PHP e conformità PCI

È tua responsabilità monitorare lo stato di supporto delle versioni PHP utilizzate negli ambienti.

Le seguenti versioni PHP utilizzate dalle precedenti linee di rilascio di Commerce hanno raggiunto o raggiungeranno la fine del ciclo di vita, il che ha implicazioni dirette per la conformità PCI.

| Versione PHP | Data di fine del ciclo di vita | Versioni Commerce interessate | Impatto sulla conformità PCI |
| ------------- | ------------------ | ---------------------------- | ------------------------ |
| PHP 8.1 | 31 dicembre 2025 | 2.4.4, 2.4.5 e 2.4.6 (dove si utilizza PHP 8.1) | Conformità PCI a rischio: l&#39;esecuzione di PHP 8.1 oltre la data di fine del ciclo di vita significa che le vulnerabilità di sicurezza in PHP potrebbero non ricevere correzioni, il che mette a rischio la conformità PCI. Valuta lo stato di conformità e assegna priorità all&#39;aggiornamento. |
| PHP 8.2 | 31 dicembre 2026 | 2.4.6 (se viene utilizzato PHP 8.2) | Conformità PCI a rischio a partire dalla fine del 2026 — pianificare l’aggiornamento o la migrazione prima della fine del 2026 per mantenere la conformità PCI. |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>**Avviso di conformità PCI:** la conformità PCI è responsabilità dell&#39;esercente valutare. Adobe consiglia vivamente ai commercianti delle versioni interessate di consultare un valutatore della sicurezza qualificato e di privilegiare il passaggio a una versione di Commerce supportata e a una versione PHP supportata il prima possibile. Per le timeline di supporto PHP, vedere [Versioni supportate PHP](https://www.php.net/supported-versions.php) e [fine del ciclo di vita PHP](https://www.php.net/eol.php).

## Opzioni di aggiornamento e migrazione

Se ti trovi in una versione che si avvicina o che è scaduta le date di fine del supporto, puoi intervenire ora. Il mantenimento di una versione non supportata espone il tuo archivio al rischio di vulnerabilità di sicurezza, problemi di conformità e perdita del supporto. Per passare a una versione supportata, Adobe fornisce i seguenti percorsi.

### Percorso consigliato: migrazione ad Adobe Commerce as a Cloud Service

[!DNL Adobe Commerce as a Cloud Service] è la piattaforma di e-commerce ospitato di nuova generazione di Adobe e la destinazione a lungo termine consigliata da Adobe per tutti i clienti Adobe Commerce on Cloud.

- Adobe gestisce automaticamente tutte le infrastrutture, le patch e gli aggiornamenti.
- L&#39;azienda utilizza sempre un&#39;infrastruttura supportata e conforme alle normative, in modo che la situazione di fine del ciclo di vita non si ripeta.
- Puoi accedere alle funzionalità più recenti di Adobe: merchandising basato sull’intelligenza artificiale, architettura della vetrina componibile e integrazioni native di Adobe Experience Cloud.
- Vengono eliminati i cicli di aggiornamento ricorrenti.

Contatta il team del tuo account Adobe per iniziare una valutazione della migrazione. Per una panoramica del prodotto, consulta [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview).

### Percorso alternativo: aggiornamento a una versione supportata di Adobe Commerce su cloud o on-premise

Se non riesci a eseguire immediatamente la migrazione a [!DNL Adobe Commerce as a Cloud Service], puoi eseguire l&#39;aggiornamento all&#39;ultima versione di Adobe Commerce on Cloud attualmente supportata. In questo modo puoi passare a uno stack di infrastruttura moderno completamente supportato, preservando al contempo il modello di distribuzione Commerce on Cloud esistente.

Si noti che questo percorso non elimina gli obblighi di aggiornamento futuri. I clienti con implementazioni di Adobe Commerce on Cloud devono continuare l’aggiornamento man mano che le righe della versione raggiungono le date di applicazione dell’aggiornamento della versione.
