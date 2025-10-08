---
title: riferimento .gitignore
description: Scopri come aggiungere file all’elenco .gitignore per i progetti Adobe Commerce. Scopri le best practice per la gestione del controllo delle versioni e l’esclusione dei file.
exl-id: 7c53b50a-7bdf-433b-bebb-0129f792a1a4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '60'
ht-degree: 0%

---

# riferimento .gitignore

Magento Open Source include un file `.gitignore` di base. Vedi [l&#39;ultimo file `.gitignore`](https://raw.githubusercontent.com/magento/magento2/2.4/.gitignore) di Commerce. Se è necessario aggiungere un file presente nell&#39;elenco `.gitignore`, è possibile utilizzare l&#39;opzione `-f` (forza) durante la gestione temporanea di un commit:

```bash
git add <path/filename> -f
```
