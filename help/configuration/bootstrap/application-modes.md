---
title: Modalità di applicazione
description: L’applicazione Commerce può funzionare in diverse modalità in base alle tue esigenze. Visualizzare un elenco dettagliato delle modalità di applicazione disponibili.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Modalità di applicazione

Puoi eseguire l’applicazione Commerce in uno dei seguenti modi _modalità_:

| Nome modalità | Descrizione | Supporto cloud |
| ------------------------ | ------------------- | ------------- |
| [predefinito](#default-mode) | Distribuisci ed esegui l’applicazione Commerce su un singolo server senza modificare le impostazioni. _Not_ ottimizzato per la produzione. | no |
| [sviluppatore](#developer-mode) | Ideale per lo sviluppo nell’estensione o personalizzazione dell’applicazione Commerce. | no |
| [produzione](#production-mode) | Distribuire ed eseguire l’applicazione Commerce in un sistema di produzione. | Sì |
| [manutenzione](#maintenance-mode) | Impedisci l’accesso a un sito durante l’esecuzione di aggiornamenti e configurazioni. | Sì |

Consulta [Impostare la modalità operativa](../cli/set-mode.md) per scoprire come modificare manualmente le modalità operative di Adobe Commerce.

## Supporto cloud

Non è necessario gestire le modalità di applicazione per un progetto di infrastruttura cloud. A causa del file system di sola lettura, non è possibile modificare le modalità negli ambienti cloud remoti. Adobe Commerce su infrastruttura cloud esegue automaticamente l’applicazione in _manutenzione_ modalità durante una distribuzione, che porta il sito offline fino al completamento della distribuzione. In caso contrario, l’applicazione rimane in _produzione_ modalità. Consulta [Processo di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) nel _Guida di Commerce su infrastruttura cloud_.

Se utilizzi Cloud Docker for Commerce come strumento di sviluppo, puoi distribuire il progetto di infrastruttura cloud in un ambiente Docker in _sviluppatore_ ma le prestazioni sono più lente a causa di operazioni aggiuntive di sincronizzazione dei file. Consulta [Distribuire l’ambiente Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) nel _Guida a Cloud Docker per Commerce_.

## Modalità predefinita

Il _predefinito_ La modalità consente di distribuire l’applicazione Commerce su un singolo server senza modificare le impostazioni. Tuttavia, la modalità predefinita non è ottimizzata per la produzione a causa dell’impatto negativo sulle prestazioni dei file statici. La creazione e la memorizzazione nella cache di file statici ha un impatto maggiore sulle prestazioni rispetto alla generazione di tali file mediante lo strumento di creazione di file statici.

In modalità predefinita:

- Le eccezioni vengono scritte in file di registro anziché in visualizzazione
- I file delle viste statiche sono memorizzati nella cache
- Nasconde gli elementi personalizzati `X-Magento-*` Intestazioni di richieste e risposte HTTP

Commerce funziona in modalità predefinita se non è specificata alcuna altra modalità.

## Modalità sviluppatore

Il _sviluppatore_ è consigliata per estendere e personalizzare l’applicazione Commerce. I file di visualizzazione statica non vengono memorizzati in cache, ma scritti in `pub/static` directory on-demand.

In modalità sviluppatore:

- Abilita [compilazione automatica del codice](../cli/code-compiler.md) e debug avanzato
- Le eccezioni non rilevate vengono visualizzate nel browser
- Accesso al sistema `var/report` è dettagliato
- Nel gestore degli errori viene generata un&#39;eccezione, anziché essere registrata
- Viene generata un&#39;eccezione quando non è possibile richiamare un sottoscrittore di eventi
- Mostra personalizzati `X-Magento-*` Intestazioni di richieste e risposte HTTP

## Modalità di produzione

Il _produzione_ è la modalità migliore per distribuire l’applicazione Commerce su un sistema di produzione. Dopo aver ottimizzato l’ambiente del server, ad esempio il database e il server web, è necessario eseguire il comando [strumento di distribuzione dei file di visualizzazione statica](../cli/static-view-file-deployment.md) per scrivere file di visualizzazione statica in `pub/static` directory. Questo migliora le prestazioni fornendo tutti i file statici necessari durante la distribuzione invece di forzare l’applicazione Commerce a individuare e copiare dinamicamente (materializzare) i file statici su richiesta durante il runtime.

Alcuni campi, come le sezioni di configurazione del sistema Avanzate e Sviluppatori nell’Admin, non sono disponibili in modalità di produzione. Ad esempio, puoi _non può_ abilita o disabilita i tipi di cache utilizzando l’amministratore. Puoi abilitare e disabilitare i tipi di cache _solo_ utilizzando [riga di comando](../cli/manage-cache.md#config-cli-subcommands-cache-en).

In modalità di produzione:

- I file di visualizzazione statica vengono forniti solo dalla cache
- Gli errori e le eccezioni vengono registrati nel file system e non vengono mai visualizzati all&#39;utente
- Alcuni campi di configurazione nell’Amministratore non sono disponibili

## Modalità di manutenzione

Il _manutenzione_ La modalità limita o impedisce l’accesso a un sito durante miglioramenti, aggiornamenti e attività di configurazione. Per impostazione predefinita, il sito reindirizza i visitatori a un `Service Temporarily Unavailable` pagina.

Puoi creare una [pagina manutenzione personalizzata](../../upgrade/troubleshooting/maintenance-mode-options.md), abilita e disabilita manualmente la modalità di manutenzione e configura la modalità di manutenzione per consentire ai visitatori di indirizzi IP autorizzati di visualizzare lo store normalmente. Consulta [attivare e disattivare la modalità di manutenzione](../../installation/tutorials/maintenance-mode.md) nel _Guida all’installazione_.

Se utilizzi Commerce su un’infrastruttura cloud, l’applicazione Commerce viene eseguita in modalità di manutenzione durante la fase di distribuzione. Al termine della distribuzione, l’applicazione Commerce torna in esecuzione in modalità di produzione. Consulta [Hook di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) nel _Guida di Commerce su infrastruttura cloud_.

In modalità di manutenzione:

- I visitatori del sito vengono reindirizzati a un valore predefinito `Service Temporarily Unavailable` pagina
- Il `var/` la directory contiene `.maintenance.flag` file
- Puoi limitare l’accesso dei visitatori in base agli indirizzi IP
