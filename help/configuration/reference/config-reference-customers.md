---
title: Riferimento per i percorsi di configurazione dei clienti
description: Consulta un elenco dei valori di configurazione dei clienti.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# Riferimento per i percorsi di configurazione dei clienti

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti**.

La [`magento app:config:dump` command](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che dovrebbe essere nel controllo della sorgente. Per ignorare facoltativamente le impostazioni di configurazione o per impostare le impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento _not_ elenco [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi newsletter

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Newsletter**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Consenti sottoscrizione guest | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conferma | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia e-mail di conferma | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail di conferma | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia e-mail con successo | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail di successo | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia e-mail senza abbonamento | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail di annullamento dell’abbonamento | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi di configurazione del cliente

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Configurazione del cliente**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Intervallo minuti online | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condividi account cliente | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita assegnazione automatica al gruppo cliente | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcolo fiscale basato su | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo predefinito | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo per ID IVA valido - Domestico | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo per ID IVA valido - Intra-Union | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo per ID IVA non valido | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo di errori di convalida | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida su ogni transazione | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore predefinito per disattivare le modifiche del gruppo automatico in base all&#39;ID IVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra numero IVA su Storefront | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail di benvenuto predefinita | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail di benvenuto predefinita senza password | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Richiedi conferma e-mail | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail collegamento di conferma | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail di benvenuto | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera ID cliente rispettoso dell’uomo | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di protezione per il ripristino della password | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di richieste di ripristino della password | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo minimo tra le richieste di ripristino della password | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail dimenticato | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail promemoria | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ripristina modello password | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail modello password | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza del collegamento di ripristino (ore) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita completamento automatico nei moduli di accesso/password dimenticata | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di classi di caratteri richieste | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di errori di accesso all’account di blocco | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza minima password | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora blocco (minuti) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di righe in un indirizzo via | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra prefisso | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opzioni elenco a discesa Prefisso | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra nome intermedio (iniziale) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra suffisso | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opzioni elenco a discesa Suffisso | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra data di nascita | `customer/address/dob_show`<br>In linea con le best practice in materia di sicurezza e privacy correnti, assicurati di essere a conoscenza di eventuali rischi legali e di sicurezza associati all’archiviazione della data completa di nascita (mese, giorno, anno) dei clienti insieme ad altri identificatori personali, come il nome completo, prima di raccogliere o elaborare tali dati. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra numero imposta/IVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra genere | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita funzionalità credito store | `customer/magento_customerbalance/is_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mostra cronologia crediti store ai clienti | `customer/magento_customerbalance/show_history` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Rimborso automatico del credito dell&#39;archivio | `customer/magento_customerbalance/refund_automatically` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Invia e-mail con aggiornamento credito | `customer/magento_customerbalance/email_identity` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Archivia modello e-mail di aggiornamento credito | `customer/magento_customerbalance/email_template` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Reindirizza il cliente al dashboard dell&#39;account dopo l&#39;accesso | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Testo | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Testo su una riga | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitare la funzionalità dei segmenti cliente | `customer/magento_customersegment/is_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Abilita CAPTCHA su Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Font | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità di visualizzazione | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di tentativi di accesso non riusciti | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout CAPTCHA (minuti) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di simboli | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Simboli utilizzati in CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Distintivo tra maiuscole e minuscole | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi elenco dei desideri

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Lista dei desideri**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilitato | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita elenchi di desideri multipli | `wishlist/general/multiple_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero di elenchi di desideri multipli | `wishlist/general/multiple_wishlist_number` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di e-mail consentite da inviare | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite lunghezza testo e-mail | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza riepilogo dei desideri | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi degli inviti

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Inviti**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilita funzionalità inviti | `magento_invitation/general/enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Abilita inviti su Storefront | `magento_invitation/general/enabled_on_front` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Gruppo di clienti di riferimento | `magento_invitation/general/registration_use_inviter_group` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Registrazione nuovi account | `magento_invitation/general/registration_required_invitation` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Consenti ai clienti di aggiungere messaggi personalizzati all&#39;e-mail di invito | `magento_invitation/general/allow_customer_message` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di inviti consentiti da inviare contemporaneamente | `magento_invitation/general/max_invitation_amount_per_send` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail invito cliente | `magento_invitation/email/identity` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail di invito del cliente | `magento_invitation/email/template` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Percorsi dei punti premio

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Punti premio**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilita funzionalità punti premio | `magento_reward/general/is_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Abilita la funzionalità dei punti premio su Storefront | `magento_reward/general/is_enabled_on_front` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| I Clienti Possono Vedere La Cronologia Dei Punti Di Premio | `magento_reward/general/publish_history` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Premi Punti Saldo Rimborso Soglia | `magento_reward/general/min_points_balance` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Saldo Dei Punti Di Ricompensa A Capo | `magento_reward/general/max_points_balance` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Punti premio Scadenza in (giorni) | `magento_reward/general/expiration_days` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Calcolo della scadenza dei punti premio | `magento_reward/general/expiry_calculation` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Rimborso automatico | `magento_reward/general/refund_automatically` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Detrazione automatica dei punti premio dall&#39;importo del rimborso | `magento_reward/general/deduct_automatically` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Pagina di destinazione | `magento_reward/general/landing_page` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Acquisto | `magento_reward/points/order` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Registrazione | `magento_reward/points/register` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Iscrizione alla newsletter | `magento_reward/points/newsletter` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Conversione dell&#39;invito al cliente | `magento_reward/points/invitation_customer` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Invito alle conversioni cliente Limite di quantità | `magento_reward/points/invitation_customer_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Conversione dell&#39;invito all&#39;ordine | `magento_reward/points/invitation_order` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Limite di quantità per l&#39;invito alle conversioni ordine | `magento_reward/points/invitation_order_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Conversione invito in premio ordine | `magento_reward/points/invitation_order_frequency` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Invia per revisione | `magento_reward/points/review` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Revisioni premiate Limite di quantità di invio | `magento_reward/points/review_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail | `magento_reward/notification/email_sender` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Iscriviti a clienti per impostazione predefinita | `magento_reward/notification/subscribe_by_default` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Aggiorna e-mail | `magento_reward/notification/balance_update_template` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| E-mail di avviso sulla scadenza dei punti premio | `magento_reward/notification/expiry_warning_template` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Avviso di scadenza prima (giorni) | `magento_reward/notification/expiry_day_before` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Percorsi di promozione

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Promozioni**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilita e-mail promemoria | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervallo | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuto dell&#39;ora | `promo/magento_reminder/minutes` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Ora di inizio | `promo/magento_reminder/time` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di e-mail per ogni esecuzione | `promo/magento_reminder/limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Soglia errore invio e-mail | `promo/magento_reminder/threshold` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Invia e-mail promemoria | `promo/magento_reminder/identity` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Lunghezza del codice | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato del codice | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefisso di codice | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso codice | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Trattino ogni X carattere | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi del registro dei regali

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Registro dei regali**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilita registro dei regali | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registratori massimi | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia massima e-mail inviate | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi del carrello acquisti persistenti

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Carrello acquisti persistente**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilita persistenza | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata (secondi) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita &quot;Ricorda utente&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore predefinito &quot;Ricorda utente&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cancella persistenza all&#39;uscita | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Carrello acquisti permanente | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lista dei desideri persistenti | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni elementi ordinati di recente | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni prodotti attualmente confrontati | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cronologia confronto persistenza | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni prodotti visualizzati di recente | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantenere l&#39;appartenenza al gruppo cliente e la segmentazione | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
