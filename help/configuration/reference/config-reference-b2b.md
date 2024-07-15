---
title: Riferimento ai percorsi di configurazione dell’estensione B2B
description: Consulta un elenco di valori di configurazione relativi a B2B.
feature: Configuration, B2B, Companies, Payments, Quotes
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Riferimento ai percorsi di configurazione dell’estensione B2B

_Disponibile per le istanze con B2B per Adobe Commerce installato._

In questo argomento sono elencati i percorsi di configurazione per l’estensione B2B di Commerce Enterprise. Il comando [`magento app:config:dump`](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente.

>[!INFO]
>
>Questo riferimento elenca _solo_ percorsi di configurazione univoci per B2B per Adobe Commerce. Questa estensione include tutti i percorsi di configurazione per Adobe Commerce.

Per i percorsi di configurazione, vedi:

- [Percorsi di configurazione del pagamento](config-reference-payment.md)
- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)

Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedere [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables).

## Categoria generale

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### Percorsi di funzionalità B2B

Questi valori di configurazione sono disponibili nell&#39;Admin in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Nome | Percorso configurazione | Crittografato? | Specifico per il sistema? | Sensibili? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Abilita società | `btob/website_configuration/company_active` | | | |
| Abilita catalogo condiviso | `btob/website_configuration/sharedcatalog_active` | | | |
| Abilita offerta B2B | `btob/website_configuration/negotiablequote_active` | | | |
| Abilita ordine rapido | `btob/website_configuration/quickorder_active` | | | |
| Abilita elenco richieste di acquisto | `btob/website_configuration/requisition_list_active` | | | |
| Metodi di pagamento applicabili | `btob/default_b2b_payment_methods/applicable_payment_methods` | | | |
| Metodi di pagamento | `btob/default_b2b_payment_methods/available_payment_methods` | | | |

{style="table-layout:auto"}

## Categoria di clienti

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Percorsi di configurazione società

Questi valori di configurazione sono disponibili nell&#39;Admin in **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Nome | Percorso configurazione | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|
| Consenti registrazione società da vetrina | `company/general/allow_company_registration` | | | |
| Destinatario e-mail registrazione società | `company/email/company_registration` | | | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia la copia dell&#39;e-mail di registrazione della società a | `company/email/company_registration_copy` | | | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Metodo Send Email Copy | `company/email/company_copy_method` | | | |
| E-mail di registrazione società predefinita | `company/email/company_notify_admin_template` | | | |
| E-mail relative al cliente | `company/email/heading_customer` | | | |
| E-mail assegnata rappresentante commerciale predefinito | `company/email/customer_sales_representative_template` | | | |
| E-mail predefinita Assegna società al cliente | `company/email/customer_company_customer_assign_template` | | | |
| E-mail predefinita per l’amministratore della società | `company/email/customer_assign_super_user_template` | | | |
| E-mail inattiva amministrazione società predefinita | `company/email/customer_inactivate_super_user_template` | | | |
| L&#39;Amministratore Predefinito Della Società È Diventato Membro E-Mail | `company/email/customer_remove_super_user_template` | | | |
| E-mail attiva stato cliente predefinito | `company/email/customer_account_activated_template` | | | |
| E-mail con stato cliente inattivo predefinito | `company/email/customer_account_locked_template` | | | |
| Modifica stato società | `company/email/heading_company_status` | | | |
| Destinatario e-mail per modifica stato società | `company/email/company_status_change` | | | |
| Invia copia e-mail per modifica stato società a | `company/email/company_status_change_copy` | | | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Metodo Send Email Copy | `company/email/company_status_copy_method` | | | |
| Stato Predefinito Azienda Cambiato In Attivo 1 E-Mail | `company/email/company_status_pending_approval_to_active_template` | | | |
| Lo Stato Predefinito Della Società È Stato Impostato Su Active 2 Email | `company/email/company_status_rejected_blocked_to_active_template` | | | |
| Stato Predefinito Azienda Cambiato In E-Mail Rifiutata | `company/email/company_status_rejected_template` | | | |
| Modifica Predefinita Dello Stato Della Società In E-Mail Bloccata | `company/email/company_status_blocked_template` | | | |
| Modifica Stato Predefinito Azienda All&#39;E-Mail Di Approvazione In Sospeso | `company/email/company_status_pending_approval_template` | | | |
| Credito società | `company/email/heading_company_credit` | | | |
| Mittente e-mail per modifica credito società | `company/email/company_credit_change` |  | | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail per modifica credito società a | `company/email/company_credit_change_copy` | | | |
| Metodo Send Email Copy | `company/email/company_credit_copy_method` | | | |
| Modello e-mail allocato | `company/email/credit_allocated_email_template` | | | |
| Modello e-mail aggiornato | `company/email/credit_updated_email_template` | | | |
| Modello e-mail rimborsato | `company/email/credit_reimbursed_email_template` | | | |
| Modello e-mail rimborsato | `company/email/credit_refunded_email_template` | | | |
| Modello e-mail ripristinato | `company/email/credit_reverted_email_template` | | | |

{style="table-layout:auto"}

### La richiesta elenca i percorsi

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Clienti** > **Elenchi richieste di acquisto**.

| Nome | Percorso configurazione | Crittografato? | Specifico per il sistema? | Sensibili? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Numero di elenchi di richieste | `requisitionlist/general/number_requisition_lists` | | | |

{style="table-layout:auto"}

## Categoria di vendita

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite**.

### Percorsi e-mail vendite

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **E-mail vendite**.

| Nome | Percorso configurazione | Crittografato? | Specifico per il sistema? | Sensibili? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Abilitato | `sales_email/quote/enabled` | | | |
| Modello offerta aggiornato (all&#39;acquirente) | `sales_email/quote/updated_buyer_template` | | | |
| Modello offerta rifiutata (all&#39;acquirente) | `sales_email/quote/declined_buyer_template` | | | |
| Nuovo modello offerta (al venditore) | `sales_email/quote/new_seller_template` | | | |
| Modello di preventivo aggiornato (al venditore) | `sales_email/quote/updated_seller_template` | | | |
| Scadenza offerta (in 48 ore) | `sales_email/quote/expire_two_days_template` | | | |
| Scadenza offerta (in 24 ore) | `sales_email/quote/expire_one_day_template` | | | |
| Data di scadenza reimpostata | `sales_email/quote/expire_reset_template` | | | |
| Invia copia e-mail preventivo a | `sales_email/quote/copy_to` | | | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Metodo di invio copia e-mail preventivo | `sales_email/quote/copy_method` | | | |

{style="table-layout:auto"}

### Percorsi virgolette

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Preventivi**.

| Nome | Percorso configurazione | Crittografato? | Specifico per il sistema? | Sensibili? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Importo minimo | `quote/general/minimum_amount` | | | |
| Messaggio Importo minimo | `quote/general/minimum_amount_message` | | | |
| Periodo di scadenza predefinito | `quote/general/default_expiration_period` | | | |
| Formati di file per il caricamento | `quote/attached_files/file_formats` | | | |
| Dimensione massima file | `quote/attached_files/maximum_file_size` | | | |
| Importo minimo | `quote/general/minimum_amount` | | | |
| Messaggio Importo minimo | `quote/general/minimum_amount_message` | | | |
| Periodo di scadenza predefinito | `quote/general/default_expiration_period` | | | |
| Formati di file per il caricamento | `quote/attached_files/file_formats` | | | |
| Dimensione massima file | `quote/attached_files/maximum_file_size` | | | |

{style="table-layout:auto"}

## Percorsi del metodo di pagamento

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento**.

>[!INFO]
>
>I percorsi disponibili sono determinati dalla scelta del Paese del commerciante.

| Nome | Percorso configurazione | Crittografato? | Specifico per il sistema? | Sensibili? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Abilitato | `payment/au/companycredit/active` | | | |
| Titolo | `payment/au/companycredit/title` | | | |
| Stato nuovo ordine | `payment/au/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/au/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/au/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/au/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/au/companycredit/max_order_total` | | | |
| Ordinamento | `payment/au/companycredit/sort_order` | | | |
| Abilitato | `payment/es/companycredit/active` | | | |
| Titolo | `payment/es/companycredit/title` | | | |
| Stato nuovo ordine | `payment/es/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/es/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/es/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/es/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/es/companycredit/max_order_total` | | | |
| Ordinamento | `payment/es/companycredit/sort_order` | | | |
| Abilitato | `payment/companycredit/active` | | | |
| Titolo | `payment/companycredit/title` | | | |
| Stato nuovo ordine | `payment/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/companycredit/max_order_total` | | | |
| Ordinamento | `payment/companycredit/sort_order` | | | |
| Abilitato | `payment/nz/companycredit/active` | | | |
| Titolo | `payment/nz/companycredit/title` | | | |
| Stato nuovo ordine | `payment/nz/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/nz/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/nz/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/nz/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/nz/companycredit/max_order_total` | | | |
| Ordinamento | `payment/nz/companycredit/sort_order` | | | |
| Abilitato | `payment/us/companycredit/active` | | | |
| Titolo | `payment/us/companycredit/title` | | | |
| Stato nuovo ordine | `payment/us/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/us/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/us/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/us/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/us/companycredit/max_order_total` | | | |
| Ordinamento | `payment/us/companycredit/sort_order` | | | |
| Abilitato | `payment/gb/companycredit/active` | | | |
| Titolo | `payment/gb/companycredit/title` | | | |
| Stato nuovo ordine | `payment/gb/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/gb/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/gb/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/gb/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/gb/companycredit/max_order_total` | | | |
| Ordinamento | `payment/gb/companycredit/sort_order` | | | |
| Abilitato | `payment/de/companycredit/active` | | | |
| Titolo | `payment/de/companycredit/title` | | | |
| Stato nuovo ordine | `payment/de/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/de/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/de/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/de/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/de/companycredit/max_order_total` | | | |
| Ordinamento | `payment/de/companycredit/sort_order` | | | |
| Abilitato | `payment/other/companycredit/active` | | | |
| Titolo | `payment/other/companycredit/title` | | | |
| Stato nuovo ordine | `payment/other/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/other/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/other/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/other/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/other/companycredit/max_order_total` | | | |
| Ordinamento | `payment/other/companycredit/sort_order` | | | |
| Abilitato | `payment/ca/companycredit/active` | | | |
| Titolo | `payment/ca/companycredit/title` | | | |
| Stato nuovo ordine | `payment/ca/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/ca/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/ca/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/ca/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/ca/companycredit/max_order_total` | | | |
| Ordinamento | `payment/ca/companycredit/sort_order` | | | |
| Abilitato | `payment/hk/companycredit/active` | | | |
| Titolo | `payment/hk/companycredit/title` | | | |
| Stato nuovo ordine | `payment/hk/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/hk/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/hk/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/hk/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/hk/companycredit/max_order_total` | | | |
| Ordinamento | `payment/hk/companycredit/sort_order` | | | |
| Abilitato | `payment/jp/companycredit/active` | | | |
| Titolo | `payment/jp/companycredit/title` | | | |
| Stato nuovo ordine | `payment/jp/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/jp/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/jp/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/jp/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/jp/companycredit/max_order_total` | | | |
| Ordinamento | `payment/jp/companycredit/sort_order` | | | |
| Abilitato | `payment/fr/companycredit/active` | | | |
| Titolo | `payment/fr/companycredit/title` | | | |
| Stato nuovo ordine | `payment/fr/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/fr/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/fr/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/fr/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/fr/companycredit/max_order_total` | | | |
| Ordinamento | `payment/fr/companycredit/sort_order` | | | |
| Abilitato | `payment/it/companycredit/active` | | | |
| Titolo | `payment/it/companycredit/title` | | | |
| Stato nuovo ordine | `payment/it/companycredit/order_status` | | | |
| Pagamento dai paesi applicabili | `payment/it/companycredit/allowspecific` | | | |
| Pagamento da paesi specifici | `payment/it/companycredit/specificcountry` | | | |
| Totale ordine minimo | `payment/it/companycredit/min_order_total` | | | |
| Totale ordine massimo | `payment/it/companycredit/max_order_total` | | | |
| Ordinamento | `payment/it/companycredit/sort_order` | | | |

{style="table-layout:auto"}
