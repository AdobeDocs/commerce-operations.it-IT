---
title: Politica del ciclo di vita del software
description: Scopri le date chiave per la fine del supporto software per le versioni di Adobe Commerce.
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Criterio sul ciclo di vita di Adobe Commerce

Per Adobe Commerce 2.4 e versioni successive:

- Per semplificare meglio la nostra politica del ciclo di vita, Adobe fornisce correzioni di qualità alla linea di rilascio 2.4 fino alla data di fine del supporto della versione PHP su cui si basa. Un cliente può accedere alle correzioni di qualità contattando [Supporto Adobe Commerce](https://developer.adobe.com/commerce/contributor/community/support/) o attraverso il self-service [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;} se la loro versione è ancora idonea al supporto qualità. Fai riferimento alla tabella seguente per le date di fine del supporto software per le righe di rilascio di Adobe Commerce.

- Adobe fornisce correzioni di sicurezza solo tramite la patch o la patch di sicurezza più recente, anche se la versione di un cliente è ancora idonea al supporto qualità. A differenza delle correzioni di qualità, le correzioni di sicurezza non possono essere sottoposte a backporting alle versioni minori precedenti o alle versioni precedenti delle patch nelle versioni secondarie supportate.

- Per problemi critici di sicurezza, come le vulnerabilità a zero giorni, Adobe fornisce [hotfix](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) per tutti i clienti di una versione supportata, anche se non si trovano nella patch o nella patch di sicurezza più recente. È importante notare che un hotfix non è un catch-all e non risolve tutti i problemi di sicurezza che verrebbero risolti aggiornando alla versione più recente.

## Fine del supporto software

| Versione | Data di rilascio | Fine del supporto software<sup>1</sup> | Versione PHP dipendente |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 28 novembre 2018 | 8 settembre 2022<sup>2</sup> | PHP 7.3 e 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 28 luglio 2020 | 28 novembre 2022 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 12 aprile 2022 | 25 novembre 2024 | PHP 8.1 |

<sup>1 Il supporto di fine software include sia la fine delle correzioni di qualità che la fine delle correzioni di sicurezza.</sup><br>
<sup>2 La data di fine del supporto software per la versione 2.3 è stata estesa all’8 settembre 2022 per dare ai clienti più tempo per effettuare l’aggiornamento alla versione 2.4.4 che sarà generalmente disponibile l’8 marzo 2022.</sup><br>
<sup>3 2.3.0-2.3.6 dipendono da PHP 7.3; 2.3.7 dipende da PHP 7.4.</sup>

>[!NOTE]
>
>Vedi [Criterio del ciclo di vita del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7.4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">nov</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8.1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">mar</td>
    <td rowspan="2" style="background-color:#cd3c3c;">nov</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">Ago</td>
  </tr>
</tbody>
</table>

## Chiave

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Supportato</td>
   <td>Versione completamente testata da Adobe e supportata.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">Fine del supporto software</td>
   <td>Versione che ha raggiunto la fine del supporto software.</td>
  </tr>
 </tbody>
</table>
