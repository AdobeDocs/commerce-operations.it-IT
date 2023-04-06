---
title: Prerequisiti per la distribuzione
description: Visualizza un elenco di prerequisiti per la distribuzione di Commerce in un sistema di sviluppo, build o produzione.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Prerequisiti per i sistemi di sviluppo, generazione e produzione

Le autorizzazioni e la proprietà dei file devono essere coerenti tra i sistemi di sviluppo, generazione e produzione. Per far funzionare questa operazione, è necessario:

- Tutti i seguenti elementi:

   - Imposta lo stesso nome utente proprietario del file system su tutti i sistemi
   - Assicurati che il server web venga eseguito come lo stesso utente su tutti i sistemi
   - Assicurati che il proprietario del file system sia nel gruppo del server web su tutti i sistemi

- Modifica le autorizzazioni e la proprietà del file system Commerce su ogni sistema in base alle esigenze utilizzando le seguenti linee guida:

   - Sviluppo e creazione: [Impostare la proprietà e le autorizzazioni pre-installazione (due utenti)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produzione: [Proprietà e autorizzazioni del commercio nello sviluppo e nella produzione](file-system-permissions.md)

>[!INFO]
>
>Se si sceglie questo approccio, è necessario impostare le autorizzazioni e la proprietà del file system ogni volta che si estrae il codice dal sistema di compilazione (se il proprietario del file system o l&#39;utente del server web sono diversi sul sistema di generazione).
