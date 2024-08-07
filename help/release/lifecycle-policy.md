---
title: Regole sul ciclo di vita del software
description: Scopri le date chiave per la fine del supporto software per le versioni di Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 7df5edf2acba706fb01f58cc3749c4a2bf136fc5
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 5%

---


# criteri del ciclo di vita Adobe Commerce

Per Adobe Commerce 2.4.4 e versioni successive:

- Per semplificare la politica sul ciclo di vita di Adobe Commerce e supportare le esigenze mission-critical dei clienti, Adobe ha esteso la finestra di supporto a tre anni dalla data di disponibilità generale (GA) per Adobe Commerce 2.4.4 e versioni successive. Adobe fornisce correzioni di qualità alla versione 2.4.4 e alle versioni successive per un periodo di supporto di tre anni. I clienti possono accedere alle correzioni di qualità contattando il [Supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) o tramite il self-service [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) se la loro versione è ancora idonea per il supporto di qualità. Consultare la tabella seguente per le date di fine del supporto software per le righe sulla versione di Adobe Commerce.

- Adobe fornisce correzioni di sicurezza attraverso una versione di patch di sicurezza per il periodo di supporto di tre anni.

- Per problemi critici di sicurezza, come vulnerabilità a zero giorni, Adobe fornisce [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) per tutti i clienti che usano una versione supportata, anche se non sono nell&#39;ultima versione della patch o della patch di sicurezza. È importante notare che un hotfix non è onnicomprensivo e non risolve tutti i problemi di sicurezza che verrebbero risolti con l’aggiornamento alla versione più recente.

- Adobe non fornisce correzioni di sicurezza e di qualità per servizi di terze parti e dipendenze software (come PHP e MySQL) che possono terminare mentre i clienti sono in servizio per il periodo di supporto di tre anni per Adobe Commerce. Consulta [requisiti di sistema](../installation/system-requirements.md) per un elenco completo delle tecnologie di terze parti testate e supportate.

- Adobe offre compatibilità con servizi di terze parti e dipendenze dal software, mentre i clienti rientrano nel periodo di supporto di tre anni per Adobe Commerce nell’ambito delle versioni delle patch per la sola sicurezza, ma solo quando è possibile farlo senza introdurre modifiche non compatibili con le versioni precedenti.

## Fine del supporto software

| Versione | Disponibilità generale | Fine del supporto software<sup>1</sup> | Versione PHP dipendente | Versione MariaDB dipendente |
|----------------------|----------------------|-------------------------------------|-----------------------|------------------------------|
| Adobe Commerce 2.4.7 | 9 aprile 2024 | 9 aprile 2027 | 8.2 e 8.3 | 10,6 |
| Adobe Commerce 2.4.6 | 14 marzo 2023 | 14 marzo 2026 | 8.1 e 8.2 | 10,6 |
| Adobe Commerce 2.4.5 | 9 agosto 2022 | 9 agosto 2025 | 8,1 | 10,5<sup>2</sup> |
| Adobe Commerce 2.4.4 | 12 aprile 2022 | 24 aprile 2025 | 8,1 | 10,5<sup>3</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> La fine del supporto software include sia la fine delle correzioni di qualità che la fine delle correzioni di sicurezza.
>- <sup>2</sup> a partire dalla patch di sicurezza 2.4.5-p8.
>- <sup>3</sup> a partire dalla patch di sicurezza 2.4.4-p9.
>- Consulta [Criteri del ciclo di vita software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="2"></th>
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
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5.</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6.</td>
    <td colspan="4"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
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
   <td style="background-color:#67ac68;">Supportato</td>
   <td>Patch di sicurezza e qualità per Adobe Commerce</td>
  </tr>
  <!-- <tr>
   <td style="background-color:#cd3c3c;">End of software support</td>
   <td>Version that has reached end of software support.</td>
  </tr>
 </tbody> -->
</table>
