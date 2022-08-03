---
title: Riferimento per i percorsi di configurazione dell'estensione B2B
description: Vedi un elenco dei valori di configurazione relativi a B2B.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---


# Riferimento per i percorsi di configurazione dell&#39;estensione B2B

_Questo è disponibile per le istanze con installazione di B2B per Adobe Commerce._

In questo argomento sono elencati i percorsi di configurazione per l’estensione Commerce Enterprise B2B. La [`magento app:config:dump` command](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che dovrebbe essere nel controllo della sorgente.

>[!INFO]
>
>Elenco di riferimento _only_ percorsi di configurazione univoci per B2B per Adobe Commerce. Questa estensione include tutti i percorsi di configurazione per Adobe Commerce.

Per i percorsi di configurazione, vedi:

- [Percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)

Per ignorare facoltativamente le impostazioni di configurazione o per impostare le impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables).

## Categoria generale

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Amministratore in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Percorsi di funzionalità B2B

Questi valori di configurazione sono disponibili in Amministratore in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nome | Percorso di configurazione | Crittografato? | Specifico del sistema? | Sensibile? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Abilita società | `btob/website_configuration/company_active` |  |  |  |
| Abilita catalogo condiviso | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| Abilita preventivo B2B | `btob/website_configuration/negotiablequote_active` |  |  |  |
| Attiva ordine rapido | `btob/website_configuration/quickorder_active` |  |  |  |
| Abilita elenco richieste di acquisto | `btob/website_configuration/requisition_list_active` |  |  |  |
| Metodi di pagamento applicabili | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| Metodi di pagamento | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Categoria clienti

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Amministratore in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Percorsi di configurazione aziendali

Questi valori di configurazione sono disponibili in Amministratore in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nome | Percorso di configurazione | Crittografato? | Specifico del sistema? | Sensibile? |
|--------------|--------------|--------------|--------------|--------------|
| Consenti registrazione società dal negozio | `company/general/allow_company_registration` |  |  |  |
| Destinatario e-mail di registrazione società | `company/email/company_registration` |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail di registrazione società a | `company/email/company_registration_copy` |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Metodo Invia copia e-mail | `company/email/company_copy_method` |  |  |  |
| E-mail di registrazione della società predefinita | `company/email/company_notify_admin_template` |  |  |  |
| E-mail relative al cliente | `company/email/heading_customer` |  |  |  |
| E-mail assegnato rappresentante vendite predefinito | `company/email/customer_sales_representative_template` |  |  |  |
| Assegna società predefinita a e-mail cliente | `company/email/customer_company_customer_assign_template` |  |  |  |
| E-mail amministratore assegnazione società predefinita | `company/email/customer_assign_super_user_template` |  |  |  |
| E-mail inattiva amministratore società predefinita | `company/email/customer_inactivate_super_user_template` |  |  |  |
| L’Amministratore Aziendale Predefinito È Stato Modificato In E-Mail Membro | `company/email/customer_remove_super_user_template` |  |  |  |
| E-mail attiva stato cliente predefinito | `company/email/customer_account_activated_template` |  |  |  |
| E-mail inattiva stato cliente predefinito | `company/email/customer_account_locked_template` |  |  |  |
| Modifica dello stato della società | `company/email/heading_company_status` |  |  |  |
| Destinatario e-mail modifica stato società | `company/email/company_status_change` |  |  |  |
| Invia copia e-mail modifica stato società in | `company/email/company_status_change_copy` |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Metodo Invia copia e-mail | `company/email/company_status_copy_method` |  |  |  |
| Modifica Dello Stato Aziendale Predefinito In Posta Elettronica Attiva 1 | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| Modifica dello stato della società predefinita in un indirizzo e-mail attivo 2 | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| Modifica dello stato predefinito della società in un messaggio e-mail rifiutato | `company/email/company_status_rejected_template` |  |  |  |
| Modifica dello stato predefinito della società in un messaggio e-mail bloccato | `company/email/company_status_blocked_template` |  |  |  |
| Modifica dello stato della società predefinita in un messaggio di posta elettronica di approvazione in sospeso | `company/email/company_status_pending_approval_template` |  |  |  |
| Credito della società | `company/email/heading_company_credit` |  |  |  |
| Mittente e-mail modifica credito società | `company/email/company_credit_change` |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail modifica credito società a | `company/email/company_credit_change_copy` |  |  |  |
| Metodo Invia copia e-mail | `company/email/company_credit_copy_method` |  |  |  |
| Modello e-mail allocato | `company/email/credit_allocated_email_template` |  |  |  |
| Modello e-mail aggiornato | `company/email/credit_updated_email_template` |  |  |  |
| Modello e-mail rimborsato | `company/email/credit_reimbursed_email_template` |  |  |  |
| Modello e-mail rimborsato | `company/email/credit_refunded_email_template` |  |  |  |
| Modello e-mail invertito | `company/email/credit_reverted_email_template` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Percorsi elenco richieste

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Elenchi richieste di acquisto**.

| Nome | Percorso di configurazione | Crittografato? | Specifico del sistema? | Sensibile? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Numero di elenchi di richieste di acquisto | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Categoria vendite

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Vendite**.

### Percorsi e-mail di vendita

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **E-mail di vendita**.

| Nome | Percorso di configurazione | Crittografato? | Specifico del sistema? | Sensibile? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Abilitato | `sales_email/quote/enabled` |  |  |  |
| Modello di preventivo aggiornato (a Acquirente) | `sales_email/quote/updated_buyer_template` |  |  |  |
| Modello di preventivo rifiutato (all&#39;acquirente) | `sales_email/quote/declined_buyer_template` |  |  |  |
| Nuovo modello di preventivo (al venditore) | `sales_email/quote/new_seller_template` |  |  |  |
| Modello di preventivo aggiornato (al venditore) | `sales_email/quote/updated_seller_template` |  |  |  |
| Scadenza preventivo (in 48 ore) | `sales_email/quote/expire_two_days_template` |  |  |  |
| Scadenza preventivo (in 24 ore) | `sales_email/quote/expire_one_day_template` |  |  |  |
| Ripristino della data di scadenza | `sales_email/quote/expire_reset_template` |  |  |  |
| Invia copia e-mail preventivo a | `sales_email/quote/copy_to` |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia metodo di copia e-mail preventivo | `sales_email/quote/copy_method` |  |  |  |

{style=&quot;table-layout:auto&quot;}

### Percorsi virgolette

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Preventivi**.

| Nome | Percorso di configurazione | Crittografato? | Specifico del sistema? | Sensibile? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Importo minimo | `quote/general/minimum_amount` |  |  |  |
| Messaggio di importo minimo | `quote/general/minimum_amount_message` |  |  |  |
| Periodo di scadenza predefinito | `quote/general/default_expiration_period` |  |  |  |
| Formati di file da caricare | `quote/attached_files/file_formats` |  |  |  |
| Dimensione massima del file | `quote/attached_files/maximum_file_size` |  |  |  |
| Importo minimo | `quote/general/minimum_amount` |  |  |  |
| Messaggio di importo minimo | `quote/general/minimum_amount_message` |  |  |  |
| Periodo di scadenza predefinito | `quote/general/default_expiration_period` |  |  |  |
| Formati di file da caricare | `quote/attached_files/file_formats` |  |  |  |
| Dimensione massima del file | `quote/attached_files/maximum_file_size` |  |  |  |

{style=&quot;table-layout:auto&quot;}

## Percorsi del metodo di pagamento

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento**.

>[!INFO]
>
>I percorsi disponibili sono determinati dalla scelta del Paese Merchant.

| Nome | Percorso di configurazione | Crittografato? | Specifico del sistema? | Sensibile? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Abilitato | `payment/au/companycredit/active` |  |  |  |
| Titolo | `payment/au/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/au/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/au/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/au/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/au/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/au/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/au/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/es/companycredit/active` |  |  |  |
| Titolo | `payment/es/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/es/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/es/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/es/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/es/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/es/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/es/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/companycredit/active` |  |  |  |
| Titolo | `payment/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/nz/companycredit/active` |  |  |  |
| Titolo | `payment/nz/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/nz/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/nz/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/nz/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/nz/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/nz/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/nz/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/us/companycredit/active` |  |  |  |
| Titolo | `payment/us/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/us/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/us/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/us/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/us/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/us/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/us/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/gb/companycredit/active` |  |  |  |
| Titolo | `payment/gb/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/gb/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/gb/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/gb/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/gb/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/gb/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/gb/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/de/companycredit/active` |  |  |  |
| Titolo | `payment/de/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/de/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/de/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/de/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/de/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/de/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/de/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/other/companycredit/active` |  |  |  |
| Titolo | `payment/other/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/other/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/other/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/other/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/other/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/other/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/other/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/ca/companycredit/active` |  |  |  |
| Titolo | `payment/ca/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/ca/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/ca/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/ca/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/ca/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/ca/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/ca/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/hk/companycredit/active` |  |  |  |
| Titolo | `payment/hk/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/hk/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/hk/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/hk/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/hk/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/hk/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/hk/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/jp/companycredit/active` |  |  |  |
| Titolo | `payment/jp/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/jp/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/jp/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/jp/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/jp/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/jp/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/jp/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/fr/companycredit/active` |  |  |  |
| Titolo | `payment/fr/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/fr/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/fr/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/fr/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/fr/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/fr/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/fr/companycredit/sort_order` |  |  |  |
| Abilitato | `payment/it/companycredit/active` |  |  |  |
| Titolo | `payment/it/companycredit/title` |  |  |  |
| Nuovo stato ordine | `payment/it/companycredit/order_status` |  |  |  |
| Pagamento da paesi candidati | `payment/it/companycredit/allowspecific` |  |  |  |
| Pagamento da paesi specifici | `payment/it/companycredit/specificcountry` |  |  |  |
| Totale ordine minimo | `payment/it/companycredit/min_order_total` |  |  |  |
| Totale ordine | `payment/it/companycredit/max_order_total` |  |  |  |
| Ordinamento | `payment/it/companycredit/sort_order` |  |  |  |

{style=&quot;table-layout:auto&quot;}
