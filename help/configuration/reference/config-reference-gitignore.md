---
title: Riferimento .gitignore
description: Scopri come aggiungere un file incluso nell’elenco ignora .
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 0%

---


# Riferimento .gitignore

Il Magento Open Source include una base `.gitignore` file. Vedi [l’ultima versione di Commerce `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) file. Se devi aggiungere un file presente nella `.gitignore` è possibile utilizzare `-f` (forza) opzione quando si esegue lo staging di un commit:

```bash
git add <path/filename> -f
```
