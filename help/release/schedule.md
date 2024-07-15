---
title: Pianificazione della versione
description: Scopri quando Adobe intende annunciare il rilascio di nuove funzioni per Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# Pianificazione della versione

Adobe cerca continuamente di trovare il giusto equilibrio tra l&#39;esigenza di rendere gli aggiornamenti dei prodotti semplici e prevedibili e la distribuzione più rapida di miglioramenti e nuove funzionalità ai primi utenti (consulta [criteri di controllo delle versioni](versioning-policy.md)). Lo scopo di questo programma è quello di fornire le date in cui Adobe pianifica di annunciare il rilascio di nuove funzionalità sostanziali. Queste caratteristiche possono variare nel corso dell’anno. Tuttavia, Adobe rilascia regolarmente e in modo continuo miglioramenti per strumenti di estensibilità, infrastrutture e prodotti (servizi) SaaS tra le date specificate in questa pagina.

Adobe rilascia [patch](versioning-policy.md#patch-release) per ogni riga di rilascio supportata dell&#39;applicazione Adobe Commerce PHP di base. Le versioni patch offrono l’opportunità di aggiornare la base di codice principale per mantenere la piattaforma sicura, affidabile e performante. Le funzionalità sono indipendenti dal codebase principale e sono disponibili tramite [modulo esterno, estensione, strumento o servizio Web](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>A partire dal 2024, Adobe non fornisce più l’accesso &quot;pre-release&quot; alle patch. Per la versione 2.4.7 e successive, invece, i clienti Adobe Commerce possono utilizzare [versioni beta](beta.md) per accedere al codice di disponibilità pre-generale a scopo di test e sviluppo.

Nella tabella seguente sono riportate le date dei rilasci pianificati (le date sono soggette a modifiche):

<table>
<thead>
  <tr>
    <th>Disponibilità generale</th>
    <th>Funzioni</th>
    <th>PHP Core</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong>Legenda</strong>
         <ul>
           <li><strong><img alt="Icona della funzione B2B" src="../assets/icons/enterprise.svg"></img> B2B</strong>: nuove funzionalità, miglioramenti e correzioni di bug per l'estensione B2B per Adobe Commerce. Per informazioni dettagliate sulle versioni dell'estensione B2B, consulta le <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">note sulla versione B2B</a>.</li>
            <li><strong><img alt="Icona della funzione di estensibilità" src="../assets/icons/brackets.svg"></img> Estensibilità</strong>: nuovi strumenti e servizi per sviluppatori per l'estensibilità fuori processo forniti indipendentemente dalle versioni delle patch. Ad esempio, l’SDK dell’interfaccia di amministrazione, gli eventi di Adobe I/O per Commerce e API Mesh.</li>
            <li>Infrastruttura <strong><img alt="Icona della funzione di infrastruttura" src="../assets/icons/servers.svg"></img></strong>: nuove funzionalità e miglioramenti apportati ad Adobe Commerce sull'infrastruttura cloud e ai pacchetti Cloud Tools Suite per Commerce, progettati per distribuire e gestire le installazioni e gli aggiornamenti di Adobe Commerce sulla piattaforma cloud.</li>
            <li><strong><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> patch</strong>: aggiornamenti all'applicazione principale Adobe Commerce PHP che includono correzioni di sicurezza, conformità, prestazioni e qualità ad alta priorità.</li>
            <li><strong><img alt="Icona della funzione Servizi" src="../assets/icons/feature.svg"></img> Servizi</strong>: nuove funzionalità SaaS distribuite in modo indipendente dalle versioni patch. Ad esempio Catalog Service, Live Search e Product Recommendations.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>13 febbraio 2024</td>
    <td><img alt="Icona della funzione di estensibilità" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Estensibilità</a><br><img alt="Icona della funzione di infrastruttura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruttura</a><br><img alt="Icona della funzione Servizi" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servizi</a></td>
    <td><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patch di sicurezza</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>12 marzo 2024</td>
    <td>—</td>
    <td><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">patch Beta</a>: 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>9 aprile 2024</td>
    <td><img alt="Icona della funzione di estensibilità" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Estensibilità</a><br><img alt="Icona della funzione di infrastruttura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruttura</a><br><img alt="Icona della funzione Servizi" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servizi</a></td>
    <td><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>Miglioramenti delle prestazioni</li><li>Miglioramenti della qualità</li><li>Miglioramenti di sicurezza</li><li>Aggiornamenti delle dipendenze di terze parti</li></ul><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patch di sicurezza</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>11 giugno 2024</td>
    <td><img alt="Icona della funzione di estensibilità" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Estensibilità</a><br><img alt="Icona della funzione di infrastruttura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruttura</a><br><img alt="Icona della funzione Servizi" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servizi</a></td>
    <td><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patch di sicurezza</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>13 agosto 2024</td>
    <td><img alt="Icona della funzione di estensibilità" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Estensibilità</a><br><img alt="Icona della funzione di infrastruttura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruttura</a><br><img alt="Icona della funzione Servizi" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servizi</a></td>
    <td><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Patch di sicurezza</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>8 ottobre 2024</td>
    <td><img alt="Icona della funzione di estensibilità" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Estensibilità</a><br><img alt="Icona della funzione di infrastruttura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infrastruttura</a><br><img alt="Icona della funzione Servizi" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servizi</a></td>
    <td><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">patch di Beta</a>: 2.4.8-beta1<br><img alt="Icona rilascio patch" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">patch di sicurezza</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>
