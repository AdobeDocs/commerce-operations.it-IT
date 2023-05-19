---
title: riferimento .gitignore
description: Scopri come aggiungere un file incluso nell’elenco da ignorare.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---

# riferimento .gitignore

Il Magento Open Source include una base `.gitignore` file. Consulta [la versione più recente di Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) file. Se devi aggiungere un file che si trova in `.gitignore` , è possibile utilizzare `-f` (forza) opzione durante la gestione temporanea di un commit:

```bash
git add <path/filename> -f
```
