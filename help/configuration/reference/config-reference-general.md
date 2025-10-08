---
title: Riferimento generale ai percorsi di configurazione
description: Scopri percorsi e valori di configurazione generali e avanzati per Adobe Commerce. Scopri le opzioni di configurazione di sistema, sicurezza e amministrazione.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# Riferimento ai percorsi di configurazione generali e avanzati

In questo argomento sono elencati i percorsi di configurazione generali e avanzati e _non_ [valori sensibili e specifici del sistema](config-reference-sens.md). Il comando [`magento app:config:dump`](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente.

Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedere [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables).

## Categoria generale

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale**.

### Percorsi generali

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > Generale > **Generale**.

| Nome | Percorso configurazione | Solo Commerce? | Sensibili? |
|--------------|--------------|--------------|--------------|
| Paese predefinito | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Consenti paesi | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Il CAP è facoltativo per | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Paesi dell&#39;Unione Europea | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Destinazioni principali | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lo stato è obbligatorio per | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti di scegliere lo stato se è facoltativo per il paese | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Fuso orario | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Lingua | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Unità di peso | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Primo giorno della settimana | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Giorni fine settimana | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Limitazione di accesso | `general/restriction/is_active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | |
| Modalità di restrizione | `general/restriction/mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | |
| Pagina di avvio | `general/restriction/http_redirect` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | |
| Pagina di destinazione | `general/restriction/cms_page` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | |
| Risposta HTTP | `general/restriction/http_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | |
| Nome store | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Numero di telefono store | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Memorizza ore di funzionamento | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Paese | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Regione/Stato | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| CAP | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Città | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Indirizzo | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Indirizzo 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Partita IVA | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Abilita modalità archivio singolo | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |

{style="table-layout:auto"}

### Percorsi web

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Web**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Aggiungi codice store agli URL | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reindirizzamento automatico all&#39;URL di base | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa riscritture server Web | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa URL protetti in Storefront | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizzare URL protetti in Admin | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita HTTP Strict Transport Security (HSTS) | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aggiornare richieste non sicure | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intestazione offloader | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Home page di CMS | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagina CMS nessuna route | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagina CMS senza cookie | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra breadcrumb per pagine CMS | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata dei cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa solo HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità di restrizione cookie | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida REMOTE_ADDR | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida HTTP_VIA | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida HTTP_X_FORWARDED_FOR | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida HTTP_USER_AGENT | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa SID in Storefront | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Reindirizza alla pagina CMS se i cookie sono disabilitati | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra avviso se JavaScript è disabilitato | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra avviso se l&#39;archiviazione locale è disabilitata | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi di impostazione della valuta

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Impostazione valuta**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Valuta di base | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta di visualizzazione predefinita | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valute consentite | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` | |
| Fixer.io | `TBD` | |
| Webservicex | `TBD` | |
| Timeout connessione in secondi | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout connessione in secondi | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout connessione in secondi | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Servizio | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinatario e-mail per errore | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore mittente e-mail | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per errore | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi contatti

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Contatti**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita Contattaci | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia e-mail a | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi dei rapporti

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Rapporti**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Inizio progressivo anno | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inizio mese corrente | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi di gestione dei contenuti

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Gestione contenuto**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita editor WYSIWYG | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa URL statici per contenuti multimediali in WYSIWYG per il catalogo | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita funzionalità gerarchia | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita metadati gerarchia | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Layout predefinito per menu gerarchia | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi di reporting di New Relic

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generali** > **Generazione rapporti New Relic**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita integrazione New Relic | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome applicazione New Relic | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Attiva Cron | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Categoria avanzata

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate**.

### Percorsi di amministrazione

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Amministratore**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Modello e-mail per password dimenticata | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail dimenticato e reimpostato | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello di notifica utente | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagina di avvio | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa URL amministratore personalizzato | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa percorso amministratore personalizzato | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condivisione account amministratore | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di protezione reimpostazione password | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di scadenza collegamento di ripristino (ore) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di richieste di reimpostazione password | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo minimo tra richieste di reimpostazione password | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aggiungi chiave segreta agli URL | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| L’accesso fa distinzione tra maiuscole e minuscole | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata sessione amministratore (secondi) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di errori di accesso all&#39;account di blocco | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo di blocco (minuti) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata password (giorni) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modifica password | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita grafici | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitare il CAPTCHA in Admin | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Font | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità di visualizzazione | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di tentativi di accesso non riusciti | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout CAPTCHA (minuti) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di simboli | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Simboli utilizzati in CAPTCHA | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maiuscole/minuscole | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azioni abilitate | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi di sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Durata dei messaggi riusciti | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ritenta messaggi in corso dopo | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata messaggi non riusciti | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata dei nuovi messaggi | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera pianificazioni ogni | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pianifica in anticipo per | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mancato se non eseguito entro | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pulizia cronologia ogni | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata della cronologia di successo | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata cronologia errori | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa processo separato | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera pianificazioni ogni | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pianifica in anticipo per | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mancato se non eseguito entro | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pulizia cronologia ogni | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata della cronologia di successo | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata cronologia errori | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera pianificazioni ogni | `system/cron/staging/schedule_generate_every` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pianifica in anticipo per | `system/cron/staging/schedule_ahead_for` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mancato se non eseguito entro | `system/cron/staging/schedule_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pulizia cronologia ogni | `system/cron/staging/history_cleanup_every` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Durata della cronologia di successo | `system/cron/staging/history_success_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Durata cronologia errori | `system/cron/staging/history_failure_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Usa processo separato | `system/cron/staging/use_separate_process` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Genera pianificazioni ogni | `system/cron/catalog/event/schedule_generate_every` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pianifica in anticipo per | `system/cron/catalog/event/schedule_ahead_for` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mancato se non eseguito entro | `system/cron/catalog/event/schedule_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pulizia cronologia ogni | `system/cron/catalog/event/history_cleanup_every` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Durata della cronologia di successo | `system/cron/catalog/event/history_success_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Durata cronologia errori | `system/cron/catalog/event/history_failure_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Usa processo separato | `system/cron/catalog/event/use_separate_process` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Usa processo separato | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Disabilita comunicazioni e-mail | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta percorso di ritorno | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail del percorso di ritorno | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valute installate | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa HTTPS per ottenere i feed | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza di aggiornamento | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ultimo aggiornamento | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita backup pianificato | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di backup | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità manutenzione | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata voce registro, giorni | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza archiviazione log | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Applicazione di caching | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL per contenuto pubblico | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di tolleranza | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esporta configurazione | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Giorni salvati nel registro | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Storage multimediale | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seleziona database multimediale | `system/media_storage_configuration/media_database` (obsoleto in Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di aggiornamento dell’ambiente | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Salva file, giorni | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita pulizia cronologia file pianificata | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per errore | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Percorsi per sviluppatori

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppatore**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Tipo di flusso di lavoro | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti collegamenti simbolici | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimizza Html | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita suggerimenti percorso modello per Storefront | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita suggerimenti percorso modello per l’amministratore | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aggiungere nomi di blocco ai suggerimenti | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Accedi al file | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Accedi a syslog | `dev/syslog/syslog_logging` |  |
| Abilitato per Storefront | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per l&#39;amministratore | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unisci file JavaScript | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita bundle JavaScript | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimizza file JavaScript | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Strategia di traduzione | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Registra errori JS nell’archiviazione della sessione | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unisci file CSS | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimizza file CSS | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adattatore immagine | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Firma file statici | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indicizzazione asincrona | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Memorizza nella cache attributi definiti dall&#39;utente | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
