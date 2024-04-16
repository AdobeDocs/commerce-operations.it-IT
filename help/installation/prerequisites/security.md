---
title: Sicurezza dell'installazione locale
description: Scopri come migliorare la postura di sicurezza dell’installazione on-premise di Adobe Commerce o di Magento Open Source.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Sicurezza dell&#39;installazione locale

[Sicurezza Linux avanzata (SELinux)](https://selinuxproject.org/page/Main_Page) consente agli amministratori di CentOS e Ubuntu un maggiore controllo dell&#39;accesso ai propri server. Se si utilizza SELinux *e* Apache deve avviare una connessione a un altro host. È necessario eseguire i comandi descritti in questa sezione.

>[!NOTE]
>
>L’Adobe non contiene consigli sull’utilizzo di SELinux; puoi utilizzarlo per una maggiore sicurezza, se lo desideri. Se utilizzi SELinux, devi configurarlo correttamente oppure Adobe Commerce può funzionare in modo imprevedibile. Se scegli di utilizzare SELinux, consulta una risorsa come [Wiki CentOS](https://wiki.centos.org/HowTos/SELinux) per impostare le regole per abilitare la comunicazione.

## Suggerimenti per l’installazione con Apache

Se si sceglie di attivare SELinux, potrebbero verificarsi problemi durante l&#39;esecuzione del programma di installazione a meno che non si modifichi il *contesto di sicurezza* di alcune directory come segue:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

I comandi precedenti funzionano solo con il server web Apache. A causa della varietà di configurazioni e di requisiti di sicurezza, non garantiamo che questi comandi funzionino in tutte le situazioni. Per ulteriori informazioni, consulta:

* [pagina man](https://linux.die.net/man/8/httpd_selinux)
* [Laboratorio server](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Abilita comunicazione tra server

Se Apache e il server di database si trovano sullo stesso host, utilizza il seguente comando se intendi utilizzare integrazioni che utilizzano `curl` (es. Paypal e USPS).
Per abilitare Apache per avviare una connessione a un altro host con SELinux abilitato:

1. Per determinare se SELinux è abilitato, utilizzare il comando seguente:

   ```bash
   getenforce
   ```

   `Enforcing` viene visualizzato per confermare che SELinux è in esecuzione.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Apertura delle porte nel firewall

A seconda dei requisiti di sicurezza, potrebbe essere necessario aprire la porta 80 e altre porte nel firewall. A causa della natura sensibile della sicurezza della rete, Adobe consiglia vivamente di consultare il reparto IT prima di procedere. Di seguito sono riportati alcuni riferimenti suggeriti:

* Ubuntu: [Pagina della documentazione di Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [Procedure relative a CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
