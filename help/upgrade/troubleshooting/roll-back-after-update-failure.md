---
title: Ripristino dello stato precedente dopo un errore di aggiornamento del modulo
description: Risolvi i problemi relativi all’aggiornamento di Adobe Commerce dopo aver incontrato un errore di aggiornamento del modulo.
exl-id: 1537a6b1-b450-4f90-bffb-73359fa71598
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '89'
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

Nel frattempo, puoi tornare a una versione precedente facendo clic su **Rollback**, che ripristina i dati anche se non ne hai eseguito il backup in precedenza.
