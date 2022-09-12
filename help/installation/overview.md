---
title: Panoramica sull'installazione in loco
description: Scopri il processo di installazione per le distribuzioni locali di Adobe Commerce e Magenti Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Panoramica sull&#39;installazione in loco

>[!NOTE]
>
>Il diagramma seguente fornisce una panoramica di alto livello di _**locale**_ installazioni di Adobe Commerce e Magento Open Source:

![Come funziona l&#39;installazione](../assets/installation/install-diagram-24.svg)

Il flusso generale di installazione è il seguente:

1. Configurare l&#39;ambiente server.

   Installare il software prerequisito, inclusi PHP, Apache, MySQL e il motore di ricerca. Consulta la sezione [requisiti di sistema](system-requirements.md) per ulteriori informazioni.

1. Get [chiavi di autenticazione](prerequisites/authentication-keys.md) all’archivio Commerce Composer.

1. Scarica il software Adobe Commerce o Magenti Open Source.

   * (Consigliato) Ottieni il [Metapackage compositore](composer.md) per gestire i moduli e le loro dipendenze.

   * Se desideri contribuire alla base di codice del Magento Open Source o personalizzare l&#39;applicazione, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) l’archivio GitHub. Questo metodo richiede familiarità sia con GitHub che con il Compositore esperienza.

1. Installa l&#39;applicazione utilizzando la riga di comando.

   Se il passaggio non riesce perché il software di prerequisito non è configurato correttamente, controlla il [prerequisiti](prerequisites/overview.md).

1. [Verifica](next-steps/verify.md) l&#39;installazione visualizzando la vetrina e l&#39;amministratore.

