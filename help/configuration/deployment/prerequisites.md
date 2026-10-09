---
title: Prerequisiti per la distribuzione
description: Consulta un elenco di prerequisiti per la distribuzione di Commerce in un sistema di sviluppo, build o produzione.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '162'
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
