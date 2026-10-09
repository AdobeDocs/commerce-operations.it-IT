---
title: Verificare l'installazione
description: Segui questi passaggi per verificare che l’installazione Adobe Commerce on-premise sia andata a buon fine.
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%
---
# Verificare l&#39;installazione

Vai alla vetrina in un browser web. Ad esempio, se l&#39;URL di base dell&#39;installazione è `http://www.example.com`, immetterlo nella barra degli indirizzi o della posizione del browser.

La figura seguente mostra una pagina di vetrina di esempio. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

![Vetrina con tema Luma](../../assets/installation/install-success_store-luma.png)

## Verifica la vetrina (nessun dato di esempio)

Vai alla vetrina in un browser web. Ad esempio, se l&#39;URL di base dell&#39;installazione è `http://www.example.com`, immetterlo nella barra degli indirizzi o della posizione del browser.

La figura seguente mostra una pagina di vetrina di esempio. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

![Storefront che verifica la corretta installazione](../../assets/installation/install-success_store.png)

Se nella pagina viene visualizzato un errore `404 (Not Found)` o non vengono visualizzati gli stili, vedere [risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352).

## Verificare l’amministratore

Accedi all’amministratore in un browser web. Ad esempio, se l&#39;URL di base dell&#39;installazione è `http://www.example.com` e l&#39;URI amministratore è `admin_au1nT`, immettere `http://www.example.com/admin_au1nT` nella barra degli indirizzi o della posizione del browser.

L&#39;URI amministratore è specificato dal valore del parametro di installazione `backend-frontname`.

Quando richiesto, accedi come amministratore.

La figura seguente mostra un esempio di pagina Amministratore. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

![Amministratore che verifica la corretta installazione](../../assets/installation/install_success_admin.png)

Se nella pagina non sono visualizzati gli stili, vedere [risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352).

Se ricevi un errore 404 (Non trovato) simile al seguente, vedi [Errore di versione PHP o 404 durante l&#39;accesso ad Adobe Commerce nel browser](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
