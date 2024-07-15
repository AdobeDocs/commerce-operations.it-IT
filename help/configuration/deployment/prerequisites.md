---
title: Prerequisiti per la distribuzione
description: Consulta un elenco di prerequisiti per la distribuzione di Commerce in un sistema di sviluppo, build o produzione.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Prerequisiti per i sistemi di sviluppo, generazione e produzione

Le autorizzazioni e la proprietà dei file devono essere coerenti tra i sistemi di sviluppo, generazione e produzione. Per eseguire questa operazione, è necessario:

- Tutti i seguenti elementi:

   - Impostare lo stesso nome utente proprietario del file system su tutti i sistemi
   - Assicurati che il server web funzioni come lo stesso utente su tutti i sistemi
   - Verificare che il proprietario del file system si trovi nel gruppo di server Web su tutti i sistemi

- Modificare le autorizzazioni e la proprietà del file system di Commerce in base alle esigenze utilizzando le seguenti linee guida:

   - Sviluppo e compilazione: [Impostare le autorizzazioni e la proprietà di preinstallazione (due utenti)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produzione: [Proprietà e autorizzazioni di Commerce in sviluppo e produzione](file-system-permissions.md)

>[!INFO]
>
>Se si sceglie questo approccio, è necessario impostare le autorizzazioni e la proprietà del file system ogni volta che si richiama il codice dal sistema di build (se il proprietario del file system o l&#39;utente del server Web sono diversi nel sistema di build).
