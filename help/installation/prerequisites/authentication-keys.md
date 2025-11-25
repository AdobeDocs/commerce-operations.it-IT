---
title: Ottieni le chiavi di autenticazione
description: Segui questi passaggi per recuperare le credenziali di accesso ai pacchetti di Adobe Commerce Composer su repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# Ottieni le chiavi di autenticazione

L&#39;archivio `repo.magento.com` è il luogo in cui sono archiviati i pacchetti Adobe Commerce e Compositore di terze parti e richiede l&#39;autenticazione. Utilizza il tuo account Commerce Marketplace per generare una coppia di *chiavi di autenticazione* di 32 caratteri per accedere all&#39;archivio.

Per accedere ai pacchetti Adobe Commerce, devi utilizzare le chiavi associate a un MAGEID a cui è stato concesso l’accesso. Il MAGEID è in genere il contatto principale sull’account Adobe Commerce e potrebbe non essere sempre il proprietario del progetto di infrastruttura cloud di Adobe Commerce.

>[!TIP]
>
>Se riscontri [errori](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=it) o non vedi la sezione [!UICONTROL Access Keys] nella scheda Marketplace, potresti non disporre dell&#39;autorizzazione per accedere al pacchetto o il diritto di accesso è scaduto a causa di una fattura in sospeso sul tuo account.
>
>* Se si è la persona di contatto principale dell&#39;account, verificare che non siano presenti fatture in sospeso nell&#39;elenco dell&#39;account.
>* Se le chiavi fornite dal contatto principale non funzionano e non sono presenti fatture in sospeso nell&#39;account, il contatto principale deve contattare il [supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket) per assistenza.

Per creare le chiavi di autenticazione:

1. Accedi a [Commerce Marketplace](https://commercemarketplace.adobe.com/). Se non hai un account, fai clic su **Registra**.

1. Fai clic sul nome del tuo account in alto a destra della pagina e seleziona **Il mio profilo**.

1. Fare clic su **Chiavi di accesso** nella scheda Marketplace.

   ![Ottieni le tue chiavi di accesso sicure in Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Fare clic su **Crea una nuova chiave di accesso**. Immettere un nome specifico per le chiavi, ad esempio il nome dello sviluppatore che le riceve, quindi fare clic su **OK**.

1. Le nuove chiavi pubbliche e private sono ora associate al tuo account su cui puoi fare clic per copiarle. Salva queste informazioni o tieni aperta la pagina quando lavori con il progetto. Utilizza la **chiave pubblica** come nome utente e la **chiave privata** come password.

## Gestire le chiavi di autenticazione

È inoltre possibile disattivare o eliminare le chiavi di autenticazione. Ad esempio, puoi disabilitare o eliminare le chiavi per motivi di sicurezza dopo che un utente ha lasciato l’organizzazione.

* Per disabilitare le chiavi, fare clic su **Disable**. È possibile eseguire questa operazione se si desidera sospendere l&#39;utilizzo delle chiavi.
* Per abilitare una chiave precedentemente disabilitata: fare clic su **Abilita**.
* Per eliminare le chiavi: fare clic su **Elimina**.

### Gestisci token di accesso SSH

Per scaricare le versioni di Adobe Commerce utilizzando SSH, devi generare un token di accesso per i download. Per generare un token:

1. Accedi al tuo account [magento.com](https://account.magento.com/customer/account/login).
1. Fai clic su **Il mio account** nella parte superiore della pagina.
1. Fai clic su **Impostazioni account** > **Scarica token di accesso**.

   ![Accedi alle chiavi](../../assets/installation/connect_keys1.png)

1. Fai clic su **Genera nuovo token** per sostituire e disabilitare un token esistente.

Per scaricare una versione devi usare il tuo MAGEID più il token. Il tuo MAGEID viene visualizzato in alto a sinistra nella pagina del tuo account.

Ad esempio:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Utilizza le chiavi di autenticazione per:

* [Ottieni il metapacchetto (integratori, pacchetti)](../composer.md)
* [Clona l&#39;archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) (solo sviluppatori partecipanti)
* [Aggiornare e gestire i moduli](../../upgrade/modules/upgrade.md)
