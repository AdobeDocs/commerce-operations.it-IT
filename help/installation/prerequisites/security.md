---
title: Sicurezza dell'installazione locale
description: Scopri come migliorare la postura di sicurezza dell’installazione on-premise di Adobe Commerce.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Sicurezza dell&#39;installazione locale

[Security Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) consente agli amministratori di CentOS e Ubuntu un maggiore controllo dell&#39;accesso ai propri server. Se utilizzi SELinux *e* Apache deve avviare una connessione a un altro host, devi eseguire i comandi descritti in questa sezione.

>[!NOTE]
>
>Adobe non ha consigli sull’utilizzo di SELinux; se lo desideri, puoi utilizzarlo per una maggiore sicurezza. Se utilizzi SELinux, devi configurarlo correttamente oppure Adobe Commerce può funzionare in modo imprevedibile. Se scegli di utilizzare SELinux, consulta una risorsa come [CentOS wiki](https://wiki.centos.org/HowTos/SELinux) per impostare le regole per abilitare la comunicazione.

## Suggerimenti per l’installazione con Apache

Se scegli di abilitare SELinux, potrebbero verificarsi problemi durante l&#39;esecuzione del programma di installazione a meno che non modifichi il *contesto di sicurezza* di alcune directory come segue:

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

Se Apache e il server di database si trovano nello stesso host, utilizzare il comando seguente se si intende utilizzare integrazioni che utilizzano `curl` (ad esempio Paypal e USPS).
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

* Ubuntu: [Pagina documentazione Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [procedure CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
