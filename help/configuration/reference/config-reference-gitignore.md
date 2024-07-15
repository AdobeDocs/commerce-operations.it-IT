---
title: riferimento .gitignore
description: Scopri come aggiungere un file incluso nell’elenco da ignorare.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '51'
ht-degree: 0%

---

# riferimento .gitignore

Il Magento Open Source include un file `.gitignore` di base. Vedi [l&#39;ultimo file `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) di Commerce. Se è necessario aggiungere un file presente nell&#39;elenco `.gitignore`, è possibile utilizzare l&#39;opzione `-f` (forza) durante la gestione temporanea di un commit:

```bash
git add <path/filename> -f
```
