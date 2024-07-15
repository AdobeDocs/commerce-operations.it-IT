---
title: Modalità di applicazione
description: L'applicazione Commerce può funzionare in modalità diverse a seconda delle esigenze. Visualizzare un elenco dettagliato delle modalità di applicazione disponibili.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 5003e8dcbb3736201ea19ebe30d5e56775096157
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Modalità di applicazione

È possibile eseguire l&#39;applicazione Commerce in una delle _modalità_ seguenti:

| Nome modalità | Descrizione | Supporto cloud |
| ------------------------ | ------------------- | ------------- |
| [predefinito](#default-mode) | Distribuire ed eseguire l&#39;applicazione Commerce su un singolo server senza modificare le impostazioni. _Non_ ottimizzato per la produzione. | no |
| [sviluppatore](#developer-mode) | Ideale per lo sviluppo durante l’estensione o la personalizzazione dell’applicazione Commerce. | no |
| [produzione](#production-mode) | Distribuire ed eseguire l&#39;applicazione Commerce in un sistema di produzione. | Sì |
| [manutenzione](#maintenance-mode) | Impedisci l’accesso a un sito durante l’esecuzione di aggiornamenti e configurazioni. | Sì |

Consulta [Impostare la modalità operativa](../cli/set-mode.md) per scoprire come modificare manualmente le modalità operative di Adobe Commerce.

## Supporto cloud

A causa del file system di sola lettura, non è possibile modificare le modalità negli ambienti cloud remoti. Non tentare di modificare le modalità modificando il file `app/etc/env.php` perché il pacchetto `ece-tools` sovrascrive il file in base a più origini di configurazione.

Adobe Commerce su infrastruttura cloud esegue automaticamente l&#39;applicazione in modalità _manutenzione_ durante una distribuzione, che disconnette il sito fino al completamento della distribuzione. In caso contrario, l&#39;applicazione rimane in modalità _produzione_. Consulta [Processo di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) nella _guida di Commerce sull&#39;infrastruttura cloud_.

Se utilizzi Cloud Docker per Commerce come strumento di sviluppo, puoi distribuire il progetto di infrastruttura cloud in un ambiente Docker in modalità _sviluppatore_, ma le prestazioni sono più lente a causa di operazioni aggiuntive di sincronizzazione dei file. Consulta [Distribuire l&#39;ambiente Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) nella _guida di Cloud Docker per Commerce_.

## Modalità predefinita

La modalità _default_ consente di distribuire l&#39;applicazione Commerce su un singolo server senza modificare le impostazioni. Tuttavia, la modalità predefinita non è ottimizzata per la produzione a causa dell’impatto negativo sulle prestazioni dei file statici. La creazione e la memorizzazione nella cache di file statici ha un impatto maggiore sulle prestazioni rispetto alla generazione di tali file mediante lo strumento di creazione di file statici.

In modalità predefinita:

- Le eccezioni vengono scritte in file di registro anziché in visualizzazione
- I file delle viste statiche sono memorizzati nella cache
- Nasconde le intestazioni di richiesta HTTP e risposta `X-Magento-*` personalizzate

Commerce funziona in modalità predefinita se non è specificata alcuna altra modalità.

## Modalità sviluppatore

La modalità _sviluppatore_ è consigliata per estendere e personalizzare l&#39;applicazione Commerce. I file di visualizzazione statica non vengono memorizzati nella cache, ma scritti nella directory `pub/static` su richiesta.

In modalità sviluppatore:

- Abilita la [compilazione automatica del codice](../cli/code-compiler.md) e il debug avanzato
- Le eccezioni non rilevate vengono visualizzate nel browser
- La registrazione del sistema in `var/report` è dettagliata
- Nel gestore degli errori viene generata un&#39;eccezione, anziché essere registrata
- Viene generata un&#39;eccezione quando non è possibile richiamare un sottoscrittore di eventi
- Mostra le intestazioni di richiesta HTTP e risposta `X-Magento-*` personalizzate

## Modalità di produzione

La modalità _produzione_ è la migliore per distribuire l&#39;applicazione Commerce in un sistema di produzione. Dopo aver ottimizzato l&#39;ambiente del server, ad esempio il database e il server Web, è necessario eseguire lo strumento di distribuzione [file di visualizzazione statica](../cli/static-view-file-deployment.md) per scrivere file di visualizzazione statica nella directory `pub/static`. Questo migliora le prestazioni fornendo tutti i file statici necessari durante la distribuzione anziché costringere l’applicazione Commerce a individuare e copiare dinamicamente (materializzare) i file statici su richiesta durante il runtime.

Alcuni campi, come le sezioni di configurazione del sistema Avanzate e Sviluppatori nell’Admin, non sono disponibili in modalità di produzione. Ad esempio, _non è possibile_ abilitare o disabilitare i tipi di cache utilizzando l&#39;amministratore. È possibile abilitare e disabilitare i tipi di cache _only_ utilizzando la [riga di comando](../cli/manage-cache.md#config-cli-subcommands-cache-en).

In modalità di produzione:

- I file di visualizzazione statica vengono forniti solo dalla cache
- Gli errori e le eccezioni vengono registrati nel file system e non vengono mai visualizzati all&#39;utente
- Alcuni campi di configurazione nell’Amministratore non sono disponibili

## Modalità di manutenzione

La modalità _manutenzione_ limita o impedisce l&#39;accesso a un sito durante miglioramenti, aggiornamenti e attività di configurazione. Per impostazione predefinita, il sito reindirizza i visitatori a una pagina `Service Temporarily Unavailable` predefinita.

Puoi creare una [pagina di manutenzione personalizzata](../../upgrade/troubleshooting/maintenance-mode-options.md), abilitare e disabilitare manualmente la modalità di manutenzione e configurare la modalità di manutenzione in modo da consentire ai visitatori di indirizzi IP autorizzati di visualizzare l&#39;archivio normalmente. Vedere [attivare e disattivare la modalità di manutenzione](../../installation/tutorials/maintenance-mode.md) nella _Guida all&#39;installazione_.

Se utilizzi Commerce su un’infrastruttura cloud, l’applicazione Commerce viene eseguita in modalità di manutenzione durante la fase di distribuzione. Al termine della distribuzione, l’applicazione Commerce torna in esecuzione in modalità di produzione. Consulta [Hook di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) nella _guida di Commerce sull&#39;infrastruttura cloud_.

In modalità di manutenzione:

- I visitatori del sito vengono reindirizzati a una pagina `Service Temporarily Unavailable` predefinita
- La directory `var/` contiene il file `.maintenance.flag`
- Puoi limitare l’accesso dei visitatori in base agli indirizzi IP
