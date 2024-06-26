---
title: Panoramica sull'installazione locale
description: Scopri il processo di installazione per le implementazioni locali di Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Panoramica sull&#39;installazione locale

>[!NOTE]
>
>Il diagramma seguente fornisce una panoramica di alto livello di _**on-premise**_ installazioni di Adobe Commerce:

![Come funziona l’installazione](../assets/installation/install-diagram-24.svg)

Il flusso generale di installazione è il seguente:

1. Configura l’ambiente server.

   Installa il software prerequisito, inclusi PHP, Apache, MySQL e il motore di ricerca. Consulta la [requisiti di sistema](system-requirements.md) per ulteriori informazioni.

1. Ottenere [chiavi di autenticazione](prerequisites/authentication-keys.md) all’archivio del Compositore Commerce.

1. Ottieni il software Adobe Commerce.

   * (Consigliato) Ottieni [Metapacchetto del compositore](composer.md) per gestire i moduli e le relative dipendenze.

   * Se desideri contribuire al codice di Magento Open Source o personalizzare l’applicazione, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) l’archivio GitHub. Questo metodo richiede familiarità sia con GitHub che con Composer.

1. Installare l&#39;applicazione utilizzando la riga di comando.

   Se il passaggio non riesce perché i prerequisiti software non sono configurati correttamente, esaminare [prerequisiti](prerequisites/overview.md).

1. [Verifica](next-steps/verify.md) l’installazione visualizzando la vetrina e l’amministratore.
