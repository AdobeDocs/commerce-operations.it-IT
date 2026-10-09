---
title: Security.txt
description: Scopri come fornire informazioni per aiutare i ricercatori di sicurezza a segnalare le vulnerabilità.
feature: Configuration, Security
badge: label="Contribuito da Kalpesh Mehta di Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# File TXT di protezione

Quando i ricercatori scoprono delle vulnerabilità di sicurezza, spesso mancano i canali di segnalazione appropriati. Di conseguenza, alcune vulnerabilità non vengono segnalate. Lo scopo del file `security.txt` [formato file](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) è quello di fornire ai ricercatori della sicurezza le informazioni che possono utilizzare per segnalare i risultati.

Gli esercenti possono immettere le informazioni di contatto per [segnalazione dei problemi di sicurezza](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/security-issue-reporting) da Commerce _Amministratore_. Per gli sviluppatori, il modulo `Magento_Securitytxt` fornisce le funzionalità seguenti:

- Consente di salvare le configurazioni di sicurezza da _Admin_.
- Contiene un router che corrisponde alla classe di azione dell&#39;applicazione per le richieste ai file `.well-known/security.txt` e `.well-known/security.txt.sig`.
- Distribuisce il contenuto dei file `.well-known/security.txt` e `.well-known/security.txt.sig`.

Un file `security.txt` valido potrebbe avere l&#39;aspetto seguente:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Per creare il file della firma `security.txt` (`security.txt.sig`):

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Per verificare la firma:

```shell
gpg --verify security.txt.sig security.txt
```
