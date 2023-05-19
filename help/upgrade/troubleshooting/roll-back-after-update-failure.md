---
title: Ripristino dello stato precedente dopo un errore di aggiornamento del modulo
description: Risolvi i problemi relativi all’aggiornamento di Adobe Commerce o di Magento Open Source dopo aver riscontrato un errore di aggiornamento del modulo.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# Ripristino dello stato precedente dopo un errore di aggiornamento del modulo

Se l’aggiornamento del modulo non riesce, nel registro della console vengono visualizzati messaggi simili a quelli riportati di seguito:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

Nell’esempio precedente, non esiste una versione del componente a cui eseguire il rollback. Contatta il fornitore del componente o prova a risolvere il problema da solo.

Nel frattempo, puoi tornare a una versione precedente facendo clic su **Rollback**, che recupera i dati anche se non ne è stato eseguito il backup in precedenza.
