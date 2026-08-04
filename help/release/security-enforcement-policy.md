---
title: 'Sicurezza e conformità: azioni necessarie e scadenze'
description: Scopri come applicare le misure di sicurezza per le versioni di Adobe Commerce on Cloud non supportate e le dipendenze dal software, comprese scadenze, azioni richieste e rischi.
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Solo Adobe Commerce su Cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo alle versioni da 2.4.4 a 2.4.9 di Adobe Commerce on Cloud"
color: blue
source-git-commit: 79afa4fa95c425dfd4bc0fd894abc24db2d1b33b
workflow-type: tm+mt
source-wordcount: 2040
ht-degree: 0%

---


# Avviso di sicurezza e conformità: azioni necessarie e scadenze

>[!NOTE]
>
> **Si applica a:** ambienti Adobe Commerce on Cloud (PaaS) che eseguono Adobe Commerce dalle versioni da 2.4.4 a 2.4.9.
>
> Questa guida non si applica agli ambienti [!DNL Adobe Commerce as a Cloud Service] (SaaS) o alle distribuzioni locali di Adobe Commerce.

Il panorama della cibersicurezza sta cambiando radicalmente e i meccanismi difensivi che le imprese hanno bisogno di evolvere rapidamente. La sicurezza è fondamentale per le aziende di e-commerce perché le transazioni online richiedono di gestire dati personali e aziendali sensibili, esponendoli a rischi finanziari e di identità in caso di violazione. Gli ambienti di e-commerce PaaS dispongono di un modello di responsabilità di sicurezza condiviso tra Adobe e i nostri clienti, in cui i clienti sono responsabili della manutenzione delle dipendenze del livello dell’applicazione, delle integrazioni con software di terze parti e delle pipeline di distribuzione.

Adobe affronta in modo proattivo i rischi in evoluzione e garantisce che i nostri clienti Adobe Commerce on Cloud siano impostati secondo gli standard di sicurezza più elevati. Ciò include:

* Correzioni di sicurezza mensili e isolate per una protezione più rapida e prevedibile da vulnerabilità critiche
* Rilasci annuali di patch con supporto a lungo termine
* Criteri del ciclo di vita semplificati per ogni versione con una finestra di supporto di 3 anni

Mentre Adobe adotta le misure necessarie per proteggere i nostri clienti, il [modello di responsabilità condivisa](../security-and-compliance/shared-responsibility.md) per Adobe Commerce on Cloud richiede che i nostri clienti utilizzino sempre una versione supportata di Adobe Commerce on Cloud e di software di terze parti, applichino patch alle applicazioni, controllino le estensioni di terze parti e proteggano il codice personalizzato. Il software che ha superato la fine del supporto del fornitore non riceve più patch di sicurezza, lasciando irrisolti i problemi di sicurezza nel software. Continuare a eseguire la vetrina di e-commerce su software non supportato crea un rischio di sicurezza reale e crescente.

Questa pagina illustra le azioni che tutti i clienti di Adobe Commerce su Cloud (versioni da 2.4.4 a 2.4.9) devono intraprendere per garantire la protezione dei propri ambienti di e-commerce, oltre alle date di applicazione e a cosa aspettarsi quando i requisiti di sicurezza non vengono soddisfatti.

## Azioni necessarie per mantenere un ambiente sicuro e conforme

Per garantire la sicurezza e la conformità dell’ambiente di e-commerce, tutti i clienti di Adobe Commerce on Cloud devono utilizzare:

1. Versioni supportate di tutte le dipendenze software di terze parti: PHP, MariaDB, Elasticsearch/OpenSearch, Redis e RabbitMQ

1. Una versione protetta e supportata di Adobe Commerce on Cloud

Segui le linee guida riportate di seguito per verificare se è necessario intervenire per proteggere Adobe Commerce negli ambienti Cloud. Gli ambienti che non soddisfano i requisiti di sicurezza entro le scadenze indicate nella tabella 1 seguente avranno traffico in entrata sospeso, disconnettendo la vetrina. Se hai dubbi sul rispetto della scadenza e hai bisogno di una breve proroga, contatta il team del tuo account o il [supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) di Adobe.

**Tabella 1: requisiti di sicurezza e scadenze**

| Versione di Adobe Commerce su Cloud | Aggiornamento alle dipendenze software di terze parti supportate | Effettua l&#39;aggiornamento alla versione più recente di Adobe Commerce on Cloud o effettua la migrazione a [!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4 o 2.4.5 | Richiesto entro il 30 ottobre 2026. | Richiesto entro il 1° giugno 2027 |
| 2.4.6 o 2.4.7 | Richiesto entro il 30 ottobre 2026 o il 31 maggio 2027, a seconda del software. | Richiesto entro il 1° giugno 2028 |
| 2.4.8 o 2.4.9 | Richiesto entro il 30 ottobre 2026 o il 31 maggio 2027, a seconda del software. | Non obbligatorio in questo momento |

## Passaggi dettagliati per la protezione dell’ambiente

### Azione 1: verifica e aggiornamento delle dipendenze software di terze parti

Verifica che nell’ambiente siano in esecuzione versioni supportate dal fornitore delle seguenti dipendenze software di terze parti: PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ. In caso contrario, aggiornare la dipendenza software a una versione supportata.

#### Passaggio 1: verifica delle versioni delle dipendenze software di terze parti

1. Accedi alla [console cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/start/cloud-console).
2. Apri il progetto pertinente, quindi seleziona l’ambiente da rivedere.
3. Controllare la configurazione del servizio per l&#39;ambiente nel file `.magento/services.yaml`, che definisce i nomi e le versioni dei servizi supportati utilizzati da Adobe Commerce su Cloud.

Per istruzioni dettagliate, vedere [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

Tutte le dipendenze software non supportate devono essere aggiornate alle versioni indicate dalle timeline nella tabella 2 seguente.

**Tabella 2: aggiornamenti delle dipendenze richiesti**

| Dipendenza | Versione | Deve effettuare l’aggiornamento a | Scadenza |
| --- | --- | --- | --- |
| PHP | 8.1 e versioni successive | 8.2 o superiore | 31 maggio 2027 |
| MariaDB/Galera | 10.5 e versioni successive | 10.6 o superiore | 30 ottobre 2026 |
| MariaDB/Galera | Maggiore di 10,5 ma inferiore a 10,11 | Versione 10.11 o successiva | 31 maggio 2027 |
| Elasticsearch | qualsiasi versione | OpenSearch: versione 2.19 per i clienti delle versioni 2.4.4 e 2.4.5. Versione 3 per i clienti 2.4.6 e successive. | 30 ottobre 2026 |
| OpenSearch | 1.x | Versione 2.19 per i clienti 2.4.4 e 2.4.5. Versione 3 per i clienti 2.4.6 e successive. | 31 maggio 2027 |
| Redis | 5 e versioni successive | Valkey versione 8 o successiva | 31 maggio 2027 |
| RabbitMQ | 3.9 e versioni successive | Versione 3.13 o successiva | 30 ottobre 2026 |
| RabbitMQ | Maggiore di 3,9 ma inferiore a 3,13 | 4.3 o superiore | 31 maggio 2027 |

#### Passaggio 2: prepararsi per un aggiornamento della dipendenza software di terze parti

Adobe ti aiuterà ad aggiornare direttamente queste dipendenze software.

* **Introduzione:** Aprire un [ticket di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) elencando gli ambienti da aggiornare e le dipendenze associate. Apri il ticket almeno 30 giorni prima della data di applicazione in modo che Adobe possa pianificare il lavoro.

* **Tempo di inattività:** Adobe conferma con te la finestra prevista durante la pianificazione.

* **Test:** Aggiorna e convalida un ambiente non di produzione prima della produzione. Come minimo, convalida l’estrazione, la ricerca, il carrello ed eventuali integrazioni personalizzate. I requisiti si applicano a tutti gli ambienti, pertanto pianifica l’aggiornamento di ogni ambiente anziché della sola produzione.

* **Compatibilità:** La maggior parte di queste modifiche sono aggiornamenti della versione all&#39;interno dello stesso software e comportano un rischio ridotto. Le seguenti modifiche richiedono maggiore attenzione:

  * **Elasticsearch in OpenSearch** e **Redis in Valkey** sono migrazioni a software diverso anziché aggiornamenti di versione. Potrebbe essere necessario aggiornare il codice personalizzato, le estensioni o la configurazione che fa riferimento al servizio originale.
  * L&#39;aggiornamento da **PHP 8.1 a 8.2** può far emergere avvisi di elementi obsoleti nel codice personalizzato e nelle estensioni di terze parti.

Se utilizzi estensioni di terze parti, conferma con i fornitori che le loro versioni correnti supportano le versioni del software di destinazione. Se si lavora con un integratore di soluzioni, coinvolgerlo nelle fasi iniziali della pianificazione, del test e della convalida dell&#39;aggiornamento.

### Azione 2: verifica la versione di Commerce on Cloud e aggiornala a una versione supportata

Controlla quale versione di Adobe Commerce su Cloud vengono eseguiti gli ambienti. Se un ambiente non dispone di una versione supportata, è possibile eseguire l&#39;aggiornamento alla versione 2.4.9 o all&#39;ultima versione supportata oppure eseguire la migrazione a [!DNL Adobe Commerce as a Cloud Service].

#### Passaggio 1: verifica la versione di Adobe Commerce su Cloud e l’azione richiesta

1. Accedi al tuo pannello di amministrazione di Adobe Commerce.

   La versione corrente viene visualizzata nell’angolo inferiore destro di qualsiasi pagina Amministratore.

1. Se la versione è nascosta dal pannello Amministratore:

   * Connetti all&#39;[ambiente remoto](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections#connect-to-a-remote-environment).
   * Utilizza lo strumento da riga di comando [Adobe Commerce](../configuration/cli/config-cli.md) per verificare la versione.

     ```shell
     bin/magento --version
     ```

Seleziona le azioni richieste per la versione di Adobe Commerce nella tabella seguente.

**Tabella 3: requisiti per l&#39;aggiornamento della versione di Adobe Commerce su Cloud**

| Versione corrente di Adobe Commerce su Cloud | Azione richiesta | Scadenza |
|---|---|---|
| Versione 2.4.4 o 2.4.5 | Effettua l’aggiornamento alla versione 2.4.9 di Adobe Commerce on Cloud (o alla versione più recente) o esegui la migrazione a [!DNL Adobe Commerce as a Cloud Service].<br>Motivo: le versioni v2.4.4 e 2.4.5 ricevono solo correzioni di sicurezza limitate e isolate per l’applicazione di base fino al 31 maggio 2027; non sono incluse le correzioni di qualità, il supporto per la compatibilità per le dipendenze delle applicazioni (ad esempio, PHP) o gli aggiornamenti delle dipendenze della piattaforma. Consulta [Criteri del ciclo di vita](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) di Adobe. | 1 giugno 2027 |
| Versione 2.4.6 o 2.4.7 | Effettua l’aggiornamento a Adobe Commerce on Cloud versione 2.4.9 (o alla versione più recente) o esegui la migrazione a [!DNL Adobe Commerce as a Cloud Service].<br>Motivo: la versione 2.4.6 riceve il supporto esteso fino al 30 agosto 2027 e riceve solo correzioni di sicurezza limitate e isolate per l’applicazione di base fino al 31 maggio 2028. La versione 2.4.7 riceve il supporto standard fino al 31 maggio 2027 e il supporto esteso fino al 31 maggio 2028. Consulta [Criteri del ciclo di vita](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) di Adobe. | 1 giugno 2028 |
| Versione 2.4.8 o 2.4.9 | Non è necessaria alcuna azione di aggiornamento della versione di Adobe Commerce su Cloud. Le scadenze relative alle dipendenze software di terze parti nell&#39;azione 1 sono ancora valide.<br>Motivo: non è stata impostata alcuna scadenza. | Non obbligatorio in questo momento |

#### Passaggio 2: determinare il percorso di aggiornamento o migrazione

Se devi aggiornare la versione di Adobe Commerce su Cloud, hai due opzioni:

1. Passare a una versione supportata di Adobe Commerce on Cloud
1. Migra a [!DNL Adobe Commerce as a Cloud Service] (SaaS)

Per decidere il percorso migliore, utilizzare la tabella seguente per confrontare le opzioni:

**Tabella 4: Adobe Commerce su Cloud rispetto a[!DNL Adobe Commerce as a Cloud Service]**

| | Adobe Commerce su Cloud versione 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **Che cos&#39;è** | L’ultima versione di Adobe Commerce con copertura totale della sicurezza, correzioni di qualità e aggiornamenti delle dipendenze dalla piattaforma. | Piattaforma commerce completamente gestita di Adobe, progettata per l&#39;innovazione continua senza sovraccarichi di upgrade. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| **Migliore per te se** | È necessario continuare a gestire l&#39;infrastruttura, gli aggiornamenti e le patch. | Desideri lasciare i cicli di aggiornamento indietro per sempre, ridurre il costo totale di proprietà e ottenere automaticamente le funzionalità più recenti di Adobe, senza alcun sforzo aggiuntivo. |
| **Vantaggio chiave** | Soddisfa i requisiti di sicurezza mantenendo la configurazione esistente. | Una vetrina fulminea e all’avanguardia, un catalogo altamente scalabile, la gestione nativa delle risorse digitali e l’intelligenza artificiale generativa integrata, il tutto su un’infrastruttura gestita da Adobe. |

## Cosa succede se non viene intrapresa alcuna azione entro la scadenza?

Adobe si impegna ad aiutarti a compiere i passaggi necessari per effettuare l’aggiornamento alle versioni supportate di Adobe Commerce su Cloud e al software di terze parti.

Se un ambiente non soddisfa i requisiti di sicurezza entro le date di imposizione condivise in precedenza, Adobe sarà costretta a intraprendere azioni appropriate per garantire la sicurezza per la base di installazione più ampia. Ciò include la sospensione del traffico verso l’infrastruttura interessata e, di conseguenza, la vetrina dell’e-commerce non sarà più in linea.

Se un ambiente continua a non essere conforme dopo la sospensione del traffico, Adobe può interrompere i servizi cloud, avviando il processo di disattivazione. Con la disattivazione, tutti i dati e le risorse all’interno dell’ambiente di e-commerce ospitato, incluse tutte le istanze, gli ambienti e i rami, verranno eliminati definitivamente e non potranno essere ripristinati.

## Risorse per il supporto dell&#39;aggiornamento o della migrazione

**Se scegli di eseguire l&#39;aggiornamento ad Adobe Commerce su Cloud versione 2.4.9:**

* **Rapporto compatibilità aggiornamento:** Adobe fornisce un rapporto dettagliato che identifica esattamente ciò che richiede l&#39;aggiornamento ad Adobe Commerce versione 2.4.9, incluso l&#39;ambito dei costi. [Genera il tuo report sulla compatibilità dell&#39;aggiornamento](https://supportinsights.adobe.com/commerce/tab/main).

* **Aggiornamento dipendenza software:** Poiché non è possibile aggiornare direttamente le dipendenze software, aprire un [ticket di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) affinché Adobe possa gestire l&#39;aggiornamento. Per ulteriori dettagli, vedere [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

**Se scegli di migrare a [!DNL Adobe Commerce as a Cloud Service]:**

Adobe fornisce strumenti che riducono i costi e i tempi di migrazione a [!DNL Adobe Commerce as a Cloud Service]. Sono disponibili gratuitamente. Questi strumenti sono applicabili solo alla migrazione. Non vengono utilizzati per gli aggiornamenti delle versioni di Adobe Commerce on Cloud. Consulta la [panoramica sulla migrazione](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) per la guida completa alla migrazione, inclusi i percorsi e le fasi di migrazione.

* **Valutazione della migrazione:** valuta la complessità della migrazione delle personalizzazioni. Consulta la [Panoramica dello strumento di valutazione della migrazione](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migrazione dati:** Lo strumento di [migrazione dati in massa e incrementale](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool) sposta i dati nel nuovo ambiente [!DNL Adobe Commerce as a Cloud Service].

* **Strumenti di sviluppo e migrazione assistiti dall&#39;intelligenza artificiale:** Adobe Developer App Builder e Commerce Storefront con tecnologia Edge Delivery Services aiutano ad accelerare la modernizzazione e la ridefinizione delle estensioni della vetrina.

In caso di domande, contatta il team del tuo account o contatta [Servizi di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

>[!MORELIKETHIS]
>
>* [Ciclo di vita](lifecycle-policy.md)
>* [Criterio di applicazione dell&#39;aggiornamento della versione per Adobe Commerce su Cloud](version-upgrade-enforcement-policy.md)
>* [Sicurezza responsabilità condivisa e modello operativo](../security-and-compliance/shared-responsibility.md)
