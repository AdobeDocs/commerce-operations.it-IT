---
title: Generare un rapporto di stato patch
description: Scopri come utilizzare  [!DNL Commerce Version Tool]  per generare rapporti sullo stato delle patch di Adobe Commerce in formato JSON o CSV.
TQID: 'https://experienceleague.adobe.com/-lC-20YMpbTM3tTZjbBO5zD5gb9n7cRah5Ycy8wQoyw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: cb0391ae368b53a795535f3adb636628a339b963
workflow-type: tm+mt
source-wordcount: 590
ht-degree: 2%

---

# Generare un rapporto sullo stato delle patch

Utilizzare [!DNL Commerce Version Tool] ([!DNL CVT]) per generare un report sullo stato delle patch per un&#39;installazione di Adobe Commerce. Il rapporto identifica le patch di sicurezza mensili applicate, mancanti e sconosciute e restituisce l’output JSON per impostazione predefinita.

## Prerequisiti

Prima di eseguire [!DNL CVT], verificare che:

- L’installazione di destinazione utilizza una versione e un’edizione di Adobe Commerce supportate.
- `composer.lock` è presente e corrisponde all&#39;ambiente che si desidera controllare.
- PHP e il file binario di sistema `patch` sono disponibili.
- È possibile leggere i file di progetto dall&#39;ambiente in cui si esegue il comando.
- Lo strumento può scrivere in `var/patch_metadata/` e `var/log/` se si desidera memorizzare i file della cache e le voci del registro di controllo.
- Le credenziali sono disponibili tramite `COMPOSER_AUTH` o `auth.json` se all&#39;installazione si applicano patch gestite dai diritti.

Lo strumento [!DNL CVT] controlla `COMPOSER_AUTH`, il progetto Adobe Commerce `auth.json` e il Compositore globale `auth.json` per verificare le credenziali della patch gestita dall&#39;adesione.

## Generare il rapporto

Dalla directory principale del progetto Adobe Commerce, esegui:

```bash
php vendor/bin/patch-status
```

Per verificare un&#39;altra installazione di Adobe Commerce, utilizzare l&#39;opzione `--root`:

```bash
php vendor/bin/patch-status --root=/path/to/commerce
```

## Opzioni di comando

JSON è il formato di output predefinito. L’output CSV è supportato per scanner, dashboard e rapporti di conformità.

| Opzione | Descrizione |
| --- | --- |
| `--root=PATH` | Specifica il percorso della directory principale di installazione di Adobe Commerce. Il valore di default è la directory corrente. |
| `--format=json\|csv` | Imposta il formato di output. Il valore predefinito è `json`. |
| `--no-cache` | Ignora le cache del Registro di sistema e di differenze tra patch, forza l&#39;aggiornamento delle recuperazioni remote e chiude con un errore se il Registro di sistema remoto non è disponibile. |
| `--version`, `-V` | Stampa la versione dello strumento. |
| `--help`, `-h` | Stampa il messaggio della Guida. |

{style="table-layout:auto"}

## Revisione dell’output JSON e CSV

L’esempio seguente mostra l’output JSON predefinito.

```bash
php vendor/bin/patch-status
```

```json
{
  "base_version": "2.4.7-p9",
  "installed_components": {
    "CE": "2.4.7-p9",
    "EE": "2.4.7-p9",
    "B2B": "1.5.2-p5"
  },
  "applied_patches": [
    "247p9-2026-05-001-CE",
    "247p9-2026-05-001-EE"
  ],
  "missing_patches": [
    "247p9-2026-06-001-CE",
    "247p9-2026-06-001-EE"
  ],
  "unknown_patches": [],
  "vulnerability_status": {
    "CVE-2026-12354": { "status": "PROTECTED" },
    "CVE-2026-67890": { "status": "VULNERABLE" }
  },
  "registry_source": "remote",
  "warnings": []
}
```

Per generare l&#39;output CSV, utilizzare l&#39;opzione `--format=csv`:

```bash
php vendor/bin/patch-status --format=csv
```

L’output CSV produce una riga per CVE ed è adatto per fogli di calcolo, scanner, dashboard e strumenti di conformità.

## Comprendere i risultati del rapporto

Esaminare le patch mancanti e sconosciute prima di effettuare richieste di informazioni sullo stato di protezione.

### Valori dello stato della patch

Il rapporto sullo stato della patch raggruppa i risultati della patch in base ai seguenti valori:

| Stato patch | Significato |
| --- | --- |
| Applicato | Lo strumento [!DNL CVT] rileva la patch di sicurezza mensile nel codebase di Adobe Commerce. |
| Mancante | La patch si applica alla versione o al componente Adobe Commerce installato, ma lo strumento [!DNL CVT] non la rileva. |
| Sconosciuto | Lo strumento non è in grado di confermare lo stato della patch dal Registro di sistema disponibile, da differenze di patch o dal risultato del rilevamento. |

{style="table-layout:auto"}

### Valori di stato CVE

L’output JSON riporta i valori dello stato CVE in lettere maiuscole.

| Stato CVE | Significato |
| --- | --- |
| `PROTECTED` | La patch applicabile viene rilevata per il CVE o il componente. |
| `VULNERABLE` | Manca una patch applicabile per il CVE o il componente. |
| `UNKNOWN` | Lo strumento [!DNL CVT] non è in grado di determinare lo stato CVE dal Registro di sistema e dai dati di rilevamento disponibili. |
| `NOT_APPLICABLE` | Il CVE si applica a un componente non installato, ad esempio Adobe Commerce business-to-business (B2B), Adobe Commerce Page Builder o Adobe Commerce Inventory. |

{style="table-layout:auto"}

### Campi di output chiave

Il rapporto può includere le seguenti informazioni:

- **Versione base Adobe Commerce** - Versione base installata rilevata da `composer.lock`.
- **Origine del Registro di sistema** - Indica se i metadati della patch provengono da `remote`, `cache` o `stale_cache`.
- **Componenti installati** - Aree pacchetto Adobe Commerce rilevate da `composer.lock`.
- **Patch applicate** - Rilevate patch di sicurezza mensili nel codebase di Adobe Commerce.
- **Patch mancanti** - Patch di sicurezza mensili applicabili ma non rilevate.
- **Patch sconosciute** - Patch che lo strumento [!DNL CVT] non può classificare.
- **Stato vulnerabilità da parte di CVE** - CVE con mapping a uno stato protetto, vulnerabile, non applicabile o sconosciuto.
- **Avvisi** - Condizioni che potrebbero influire sull&#39;affidabilità o la completezza del report.

## Registro di sistema e cache delle patch

Il file del Registro di sistema della patch contiene i metadati della patch utilizzati dallo strumento [!DNL CVT] per determinare quali patch applicare a una versione installata. Lo strumento utilizza una nuova cache del Registro di sistema quando disponibile, recupera il Registro di sistema remoto quando necessario e può utilizzare una cache non aggiornata con un avviso se la rete non è disponibile. Utilizzare `--no-cache` solo quando sono necessari nuovi recuperi remoti.

## Argomenti correlati

- [Introduzione](intro.md)
- [Risoluzione dei problemi](troubleshooting.md)
- [Note sulla versione](release-notes.md)
