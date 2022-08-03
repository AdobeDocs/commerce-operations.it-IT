---
title: Modalità di applicazione
description: L’applicazione Commerce può funzionare in modalità diverse a seconda delle tue esigenze. Visualizza un elenco dettagliato delle modalità di applicazione disponibili.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Modalità di applicazione

Puoi eseguire l’applicazione Commerce in uno dei seguenti modi _modalità_:

| Nome modulo | Descrizione |
| ----------- | ----------- |
| default | Consente di distribuire l’applicazione Commerce su un singolo server senza modificare le impostazioni. Tuttavia, la modalità predefinita non è ottimizzata per la produzione.<br>Per distribuire l’applicazione Commerce su più server o ottimizzarla per la produzione, passa a una delle altre modalità.<ul><li>La memorizzazione in cache dei file delle viste statiche è abilitata</li><li>Le eccezioni non vengono visualizzate all&#39;utente; le eccezioni vengono invece scritte nei file di registro.</li><li>Nascondi personalizzato `X-Magento-*` Intestazioni di richiesta e risposta HTTP</li></ul> |
| sviluppatore | Destinata solo allo sviluppo, questa modalità:<ul><li>Disattiva la memorizzazione in cache dei file di visualizzazione statica</li><li>Fornisce la registrazione dettagliata</li><li>Abilita [compilazione automatica del codice](../cli/code-compiler.md)</li><li>Abilita il debug avanzato</li><li>Mostra personalizzati `X-Magento-*` Intestazioni di richiesta e risposta HTTP</li><li>Risultati con prestazioni più lente</li><li>Mostra gli errori sul fronte</li></ul> |
| produzione | Destinata alla distribuzione su un sistema di produzione, questa modalità:<ul><li>Non mostra le eccezioni per l&#39;utente (le eccezioni sono scritte solo nei registri).</li><li>Distribuisce file di visualizzazione statici solo dalla cache.</li><li>Impedisce la compilazione automatica dei file di codice. I file nuovi o aggiornati non vengono scritti nel file system.</li><li>**Non consente di abilitare o disabilitare i tipi di cache nell’amministratore.** Vedi [abilitazione e disabilitazione della cache](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Alcuni campi, come le sezioni di configurazione del sistema Avanzate e Sviluppatore in Admin, non sono disponibili in modalità di produzione.</li></ul> |
| manutenzione | Per impedire l’accesso a un sito durante l’aggiornamento o la riconfigurazione, questa modalità:<ul><li>Reindirizza i visitatori del sito a un valore predefinito `Service Temporarily Unavailable` pagina.</li><li>Quando il sito è in modalità manutenzione, la `var/` la directory contiene `.maintenance.flag` file.</li><li>Puoi configurare la modalità di manutenzione per consentire l’accesso dei visitatori da un elenco specifico di indirizzi IP.</li></ul> |

>[!INFO]
>
>[Adobe Commerce su infrastruttura cloud](https://devdocs.magento.com/cloud/bk-cloud.html) supporta solo le modalità di produzione e manutenzione.

## Modalità predefinita

Come suggerisce il nome, la modalità predefinita è il modo in cui Commerce funziona se non viene specificata un’altra modalità. La modalità predefinita consente di distribuire l’applicazione Commerce su un singolo server senza modificare le impostazioni. Tuttavia, la modalità predefinita non è ottimizzata per la produzione come per la modalità di produzione.

Per distribuire l’applicazione Commerce su più server o ottimizzarla per la produzione, passa a una delle altre modalità.

In modalità predefinita:

- Gli errori vengono registrati nei rapporti sui file sul server e non vengono mai mostrati a un utente
- I file di visualizzazione statica sono memorizzati nella cache
- La modalità predefinita non è ottimizzata per un ambiente di produzione, principalmente a causa dell&#39;impatto negativo sulle prestazioni di [file statici](https://glossary.magento.com/static-files) generato in modo dinamico anziché materializzato. In altre parole, la creazione di file statici e il loro caching hanno un impatto sulle prestazioni maggiore rispetto alla generazione di file utilizzando lo strumento di creazione di file statici.

Vedi [Impostare la modalità operativa](../cli/set-mode.md).

## Modalità Sviluppatore

Esegui l’applicazione Commerce in modalità sviluppatore quando la estendi o la personalizzi.

In modalità sviluppatore:

- I file di visualizzazione statica non sono memorizzati nella cache; sono scritti `pub/static` ogni volta che vengono chiamati
- Le eccezioni non rilevate vengono visualizzate nel browser
- Accesso di sistema `var/report` è dettagliato
- Un [eccezione](https://glossary.magento.com/exception) viene lanciato nel gestore degli errori, anziché essere registrato
- Viene generata un&#39;eccezione quando un [event](https://glossary.magento.com/event) impossibile richiamare

Vedi [Impostare la modalità operativa](../cli/set-mode.md).

## Modalità di produzione

Esegui Commerce in modalità di produzione quando viene distribuito su un server di produzione. Dopo aver ottimizzato l’ambiente server, ad esempio il database e il server web, è necessario eseguire il [strumento di distribuzione file di visualizzazione statica](../cli/static-view-file-deployment.md) per scrivere file di visualizzazione statici in `pub/static` directory.

Ciò migliora le prestazioni fornendo tutti i file statici necessari durante l’implementazione, anziché forzare Commerce a individuare e copiare in modo dinamico i file statici su richiesta durante le fasi di esecuzione.

In modalità di produzione:

- I file di visualizzazione statica non vengono materializzati e gli URL per essi sono composti al volo. I file di visualizzazione statica vengono serviti dal [cache](https://glossary.magento.com/cache) solo.
- Gli errori vengono registrati nel file system e non vengono mai visualizzati all&#39;utente.
- Puoi abilitare e disabilitare i tipi di cache _only_ utilizzando [riga di comando](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- You _impossibile_ abilita o disabilita i tipi di cache utilizzando l’amministratore.

## Modalità di manutenzione

Esegui l’applicazione Commerce in modalità di manutenzione per portare il sito offline mentre completi le attività di manutenzione, aggiornamento o configurazione. In modalità di manutenzione, il sito reindirizza i visitatori a un valore predefinito `Service Temporarily Unavailable` pagina.

Puoi creare una [pagina di manutenzione personalizzata](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html), abilita e disabilita manualmente la modalità di manutenzione e configura la modalità di manutenzione per consentire ai visitatori degli indirizzi IP autorizzati di visualizzare lo store normalmente. Vedi [attiva e disattiva la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

Se utilizzi Commerce sull’infrastruttura cloud, l’applicazione Commerce viene eseguita in modalità di manutenzione durante la fase di implementazione. Al termine della distribuzione, l’applicazione Commerce torna all’esecuzione in modalità di produzione. Vedi [Hook di distribuzione](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) in _Guida alla Commerce Cloud_.
