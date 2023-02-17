---
title: Security.txt
description: Scopri come fornire informazioni per aiutare i ricercatori sulla sicurezza a segnalare le vulnerabilità.
badge: label="Contributo di Kalpesh Mehta da Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# File TXT di sicurezza

Quando i ricercatori scoprono vulnerabilità di sicurezza, spesso mancano canali di reporting adeguati. Di conseguenza, alcune vulnerabilità non vengono segnalate. Lo scopo del `security.txt` [formato file](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) file è quello di fornire ai ricercatori di sicurezza le informazioni che possono utilizzare per segnalare i loro risultati.

I commercianti possono inserire le loro informazioni di contatto per [segnalazione di problemi di sicurezza](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) da Commerce _Amministratore_. Per gli sviluppatori, la `Magento_Securitytxt` Il modulo fornisce le seguenti funzionalità:

- Consente di salvare le configurazioni di sicurezza dal _Amministratore_.
- Contiene un router per far corrispondere la classe di azione dell&#39;applicazione per le richieste al `.well-known/security.txt` e `.well-known/security.txt.sig` file.
- Distribuisce il contenuto del `.well-known/security.txt` e `.well-known/security.txt.sig` file.

Una valida `security.txt` il file potrebbe avere un aspetto simile al seguente:

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
