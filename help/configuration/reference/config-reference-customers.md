---
title: Riferimento percorsi di configurazione clienti
description: Consulta un elenco di valori di configurazione dei clienti.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Riferimento percorsi di configurazione clienti

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Clienti**.

Il [`magento app:config:dump` comando](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente. Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento fa _non_ list [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi newsletter

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Newsletter**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Consenti iscrizione ospite | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Da confermare | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail di conferma | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail di conferma | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail riuscito | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail riuscito | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail annullamento iscrizione | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per annullamento abbonamento | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di configurazione del cliente

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Configurazione cliente**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Intervallo di minuti online | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condividi account cliente | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita assegnazione automatica a gruppo di clienti | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcolo delle imposte basato su | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo predefinito | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo per ID IVA valido - Nazionale | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo per ID IVA valido - Intra-Unione | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo per ID IVA non valido | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppo di errori di convalida | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida per ogni transazione | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore predefinito per Disattiva modifiche gruppo automatiche in base all&#39;ID IVA | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra partita IVA in vetrina | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail di benvenuto predefinita | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail di benvenuto predefinita senza password | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Richiedi conferma e-mail | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail collegamento conferma | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail di benvenuto | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera un ID cliente facile da usare | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di protezione reimpostazione password | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di richieste di reimpostazione password | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo minimo tra richieste di reimpostazione password | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail dimenticato | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ricorda modello e-mail | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ripristina modello password | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail modello password | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza collegamento di ripristino (ore) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita completamento automatico per i moduli password di accesso/dimenticati | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di classi di caratteri richieste | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di errori di accesso all&#39;account di blocco | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza minima password | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo di blocco (minuti) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di righe in un indirizzo | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra prefisso | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opzioni a discesa Prefisso | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra secondo nome (iniziale) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra suffisso | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opzioni a discesa suffisso | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra data di nascita | `customer/address/dob_show`<br>In linea con le attuali best practice sulla sicurezza e la privacy, assicurati di essere a conoscenza di eventuali rischi legali e di sicurezza associati alla memorizzazione della data di nascita completa dei clienti (mese, giorno, anno) insieme ad altri identificatori personali, come il nome completo, prima di raccogliere o elaborare tali dati. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra partita IVA | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra genere | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita funzionalità credito negozio | `customer/magento_customerbalance/is_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostra cronologia crediti del negozio ai clienti | `customer/magento_customerbalance/show_history` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Rimborsa automaticamente credito negozio | `customer/magento_customerbalance/refund_automatically` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail aggiornamento credito store | `customer/magento_customerbalance/email_identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail per aggiornamento credito store | `customer/magento_customerbalance/email_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Reindirizza il cliente al dashboard account dopo l’accesso | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Testo | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Testo su una riga | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita funzionalità segmento cliente | `customer/magento_customersegment/is_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita CAPTCHA in Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Font | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità di visualizzazione | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di tentativi di accesso non riusciti | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout CAPTCHA (minuti) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di simboli | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Simboli utilizzati in CAPTCHA | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maiuscole/minuscole | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi elenco desideri

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Lista dei desideri**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilitato | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita più elenchi di desideri | `wishlist/general/multiple_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero di elenchi di desideri multipli | `wishlist/general/multiple_wishlist_number` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di e-mail consentite da inviare | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite lunghezza testo e-mail | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza riepilogo elenchi di desideri | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi inviti

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Inviti**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita funzionalità inviti | `magento_invitation/general/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita inviti in vetrina | `magento_invitation/general/enabled_on_front` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Gruppo di clienti con riferimento | `magento_invitation/general/registration_use_inviter_group` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrazione nuovi account | `magento_invitation/general/registration_required_invitation` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti ai clienti di aggiungere un messaggio personalizzato all&#39;invito | `magento_invitation/general/allow_customer_message` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di inviti consentito per l’invio in una sola volta | `magento_invitation/general/max_invitation_amount_per_send` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail invito cliente | `magento_invitation/email/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail invito cliente | `magento_invitation/email/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Percorsi punti premio

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Punti premio**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita funzionalità punti premio | `magento_reward/general/is_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita funzionalità punti premio in Storefront | `magento_reward/general/is_enabled_on_front` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| I clienti possono visualizzare la cronologia dei punti premio | `magento_reward/general/publish_history` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Soglia di rimborso saldo punti premio | `magento_reward/general/min_points_balance` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Saldo Punti Premio Limite A | `magento_reward/general/max_points_balance` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Punti premio scadono tra (giorni) | `magento_reward/general/expiration_days` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Calcolo scadenza punti premio | `magento_reward/general/expiry_calculation` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Rimborso automatico punti premio | `magento_reward/general/refund_automatically` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Detrazione automatica punti premio dall&#39;importo rimborso | `magento_reward/general/deduct_automatically` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagina di destinazione | `magento_reward/general/landing_page` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Acquisto | `magento_reward/points/order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Registrazione | `magento_reward/points/register` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Iscrizione newsletter | `magento_reward/points/newsletter` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Conversione di un invito in un cliente | `magento_reward/points/invitation_customer` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite quantità conversioni cliente invito | `magento_reward/points/invitation_customer_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Conversione dell&#39;invito in ordine | `magento_reward/points/invitation_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite quantità per conversioni da invito a ordine | `magento_reward/points/invitation_order_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Conversione invito in premio ordine | `magento_reward/points/invitation_order_frequency` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Rivedi invio | `magento_reward/points/review` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Limite quantità invio recensioni premiate | `magento_reward/points/review_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail | `magento_reward/notification/email_sender` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Iscrivi clienti per impostazione predefinita | `magento_reward/notification/subscribe_by_default` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| E-mail aggiornamento saldo | `magento_reward/notification/balance_update_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| E-mail di avviso scadenza punti premio | `magento_reward/notification/expiry_warning_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Avviso di scadenza prima del (giorni) | `magento_reward/notification/expiry_day_before` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Percorsi delle promozioni

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Promozioni**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita e-mail promemoria | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Interval | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuto dell’ora | `promo/magento_reminder/minutes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ora di inizio | `promo/magento_reminder/time` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di e-mail per esecuzione | `promo/magento_reminder/limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Soglia di errore invio e-mail | `promo/magento_reminder/threshold` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail promemoria | `promo/magento_reminder/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Lunghezza codice | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato del codice | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefisso codice | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso codice | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Trattino Ogni X Caratteri | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi del Registro di sistema per regali

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Registro Regali**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita registro regali | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di iscritti | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia massima e-mail inviate | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi persistenti del carrello

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Carrello acquisti persistente**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita persistenza | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata persistenza (secondi) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita &quot;Ricorda&quot; | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore predefinito &quot;Ricorda&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cancella persistenza alla disconnessione | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni carrello | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persist Wish List | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni elementi ordinati di recente | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni prodotti attualmente confrontati | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cronologia di confronto persistente | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantieni prodotti visualizzati di recente | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mantenere l’iscrizione al gruppo di clienti e la segmentazione | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
