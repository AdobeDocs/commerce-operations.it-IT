---
title: Pianificazione rilascio patch
description: Scopri quando Adobe prevede di annunciare il rilascio di nuove patch e correzioni di sicurezza per Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 1c32f1e506cd3caefacbb250821da087e34c34ea
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Pianificazione rilascio patch

Adobe cerca continuamente di trovare il giusto equilibrio tra la semplificazione e la prevedibilità degli aggiornamenti dei prodotti e la velocizzazione della distribuzione di miglioramenti agli utenti che li hanno adottati per primi (consulta [criteri di controllo delle versioni](versioning-policy.md)).

Lo scopo di questa pianificazione è quello di fornire le date in cui Adobe pianifica di annunciare il rilascio di [patch](versioning-policy.md#patch-release) per ogni riga di rilascio supportata dell&#39;applicazione Adobe Commerce PHP di base. Le versioni patch offrono l’opportunità di aggiornare la base di codice principale per mantenere la piattaforma sicura, affidabile e performante.

>[!NOTE]
>
>Per ulteriori informazioni sulle nuove funzioni, sull&#39;infrastruttura cloud e sulle versioni di estensibilità, consulta la [documentazione sulla versione di Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Oltre alle patch di qualità, sicurezza e versione beta pianificate elencate in questa pagina, Adobe fornisce l&#39;accesso a [singole patch](versioning-policy.md#individual-patch) tramite lo strumento [Patch di qualità](../tools/quality-patches-tool/usage.md). Lo strumento consente di applicare, ripristinare e visualizzare informazioni generali su tutte le singole patch disponibili per la versione installata di Adobe Commerce.

Adobe Commerce segue una pianificazione mensile del rilascio delle patch con la seguente strategia:

- **Correzioni di sicurezza isolate**: [correzioni di sicurezza](versioning-policy.md#isolated-patch) singole e non cumulative possono essere rilasciate mensilmente e includere correzioni di sicurezza per tutte le [righe di rilascio supportate](lifecycle-policy.md) (include supporto regolare ed esteso).

- **Patch di sicurezza**—Almeno, [le patch di sicurezza](versioning-policy.md#security-patch-release) vengono rilasciate ogni anno (maggio) per tutte le [righe di rilascio supportate](lifecycle-policy.md). Queste patch includono tutte le correzioni di sicurezza isolate rilasciate in precedenza. Se necessario, Adobe potrebbe rilasciare patch di sicurezza aggiuntive a novembre, ma ciò non è garantito.

- **Patch**—Una [patch](versioning-policy.md#patch-release) completa per la riga di rilascio Adobe Commerce 2.4.x LTS (periodo di supporto di 3 anni) viene rilasciata annualmente (maggio).

- **patch Beta**—Due [patch beta](versioning-policy.md#beta-patch-release) per la riga di rilascio Adobe Commerce 2.4.x LTS vengono rilasciate due volte all&#39;anno (marzo e novembre).

Per ulteriori informazioni, vedere l&#39;immagine seguente:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Calendario della versione di Adobe Commerce 2026](../assets/release/release-calendar.png)


## Canali di notifica delle versioni

Adobe notifica ai clienti le nuove versioni delle patch tramite i seguenti canali:

- [Bollettini sulla sicurezza e avvisi di Adobe](https://helpx.adobe.com/security/security-bulletin.html#magento)
- E-mail
- Avvisi interni al prodotto

>[!NOTE]
>
> Per le date di rilascio di ogni versione secondaria, patch e di sicurezza e per le date di fine del supporto regolare, vedere [Versioni rilasciate](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).
