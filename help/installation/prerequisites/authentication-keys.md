---
title: Ottieni le chiavi di autenticazione
description: Segui questi passaggi per recuperare le credenziali di accesso ai pacchetti di Adobe Commerce Composer su repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Ottieni le chiavi di autenticazione

Il `repo.magento.com` L’archivio è il luogo in cui vengono memorizzati i pacchetti Adobe Commerce e Compositore di terze parti e richiede l’autenticazione. Utilizza il tuo account di Commerce Marketplace per generare una coppia di 32 caratteri *chiavi di autenticazione* per accedere all’archivio.

Per accedere ai pacchetti Adobe Commerce, devi utilizzare le chiavi associate a un MAGEID a cui è stato concesso l’accesso. Il MAGEID è in genere il contatto principale sull’account Adobe Commerce e potrebbe non essere sempre il proprietario del progetto di infrastruttura cloud di Adobe Commerce.

>[!TIP]
>
>Se incontra [errori](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), potresti non disporre dell’autorizzazione per accedere al pacchetto o il diritto di accesso è scaduto a causa di una fattura in sospeso sul tuo account.
>
>* Se si è la persona di contatto principale dell&#39;account, verificare che non siano presenti fatture in sospeso nell&#39;elenco dell&#39;account.
>* Se le chiavi fornite dal contatto principale non funzionano e non sono presenti fatture in sospeso nell&#39;account, contattare [Supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) per assistenza nell’utilizzo del MAGEID del contatto principale.

Per creare le chiavi di autenticazione:

1. Accedi a [Commerce Marketplace](https://commercemarketplace.adobe.com/). Se non hai un account, fai clic su **Registrati**.

1. Fai clic sul nome del tuo account in alto a destra della pagina e seleziona **Il mio profilo**.

1. Clic **Chiavi di accesso** nella scheda Marketplace.

   ![Chiavi di accesso sicure a Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Clic **Creare una nuova chiave di accesso**. Immetti un nome specifico per le chiavi (ad esempio, il nome dello sviluppatore che riceve le chiavi) e fai clic su **OK**.

1. Le nuove chiavi pubbliche e private sono ora associate al tuo account su cui puoi fare clic per copiarle. Salva queste informazioni o tieni aperta la pagina quando lavori con il progetto. Utilizza il **Chiave pubblica** come nome utente e **Chiave privata** come password.

## Gestire le chiavi di autenticazione

È inoltre possibile disattivare o eliminare le chiavi di autenticazione. Ad esempio, puoi disabilitare o eliminare le chiavi per motivi di sicurezza dopo che un utente ha lasciato l’organizzazione.

* Per disattivare i tasti: fai clic su **Disattiva**. È possibile eseguire questa operazione se si desidera sospendere l&#39;utilizzo delle chiavi.
* Per attivare una chiave precedentemente disabilitata: fare clic su **Abilita**.
* Per eliminare le chiavi: fai clic su **Elimina**.

### Gestisci token di accesso SSH

Per scaricare le versioni di Adobe Commerce utilizzando SSH, devi generare un token di accesso per i download. Per generare un token:

1. Accedi al tuo [Account magento.com](https://account.magento.com/customer/account/login).
1. Clic **Il mio account** nella parte superiore della pagina.
1. Clic **Impostazioni account** > **Scarica il token di accesso**.

   ![Accedere alle chiavi](../../assets/installation/connect_keys1.png)

1. Clic **Genera nuovo token** per sostituire e disattivare un token esistente.

Per scaricare una versione devi usare il tuo MAGEID più il token. Il tuo MAGEID viene visualizzato in alto a sinistra nella pagina del tuo account.

Ad esempio:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilizza le chiavi di autenticazione per:

* [Ottieni il metapacchetto (integratori, pacchetti)](../composer.md)
* [Clonare l’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (solo sviluppatori contributori)
* [Aggiornare e gestire i moduli](../../upgrade/modules/upgrade.md)
