---
title: Regole sul ciclo di vita del software
description: Scopri le date chiave per la fine del supporto software per le versioni di Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3e7cef954a2be506c6f72e704710d16ed1d9b7a3
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 2%

---


# criteri del ciclo di vita Adobe Commerce

Per semplificare la politica sul ciclo di vita di Adobe Commerce e supportare le esigenze mission-critical dei clienti, Adobe offre una finestra di assistenza di tre anni dalla data di disponibilità generale (GA) per ogni versione e rilascia correzioni di qualità durante questo periodo. Per le date e i dettagli sulla fine del supporto software per ogni versione, vedere la tabella [Fine del supporto software](#end-of-software-support).

Durante il periodo di assistenza triennale, il cliente ha accesso a:

- **Correzioni di qualità**-I clienti possono accedere alle correzioni di qualità contattando [il supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o tramite [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) self-service. La tabella seguente descrive le date di fine del supporto software per le righe della versione di Adobe Commerce.

- **Correzioni di sicurezza**-Adobe fornisce correzioni di sicurezza tramite patch di sicurezza cumulative e [file di patch di sicurezza isolati](versioning-policy.md#isolated-security-fixes) non cumulativi per il periodo di supporto di tre anni.

- **Hotfix**-Per problemi critici di sicurezza, ad esempio vulnerabilità zero giorni, Adobe fornisce [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) per tutti i clienti che utilizzano una versione supportata, anche se non sono inclusi nell&#39;ultima versione della patch o della patch di sicurezza. Tieni presente che un hotfix non è completo e non risolve tutti i problemi di sicurezza che verrebbero risolti con l’aggiornamento alla versione più recente.

Adobe non fornisce correzioni di sicurezza e di qualità per servizi di terze parti e dipendenze software (come PHP e MySQL) che possono raggiungere la fine del ciclo di vita mentre i clienti sono nel periodo di supporto di tre anni o esteso per Adobe Commerce. Consulta [requisiti di sistema](../installation/system-requirements.md) per un elenco completo delle tecnologie di terze parti testate e supportate.

## Supporto esteso

Adobe incoraggia i clienti ad effettuare l’aggiornamento il prima possibile. Tuttavia, per fornire maggiore flessibilità nell’allineamento con i piani di aggiornamento e le esigenze aziendali, nelle versioni 2.4.6 Adobe offre ai clienti Adobe Commerce un’estensione del supporto di un anno senza costi aggiuntivi. L’estensione per il supporto include patch di qualità e sicurezza per l’applicazione principale per un massimo di un anno. Il supporto esteso per le versioni Adobe Commerce 2.4.4 e 2.4.5 termina ad aprile e agosto 2026 come pianificato.

>[!NOTE]
>
>Il supporto esteso è disponibile solo per i clienti Adobe Commerce. Non è disponibile per la base di codice di Magento Open Source.

## Fine del supporto software

| Versione | Disponibilità generale | Fine del supporto regolare<sup>1</sup> | Fine del supporto esteso |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 8 aprile 2025 | 31 maggio 2028 | Da definire |
| Adobe Commerce 2.4.7 | 9 aprile 2024 | 31 maggio 2027 | Da definire |
| Adobe Commerce 2.4.6 | 14 marzo 2023 | 11 agosto 2026 | 30 agosto 2027 |
| Adobe Commerce 2.4.5 | 9 agosto 2022 | 12 agosto 2025 | 11 agosto 2026 |
| Adobe Commerce 2.4.4 | 12 aprile 2022 | 12 aprile 2025 | 14 aprile 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Se sei un cliente di Adobe Commerce, puoi continuare a ricevere correzioni di sicurezza e qualità per un altro anno durante il periodo di supporto esteso.
>- Consulta [Criteri del ciclo di vita software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

## Provisioning di ulteriori correzioni di sicurezza per Adobe Commerce 2.4.4 e 2.4.5

Come eccezione una tantum, Adobe fornisce un periodo esteso di provisioning delle correzioni di sicurezza per Adobe Commerce versioni 2.4.4 e 2.4.5 per dare ai clienti più tempo per migrare ad Adobe Commerce as a Cloud Service o effettuare l’aggiornamento a una linea di rilascio supportata.

Durante questo periodo di provisioning delle correzioni di sicurezza, tieni presente quanto segue:

- **Solo file patch di sicurezza isolato**-Per queste versioni verrà rilasciato un file patch di sicurezza isolato in base alla pianificazione della versione. Durante questo periodo non verranno fornite patch di sicurezza (nessuna nuova versione -p).

  Per applicare un file di patch di sicurezza isolato, i clienti devono utilizzare l’ultima versione della patch di sicurezza (l’ultima versione -p) per la propria riga di rilascio supportata, in quanto le correzioni di sicurezza isolate vengono testate esclusivamente in base a tale versione.

- **Nessuna correzione di qualità o assistenza tecnica**-Durante questo periodo non verranno fornite correzioni di bug, aggiornamenti di qualità ([Strumento Patch di qualità](../tools/quality-patches-tool/usage.md)) o assistenza tecnica ([Supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) per le versioni 2.4.4 o 2.4.5.

- **La conformità PCI non è garantita:**-Poiché le versioni 2.4.4 e 2.4.5 utilizzano PHP che hanno raggiunto la fine del ciclo di vita, la conformità PCI non può essere garantita per gli esercenti su tali versioni. Continuare a eseguire queste versioni può mettere a rischio la conformità PCI.

Per mantenere una copertura di sicurezza completa e garantire la conformità PCI, i clienti devono effettuare l&#39;aggiornamento a una versione attualmente supportata di Adobe Commerce il prima possibile o migrare a [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview).

| Versione | Disponibilità generale | Fine del supporto esteso | Fine del provisioning delle correzioni di sicurezza |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 9 agosto 2022 | 11 agosto 2026 | Maggio 2027 |
| Adobe Commerce 2.4.4 | 12 aprile 2022 | 14 aprile 2026 | Maggio 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>Ulteriori correzioni di sicurezza sono disponibili solo per i clienti Adobe Commerce e non per la base di codice Magento Open Source.


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
    <td>2.4.4.</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5.</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6.</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7.</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8.</td>
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
   <td>Supporto regolare</td>
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
