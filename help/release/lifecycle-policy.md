---
title: Regole sul ciclo di vita del software
description: Scopri le date chiave per la fine del supporto software per le versioni di Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: ce7c322c5cf979a992e6f929c3105daf86d4aa49
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---


# criteri del ciclo di vita Adobe Commerce

Per Adobe Commerce 2.4.4 e versioni successive:

- Per semplificare la politica sul ciclo di vita di Adobe Commerce e supportare le esigenze mission-critical dei clienti, Adobe ha esteso la finestra di supporto a tre anni dalla data di disponibilità generale (GA) per Adobe Commerce 2.4.4 e versioni successive. Adobe fornisce correzioni di qualità alla versione 2.4.4 e alle versioni successive per un periodo di supporto di tre anni. I clienti possono accedere alle correzioni di qualità contattando il [Supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o tramite il self-service [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) se la loro versione è ancora idonea per il supporto di qualità. La tabella seguente descrive le date di fine del supporto software per le righe della versione di Adobe Commerce.

- Adobe fornisce correzioni di sicurezza attraverso una versione di patch di sicurezza per il periodo di supporto di tre anni.

- Per problemi critici di sicurezza, come vulnerabilità zero-day, Adobe fornisce [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) per tutti i clienti che usano una versione supportata, anche se non sono nell&#39;ultima versione della patch o della patch di sicurezza. Tieni presente che un hotfix non è completo e non risolve tutti i problemi di sicurezza che verrebbero risolti con l’aggiornamento alla versione più recente.

- Adobe non fornisce correzioni di sicurezza e di qualità per servizi di terze parti e dipendenze software (come PHP e MySQL) che potrebbero terminare mentre i clienti sono al periodo di supporto di tre anni per Adobe Commerce. Consulta [requisiti di sistema](../installation/system-requirements.md) per un elenco completo delle tecnologie di terze parti testate e supportate.

- Adobe offre compatibilità con servizi di terze parti e dipendenze dal software, mentre i clienti rientrano nel periodo di supporto di tre anni per Adobe Commerce nell’ambito delle versioni delle patch per la sola sicurezza, ma solo quando è possibile farlo senza introdurre modifiche non compatibili con le versioni precedenti.

## Supporto esteso

Adobe incoraggia i clienti ad effettuare l’aggiornamento il prima possibile. Tuttavia, per fornire maggiore flessibilità nell’allineamento con i piani di aggiornamento e le esigenze aziendali, nelle versioni 2.4.4 e 2.4.5 Adobe offre ai clienti Adobe Commerce un’estensione del supporto di un anno senza costi aggiuntivi. L’estensione per il supporto include patch di qualità e sicurezza per l’applicazione principale per un massimo di un anno.

>[!NOTE]
>
>Il supporto esteso è disponibile solo per i clienti Adobe Commerce. Non è disponibile per la base di codice del Magento Open Source.

## Fine del supporto software

| Versione | Disponibilità generale | Fine del supporto regolare<sup>1</sup> | Fine del supporto esteso | Versione PHP dipendente | Versione MariaDB dipendente |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 aprile 2024 | 9 aprile 2027 | N/D | 8.2 e 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 marzo 2023 | 11 agosto 2026<sup>2</sup> | N/D | 8.1 e 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 agosto 2022 | 9 agosto 2025 | 11 agosto 2026 | 8,1 | 10,6<sup>3</sup> |
| Adobe Commerce 2.4.4 | 12 aprile 2022 | 24 aprile 2025 | 14 aprile 2026 | 8,1 | 10,6<sup>4</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> La fine del supporto software include sia la fine delle correzioni di qualità che la fine delle correzioni di sicurezza.
>- <sup>2</sup> Aggiornato per allinearlo alla fine del supporto esteso per la versione 2.4.5.
>- <sup>3</sup> a partire dalla patch di sicurezza 2.4.5-p11.
>- <sup>4</sup> a partire dalla patch di sicurezza 2.4.4-p12.
>- Consulta [Criteri del ciclo di vita software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

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
  </tr>
  <tr>
    <td>2.4.4.</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.5.</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.6.</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="8"></td>
  </tr>
  <tr>
    <td>2.4.7.</td>
    <td colspan="9"></td>
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
 </tbody>
</table>
