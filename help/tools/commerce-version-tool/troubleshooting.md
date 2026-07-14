---
title: Risoluzione dei problemi di [!DNL Commerce Version Tool]
description: Scopri come risolvere i problemi relativi al rilevamento del compositore [!DNL Commerce Version Tool] , alle verifiche interne di esecuzione in prova, alla cache del Registro di sistema, all'output JSON e ai problemi del registro di controllo.
TQID: 'https://experienceleague.adobe.com/JwRSy7pfM89WoifYUzTVPhR-WrDIvj2A2B8SaEnmyWM'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: eafe79321da03f4778dd9e1b290141ef082a5eaf
workflow-type: tm+mt
source-wordcount: 1222
ht-degree: 0%

---

# Risoluzione dei problemi di [!DNL Commerce Version Tool]

Utilizzare questa pagina per risolvere i problemi comuni di [!DNL Commerce Version Tool] ([!DNL CVT]) relativi al rilevamento del Compositore, al caricamento del Registro di sistema, al rilevamento di patch interne di esecuzione in prova, alla generazione dell&#39;output e alla registrazione di controllo.

## Passaggi per la risoluzione rapida dei problemi

Se lo strumento [!DNL CVT] non restituisce il report sullo stato patch previsto:

- Conferma che l’installazione di destinazione utilizzi una versione e un’edizione di Adobe Commerce supportate.
- Verificare che `composer.lock` sia presente e che corrisponda all&#39;ambiente da controllare.
- Verificare che PHP e il file binario di sistema `patch` siano disponibili.
- Verificare che [!DNL CVT] sia in grado di leggere il file del Registro di sistema della patch.
- Rivedi `warnings`, `missing_patches` e `unknown_patches` nell&#39;output.
- Se il file di registro è stato creato, controllare `var/log/patch_status.log` per il riepilogo dei controlli dall&#39;esecuzione.

>[!TIP]
>
> Il file di registro è utile quando è necessario capire perché non è stato possibile classificare una patch. Per ogni patch sconosciuta, il registro registra l’output non elaborato dei tentativi di esecuzione in avanti e all’indietro, compresi eventuali errori o errori di ricerca.
>
> In caso di problemi durante il recupero dei file del Registro di sistema o delle patch, controllare il campo avvertenze nel report. Tali dettagli non vengono visualizzati nel registro.

## Problemi e soluzioni comuni

### Impossibile rilevare la versione di base

Se lo strumento [!DNL CVT] non è in grado di trovare la versione base di Adobe Commerce, verificare le condizioni seguenti:

**Verifica:**

- Manca `composer.lock`.
- Il comando `patch-status` è in esecuzione all&#39;esterno della directory principale del progetto Adobe Commerce (o `--root` punta al percorso errato), quindi `composer.lock` non è stato trovato.
- `composer.lock` esiste ma non è un JSON valido o non può essere letto.
- `composer.lock` non contiene nessuno dei pacchetti di base riconosciuti (`magento/product-enterprise-edition`, `magento/product-community-edition`, `magento/magento2-base`).

**Messaggi di avviso:**

Se `composer.lock` esiste ma è illeggibile, non analizzabile o non contiene un pacchetto di base riconosciuto, lo strumento emette una delle seguenti stringhe nel campo di output degli avvisi:

```shell-session
No recognized Commerce base package found in composer.lock
composer.lock exists but could not be read
composer.lock could not be parsed as JSON
```

>[!NOTE]
>
> Se `composer.lock` manca completamente, lo strumento segnala `base_version: "unknown"` con **nessun messaggio di avviso**. Controlla sempre `base_version` direttamente nell&#39;output. Non fare affidamento sulla presenza di un avviso per trovare questo problema.

Una qualsiasi delle condizioni precedentemente menzionate indica che lo strumento non è in grado di rilevare la versione di base. Lo strumento esce con il codice `1` e non viene eseguito il rilevamento delle patch.

**Azioni:**

- Eseguire il comando `patch-status` dalla directory principale del progetto [!DNL Adobe Commerce] oppure passare il `--root` corretto.
- Verificare che `composer.lock` sia presente, corrente e valido.
- Verificare che l&#39;installazione utilizzi un&#39;edizione di Adobe Commerce supportata in modo che `composer.lock` contenga uno dei pacchetti di base riconosciuti.

### Nessuna patch applicabile alla versione installata

Se [!DNL CVT] segnala un `base_version` valido ma `applied_patches`, `missing_patches` e `unknown_patches` sono vuoti, la versione installata non è inclusa nel Registro di sistema della patch corrente.

**Verifica:**

- La versione [!DNL Adobe Commerce] installata non è rappresentata nel file del Registro di sistema delle patch. Ad esempio, una versione più recente delle voci più recenti del Registro di sistema.

**Messaggi di avviso:**

```shell-session
No patches found in registry for installed component versions (CE=2.4.7-p9)
```

Questo avviso è diverso da &quot;Impossibile rilevare la versione di base&quot;. `base_version` è corretto, lo strumento esce da `0` e nel Registro di sistema non è presente alcun elemento con cui eseguire il confronto.

**Azioni:**

- Conferma `base_version` nell&#39;output come previsto.
- Confermare che `registry_source` è `remote` o un `cache` recente, non uno non aggiornato.
- Contatta il supporto Adobe Commerce se la versione deve già essere coperta.

### Impossibile recuperare il registro delle patch

Se lo strumento [!DNL CVT] non è in grado di recuperare il file del Registro di sistema della patch più recente, controllare le impostazioni di rete e della cache:

**Verifica:**

- Rete non disponibile.
- Timeout della richiesta dell’endpoint della patch di Adobe.
- `--no-cache` utilizzato e impossibile raggiungere il Registro di sistema remoto.
- `PATCH_REGISTRY_URL` punta a un Registro di sistema non disponibile o non è un URL HTTPS valido.
- Se lo strumento [!DNL CVT] non è in grado di recuperare il file del Registro di sistema della patch più recente, controllare le impostazioni di rete e della cache:

>[!NOTE]
>
>Se il file del Registro di sistema risulta mancante o scaduto, lo strumento scarica il Registro di sistema più recente dall&#39;host remoto.

**Messaggi di avviso:**

Lo strumento emette le seguenti stringhe nel campo di output avvertenze per questo scenario:

```shell-session
Remote registry fetch failed (HTTP 403). Check PATCH_REGISTRY_URL (if set) and network connectivity.
Remote registry response was not valid JSON; ignoring.
Could not load remote registry. Using cached registry (3 hours old). CVE coverage may be incomplete.
Patch registry could not be loaded.
Could not fetch remote registry and --no-cache was set; aborting.
```

Il messaggio cache non aggiornata include la durata effettiva in ore, ad esempio `(3 hours old)`.

Gli avvisi `patch registry could not be loaded` e `could not fetch remote registry` indicano che lo strumento è uscito senza eseguire il rilevamento delle patch.

**Azioni:**

- Eseguire nuovamente il comando `patch-status` quando la connettività di rete è disponibile.
- Consenti allo strumento [!DNL CVT] di utilizzare il Registro di sistema memorizzato nella cache se per l&#39;analisi è accettabile un avviso di cache non aggiornato.
- Rimuovere `--no-cache` a meno che non siano necessari nuovi recuperi remoti.
- Verificare che lo strumento [!DNL CVT] possa scrivere in `var/patch_metadata/` se si desidera riutilizzare la cache del Registro di sistema.

### Impossibile recuperare o verificare le differenze di patch

Se lo strumento [!DNL CVT] non è in grado di testare una o più patch applicabili, controllare l&#39;accesso con differenze di patch:

**Verifica:**

- Impossibile scaricare una differenza di patch dall’endpoint di patch Adobe.
- Credenziali richieste per i download di patch autenticate mancanti o non valide.
- `PATCH_DIFF_BASE_URL` punta a un&#39;origine diff patch non disponibile o non è un URL HTTPS valido.
- La differenza di patch memorizzata nella cache è mancante o non leggibile.
- La verifica SHA-256 non riesce per una patch scaricata diff.
- Lo strumento [!DNL CVT] non può scrivere in `var/patch_metadata/.patch_diffs/`.

**Messaggi di avviso:**

Lo strumento emette le seguenti stringhe nel campo di output avvertenze per questo scenario:

```shell-session
Patch 247p9-2026-05-001-EE requires authentication. Set credentials via COMPOSER_AUTH or auth.json.
Could not fetch patch 247p9-2026-05-001-EE (HTTP 401). Check credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch 247p9-2026-05-001-EE (HTTP 404).
Could not fetch or verify patch 247p9-2026-05-001-EE. Check network connectivity and credentials (COMPOSER_AUTH / auth.json).
Could not fetch patch file for 247p9-2026-05-001-EE.
SHA-256 verification failed for patch 247p9-2026-05-001-EE; discarding download.
```

L&#39;ID patch in ogni messaggio corrisponde all&#39;ID effettivo della voce del Registro di sistema, ad esempio `247p9-2026-05-001-EE`. `SHA-256 verification failed` indica che un file patch scaricato di recente non corrisponde al checksum previsto. Lo strumento lo elimina senza memorizzare in cache e classifica la patch `unknown` per questa esecuzione. È stata rilevata una voce danneggiata della cache *local* che viene recuperata automaticamente nella stessa esecuzione senza alcun avviso. In entrambi i casi, non è necessaria alcuna pulizia manuale della cache.

**Azioni:**

- Confermare la connettività di rete e riprovare.
- Confermare che le credenziali richieste per i download delle patch autenticate siano configurate.
- Verificare che lo strumento [!DNL CVT] possa scrivere in `var/patch_metadata/.patch_diffs/`.
- Se la patch rimane classificata come sconosciuta, mantieni i dettagli di avvertenza e output.

### Vengono segnalate patch mancanti o sconosciute

Se il report contiene valori `missing_patches` o `unknown_patches` imprevisti, esaminare i dettagli di installazione e di output:

**Verifica:**

- Le patch mensili sono state applicate fuori sequenza.
- Manca una patch specifica di un componente, ad esempio Adobe Commerce business-to-business (B2B) o Adobe Commerce Page Builder.
- `composer.lock` segnala una versione di componente installata che richiede la patch.
- Una differenza di patch non è disponibile o il risultato del rilevamento non è conclusivo.

**Messaggi di avviso:**

Lo strumento emette le seguenti stringhe nel campo di output avvertenze per questo scenario:

```shell-session
No file_name or sha256 for 247p9-2026-05-001-EE
Registry entry '247p9-2026-05-001-EE' requires unknown patch '247p9-2026-04-001-EE'; skipping.
descendant diffs unavailable for 247p9-2026-06-001-EE; dry-run for 247p9-2026-05-001-EE may be inaccurate
Failed to reverse-apply 247p9-2026-06-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
Failed to forward-apply prerequisite 247p9-2026-04-001-EE when preparing dry-run for 247p9-2026-05-001-EE; result may be inaccurate
```

Quando `may be inaccurate` viene visualizzato in un avviso, il controllo di prova viene comunque eseguito, ma con un&#39;affidabilità ridotta. La patch può essere comunque categorizzata in `applied_patches` o `missing_patches`, non necessariamente in `unknown_patches`.

Per le patch sconosciute in particolare, `var/log/patch_status.log` registra l&#39;output di esecuzione a secco della patch non elaborato (avanti e indietro), che indica quali file e blocchi non corrispondono.

Se viene visualizzato l&#39;avviso &quot;Nessuna patch trovata&quot;, consultare [nessuna patch applicata alla versione installata](#no-patches-apply-to-the-installed-version).

**Azioni:**

- Esaminare i campi `applied_patches`, `missing_patches` e `unknown_patches`.
- Verificare che le patch mancanti siano valide per l&#39;edizione e i componenti installati.
- Confrontare il risultato con le relative note sulla versione della patch di sicurezza.
- Verifica che la base di codice ispezionata corrisponda all’ambiente distribuito su cui intendi creare un rapporto.
- Contatta il supporto Adobe Commerce se lo stato sconosciuto blocca la pianificazione della correzione.

### L’output non viene generato

Se lo strumento [!DNL CVT] viene completato ma manca l&#39;output JSON o CSV previsto, controllare la sintassi del comando e l&#39;output del terminale:

**Azioni:**

- Se non è richiesto l’output CSV, utilizza l’output JSON predefinito.
- Utilizza `--format=csv` per generare l&#39;output CSV.
- Verificare che l&#39;output del comando non venga reindirizzato o eliminato dalla shell, dallo script o dallo scanner che esegue lo strumento [!DNL CVT].
- Controlla `stderr` per `patch-status:` messaggi di errore.
- Se si reindirizza l&#39;output in un file, ad esempio `patch-status > report.json`, confermare che la shell disponga dell&#39;autorizzazione di scrittura per tale destinazione. Lo strumento scrive solo in `stdout`.
- Verificare che lo strumento [!DNL CVT] possa scrivere in `var/log/patch_status.log`.
- Eseguire nuovamente il comando e acquisire l&#39;output del terminale per la risoluzione dei problemi.

## Ottenere aiuto

Quando si contatta il supporto Adobe Commerce, fornire solo i dettagli necessari per analizzare il problema.

Includi:

- Versione ed edizione di Adobe Commerce
- Versione dello strumento [!DNL CVT]
- Origine del Registro di sistema dall&#39;output dello strumento [!DNL CVT]
- Valori `applied_patches`, `missing_patches` e `unknown_patches` rilevanti
- Avvertenze pertinenti
- Messaggio di errore o output comando

Non includere segreti, credenziali, chiavi private o dati cliente non correlati in registri o allegati condivisi.

## Argomenti correlati

- [Introduzione](intro.md)
- [Generare un rapporto sullo stato delle patch](generate-report.md)
- [Note sulla versione](release-notes.md)
