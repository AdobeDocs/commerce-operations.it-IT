---
title: Security.txt
description: Scopri come fornire informazioni per aiutare i ricercatori di sicurezza a segnalare le vulnerabilità.
feature: Configuration, Security
badge: label="Contribuito da Kalpesh Mehta di Corra" type="Informativo" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# File TXT di protezione

Quando i ricercatori scoprono delle vulnerabilità di sicurezza, spesso mancano i canali di segnalazione appropriati. Di conseguenza, alcune vulnerabilità non vengono segnalate. Scopo della `security.txt` [formato file](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) file è quello di fornire ai ricercatori di sicurezza le informazioni che possono utilizzare per segnalare i loro risultati.

Gli esercenti possono inserire le informazioni di contatto per [segnalazione dei problemi di sicurezza](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) da Commerce _Amministratore_. Per gli sviluppatori, il `Magento_Securitytxt` Il modulo fornisce le seguenti funzionalità:

- Consente di salvare le configurazioni di sicurezza da _Amministratore_.
- Contiene un router che corrisponde alla classe di azione dell&#39;applicazione per le richieste al `.well-known/security.txt` e `.well-known/security.txt.sig` file.
- Distribuisce il contenuto del `.well-known/security.txt` e `.well-known/security.txt.sig` file.

Un valore valido `security.txt` Il file potrebbe avere un aspetto simile al seguente:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Per creare `security.txt` firma (`security.txt.sig`) file:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Per verificare la firma:

```bash
gpg --verify security.txt.sig security.txt
```
