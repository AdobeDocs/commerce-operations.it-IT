---
title: Verificare l'installazione
description: Segui questi passaggi per verificare che l’installazione on-premise di Adobe Commerce o di Magento Open Source sia andata a buon fine.
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Verificare l&#39;installazione

Vai alla vetrina in un browser web. Ad esempio, se l’URL di base dell’installazione è `http://www.example.com`, immetterlo nella barra degli indirizzi o della posizione del browser.

La figura seguente mostra una pagina di vetrina di esempio. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

![Vetrina con il tema Luma](../../assets/installation/install-success_store-luma.png)

## Verifica la vetrina (nessun dato di esempio)

Vai alla vetrina in un browser web. Ad esempio, se l’URL di base dell’installazione è `http://www.example.com`, immetterlo nella barra degli indirizzi o della posizione del browser.

La figura seguente mostra una pagina di vetrina di esempio. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

![Storefront che verifica la corretta installazione](../../assets/installation/install-success_store.png)

Se nella pagina viene visualizzato un tag `404 (Not Found)` errore o non visualizza gli stili, consulta [risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352).

## Verificare l’amministratore

Accedi all’amministratore in un browser web. Ad esempio, se l’URL di base dell’installazione è `http://www.example.com`e l’URI amministratore è `admin_au1nT`, immetti `http://www.example.com/admin_au1nT` nella barra degli indirizzi o della posizione del browser.

(L’URI amministratore è specificato dal valore della proprietà `backend-frontname` parametro di installazione).

Quando richiesto, accedi come amministratore.

La figura seguente mostra un esempio di pagina Amministratore. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

![Amministratore che verifica la corretta installazione](../../assets/installation/install_success_admin.png)

Se nella pagina non sono visualizzati gli stili, consulta [risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352).

Se ricevi un errore 404 (Non trovato) simile al seguente, vedi [Errore di versione PHP o 404 durante l’accesso ad Adobe Commerce nel browser](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
