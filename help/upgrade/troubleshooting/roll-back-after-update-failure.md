---
title: Ripristino dopo un errore di aggiornamento del modulo
description: Risolvere i problemi relativi all’aggiornamento di Adobe Commerce o Magento Open Source dopo un errore di aggiornamento del modulo.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ripristino dopo un errore di aggiornamento del modulo

Se l’aggiornamento del modulo non riesce, i messaggi simili alla seguente vengono visualizzati nel registro della console:

```terminal
[2015-08-14 12:12:02 CDT] Job "update {"components":[{"name":"example/module","version":"1.1.0"}]}" has been started
[2015-08-14 12:12:02 CDT] Starting composer update...
[2015-08-14 12:12:02 CDT] An error occurred while executing job "update {"components":
[{"name":"example/module","version":"1.1.0"}]}": Could not complete update {"components":
[{"name":"example/module","version":"1.1.0"}]} successfully: Cannot find component to update
```

Nell’esempio precedente, non esiste una versione di componente a cui eseguire il rollback. Contatta il fornitore del componente o prova a risolvere il problema da solo.

Nel frattempo, puoi ripristinare una versione precedente facendo clic su **Ripristino**, che recupera i dati anche se non hai eseguito il backup in precedenza.
