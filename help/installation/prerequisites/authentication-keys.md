---
title: Ottieni le chiavi di autenticazione
description: Segui questi passaggi per recuperare le credenziali per accedere ai pacchetti Adobe Commerce e Magenti Open Source Composer su repo.magento.com.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Ottieni le chiavi di autenticazione

La `repo.magento.com` archivio è il luogo in cui vengono archiviati i pacchetti Compositore Magento Open Source e di terze parti Adobe Commerce e richiede l’autenticazione. Utilizza il tuo account Commerce Marketplace per generare una coppia di 32 caratteri *chiavi di autenticazione* per accedere al repository.

>[!NOTE]
>
>Per poter accedere ai pacchetti Adobe Commerce e Magenti Open Source, devi utilizzare le chiavi associate a un MAGEID a cui è stato concesso l’accesso a tali pacchetti. Il MAGEID è in genere il **Contatto di fatturazione** sull’account Adobe Commerce e potrebbe non essere sempre il **Proprietario progetto** del progetto Adobe Commerce on cloud Infrastructure. Se incontri [errori](https://support.magento.com/hc/en-us/articles/360040296392), è possibile che non si disponga dell&#39;autorizzazione per accedere al pacchetto o che il diritto di accesso sia scaduto a causa di una fattura in sospeso sul conto. Contatto [Supporto Adobe Commerce](https://support.magento.com/hc/en-us) per assistenza sul tuo MAGEID.

Per creare le chiavi di autenticazione:

1. Accedi a [Commerce Marketplace](https://marketplace.magento.com). Se non disponi di un account, fai clic su **Registro**.
1. Fai clic sul nome dell’account in alto a destra della pagina e seleziona **Il mio profilo**.

1. Fai clic su **Chiavi di accesso** nella scheda Marketplace .

   ![Ottieni le chiavi di accesso sicure su Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Fai clic su **Creare una nuova chiave di accesso**. Immetti un nome specifico per le chiavi (ad esempio, il nome dello sviluppatore che riceve le chiavi) e fai clic su **OK**.

1. All’account sono ora associate nuove chiavi pubbliche e private che è possibile fare clic per copiare. Salva queste informazioni o tieni aperta la pagina quando lavori con il progetto. Utilizza la **Chiave pubblica** come nome utente e **Chiave privata** come password.

## Gestione delle chiavi di autenticazione

È inoltre possibile disattivare o eliminare le chiavi di autenticazione. Ad esempio, puoi disattivare o eliminare le chiavi per motivi di sicurezza dopo che un utente ha lasciato l’organizzazione.

* Per disabilitare le chiavi: Fai clic su **Disattiva**. Puoi farlo se desideri sospendere l’uso delle chiavi.
* Per abilitare una chiave precedentemente disabilitata: Fai clic su **Abilita**.
* Per eliminare le chiavi: Fai clic su **Elimina**.

### Gestisci token di accesso SSH

Per scaricare le versioni di Adobe Commerce utilizzando SSH, devi generare un token di accesso per i download. Per generare un token:

1. Accedi al tuo [account magento.com](https://account.magento.com/customer/account/login).
1. Fai clic su **Il mio account** nella parte superiore della pagina.
1. Fai clic su **Impostazioni account** > **Scarica il token di accesso**.

   ![Accedere alle chiavi](../../assets/installation/connect_keys1.png)

1. Fai clic su **Genera nuovo token** per sostituire e disabilitare un token esistente.

Per scaricare una versione, devi usare il tuo MAGEID e il tuo token. Il tuo MAGEID viene visualizzato in alto a sinistra nella pagina dell&#39;account.

Ad esempio:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilizza le tue chiavi di autenticazione per:

* [Ottieni il metapackage (integratori, pacchetti)](../composer.md)
* [Clonare l’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (solo per sviluppatori contributori)
* [Aggiornare e gestire i moduli](../../upgrade/modules/upgrade.md)
