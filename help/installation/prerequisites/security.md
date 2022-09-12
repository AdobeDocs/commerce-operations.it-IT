---
title: Sicurezza dell'installazione in loco
description: Scopri come migliorare la postura di sicurezza dell’installazione on-premise di Adobe Commerce o Magenti Open Source.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Sicurezza dell&#39;installazione in loco

[Sicurezza Enhanced Linux (SELinux)](https://selinuxproject.org/page/Main_Page) consente agli amministratori di CentOS e Ubuntu di avere un maggiore controllo degli accessi sui propri server. Se utilizzi SELinux *e* Apache deve avviare una connessione a un altro host. È necessario eseguire i comandi descritti in questa sezione.

>[!NOTE]
>
>Adobe non consiglia di utilizzare SELinux; è possibile utilizzarlo per migliorare la sicurezza, se lo si desidera. Se utilizzi SELinux, devi configurarlo correttamente oppure il Magento Open Source e Adobe Commerce possono funzionare in modo imprevedibile. Se scegli di utilizzare SELinux, consulta una risorsa come la [Wiki CentOS](https://wiki.centos.org/HowTos/SELinux) per impostare regole che consentano la comunicazione.

## Suggerimenti per l’installazione con Apache

Se si sceglie di abilitare SELinux, potrebbero verificarsi problemi durante l&#39;esecuzione del programma di installazione, a meno che non si modifichi il *contesto di sicurezza* di alcune directory come segue:

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

I comandi precedenti funzionano solo con il server web Apache. A causa della varietà di configurazioni e requisiti di sicurezza, non garantiamo che questi comandi funzionino in tutte le situazioni. Per ulteriori informazioni, consulta:

* [pagina man](https://linux.die.net/man/8/httpd_selinux)
* [Laboratorio server](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Abilitare la comunicazione tra server

Se Apache e il server di database si trovano sullo stesso host, utilizza il comando seguente se intendi utilizzare integrazioni che utilizzano `curl` (ex Paypal e USPS).
Per abilitare Apache ad avviare una connessione a un altro host con SELinux abilitato:

1. Per determinare se SELinux è abilitato, utilizza il comando seguente:

   ```bash
   getenforce
   ```

   `Enforcing` visualizza per confermare che SELinux è in esecuzione.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Apertura di porte nel firewall

A seconda dei requisiti di sicurezza, potrebbe essere necessario aprire la porta 80 e altre porte nel firewall. A causa della delicatezza della sicurezza della rete, l&#39;Adobe consiglia vivamente di consultare il reparto IT prima di procedere. Di seguito sono riportati alcuni riferimenti suggeriti:

* Ubuntu: [Pagina della documentazione di Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [Procedura dettagliata per CentOS](https://wiki.centos.org/HowTos/Network/IPTables).
