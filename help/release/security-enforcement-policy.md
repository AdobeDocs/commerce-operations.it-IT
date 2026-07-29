---
title: 'Criterio di applicazione della sicurezza: azioni necessarie e scadenze'
description: Scopri come applicare le misure di sicurezza per le versioni di Adobe Commerce on Cloud non supportate e le dipendenze dal software, comprese scadenze, azioni richieste e rischi.
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Solo Adobe Commerce su Cloud" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Cloud."
hide: true
source-git-commit: 93446d5be993e53e94f714a592d519a945dfbebd
workflow-type: tm+mt
source-wordcount: 1915
ht-degree: 0%

---

# Criterio di applicazione della sicurezza: azioni e scadenze richieste

Adobe applica i requisiti di sicurezza per Adobe Commerce negli ambienti Cloud, incluse le versioni di dipendenza software supportate e le versioni Adobe Commerce supportate. Questa pagina descrive cosa è necessario, le date di applicazione e cosa accade se i requisiti non vengono soddisfatti.

## Cosa sta succedendo?

La politica di sicurezza aziendale di Adobe richiede che tutti gli ambienti ospitati da Adobe per Adobe Commerce on Cloud vengano eseguiti con un software sicuro e conforme.

1. Versioni supportate di tutte le dipendenze software di terze parti (PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)

1. Adobe Commerce on Cloud (versione 2.4.8, 2.4.9 o l’ultima versione)

In questo modo si riducono i rischi per la sicurezza negli ambienti di e-commerce. Per gli ambienti che non soddisfano questi requisiti entro le scadenze della [Tabella 1](#determine-your-required-actions), il traffico in entrata verrà sospeso e la vetrina verrà disconnessa. Considera questo avviso come un requisito di sicurezza e conformità con date di applicazione.

Potrebbe essere necessario eseguire due azioni.

1. Verificare se le dipendenze software di terze parti sono supportate. In caso contrario, effettua l’aggiornamento a una versione supportata.

1. Seleziona questa opzione se devi aggiornare la versione di Adobe Commerce su Cloud a una versione supportata.

### Determinare le azioni richieste

Nella tabella seguente, trova la tua versione di Adobe Commerce on Cloud qui sotto per scoprire cosa ti serve.

**Tabella 1: azioni richieste e scadenze per versione**

| **Versione** | **[Azione 1:<br>Aggiorna dipendenze software di terze parti](#action-1-upgrade-third-party-software-dependencies)**&#x200B; | &#x200B;** Azione 2:<br>[Aggiorna o migra la versione di Adobe Commerce](#action-2-upgrade-to-a-supported-adobe-commerce-version)** |
| --- | --- | --- |
| 2.4.4 o 2.4.5 | Azione richiesta entro il 30 ottobre 2026. | Azione richiesta entro il 1° giugno 2027 |
| 2.4.6 o 2.4.7 | Azione richiesta entro il 30 ottobre 2026 o il 31 maggio 2027, a seconda del software. | Azione richiesta entro il 1° giugno 2028 |
| 2.4.8 o 2.4.9 | Azione richiesta entro il 30 ottobre 2026 o il 31 maggio 2027, a seconda del software. | Al momento non è richiesta alcuna azione |

## Chi non deve intervenire

Il presente avviso non si applica:

* Clienti che utilizzano [!DNL Adobe Commerce as a Cloud Service]
* Clienti che utilizzano Adobe Commerce on Cloud versione 2.4.8 o 2.4.9 con dipendenze software supportate in tutti gli ambienti

### Verifica le versioni correnti

Per verificare quale versione stai eseguendo in ciascuno degli ambienti Adobe Commerce su Cloud, rivolgiti al tuo amministratore di e-commerce e segui i passaggi seguenti.

#### Passaggio 1: controllare la versione di Adobe Commerce su Cloud

1. Accedi al pannello di amministrazione di Adobe Commerce.

   La versione corrente deve essere visualizzata nell’angolo in basso a destra di qualsiasi pagina Amministratore.

1. Se la versione non viene visualizzata nell&#39;amministratore, utilizzare lo strumento della riga di comando [Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"} per eseguire il comando version:

   ```shell
   bin/magento --version
   ```

#### Passaggio 2: verificare le versioni delle dipendenze software

1. Accedi alla [console cloud](https://console.adobecommerce.com/).
1. Apri il progetto pertinente, quindi seleziona l’ambiente da rivedere.
1. Controllare la configurazione del servizio per l&#39;ambiente nel file `.magento/services.yaml`, che definisce i nomi e le versioni dei servizi supportati utilizzati da Adobe Commerce sull&#39;infrastruttura cloud.
Per istruzioni dettagliate, consulta la documentazione di [Configurazione dei servizi](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}.

## Perché questo mandato di sicurezza è importante

Il software che ha superato la fine del supporto del fornitore non riceve più patch di sicurezza, il che significa che non è possibile risolvere i problemi di sicurezza noti in tale software. Inoltre, in base a [Adobe Lifecycle Policy](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy):

* **Le versioni 2.4.4 e 2.4.5** di Adobe Commerce ricevono ora solo correzioni di sicurezza limitate e isolate per l&#39;applicazione principale fino al 31 maggio 2027. Questo supporto limitato non include correzioni di qualità, supporto di compatibilità per le dipendenze delle applicazioni (ad esempio, PHP) o aggiornamenti delle dipendenze della piattaforma

* **Adobe Commerce 2.4.6** riceverà il supporto esteso fino al 30 agosto 2027 e solo correzioni di sicurezza limitate e isolate per l&#39;applicazione di base fino al 31 maggio 2028

* **Adobe Commerce versione 2.4.7** riceverà supporto standard fino al 31 maggio 2027 e supporto esteso fino al 31 maggio 2028

* **Adobe Commerce on Cloud versione 2.4.8 e 2.4.9** rimangono supportati e al momento non richiedono alcun aggiornamento della versione.

Continuare a eseguire la vetrina di e-commerce su software non supportato crea un rischio reale e crescente per la sicurezza della tua azienda, inclusa la possibilità di mantenere la conformità PCI e proteggere i dati dei tuoi clienti.

>[!WARNING]
>
>Se l&#39;ambiente non soddisfa i requisiti entro le scadenze indicate nella tabella [Azioni obbligatorie e scadenze](#determine-your-required-actions), Adobe sarà costretto a sospendere il traffico in entrata verso l&#39;ambiente interessato. La vetrina dell’e-commerce sarà offline e non servirà gli acquirenti.

## Cosa richiede ogni azione

### Azione 1: aggiornamento delle dipendenze software di terze parti

A seconda del software, tutte le dipendenze software non supportate devono essere aggiornate in base alle timeline condivise nella tabella seguente. Puoi visualizzare i tuoi ambienti nella [Cloud Console](https://console.adobecommerce.com/). Per verificare le versioni delle dipendenze in esecuzione in ogni ambiente, vedere [Verificare le versioni delle dipendenze software](#check-software-dependency-versions). Gli aggiornamenti delle dipendenze software sono applicabili a tutte le versioni da 2.4.4 a 2.4.9 di Adobe Commerce on Cloud.

**Tabella 2: requisiti per l&#39;aggiornamento della dipendenza software**

| Dipendenza | Versione | Deve effettuare l’aggiornamento a | Data di applicazione |
| --- | --- | --- | --- |
| PHP | 8.1 e versioni successive | 8.2 o superiore | 31 maggio 2027 |
| MariaDB/Galera | 10.5 e versioni successive | 10.6 o superiore | 30 ottobre 2026 |
| MariaDB/Galera | Maggiore di 10,5 ma inferiore a 10,11 | 10.11 o superiore | 31 maggio 2027 |
| Elasticsearch | qualsiasi versione | OpenSearch:<br><br>- versione 2.19 per i clienti 2.4.4 e 2.4.5<br>- versione 3 per i clienti 2.4.6 e versioni successive. | 30 ottobre 2026 |
| OpenSearch | 1.x | versione 2.19 per i clienti 2.4.4 e 2.4.5.<br>versione 3 per i clienti 2.4.6 e versioni successive. | 31 maggio 2027 |
| Redis | 5 e versioni successive | Valkey 8 o superiore | 31 maggio 2027 |
| RabbitMQ | 3.9 e versioni successive | 3.13 o superiore | 30 ottobre 2026 |
| RabbitMQ | Maggiore di 3,9 ma inferiore a 3,13 | 4.3 o superiore | 31 maggio 2027 |

#### Prepararsi per un aggiornamento delle dipendenze software di terze parti

Adobe ti aiuterà ad aggiornare direttamente queste dipendenze software.

* **Guida introduttiva:** Apri un ticket di supporto elencando gli ambienti da aggiornare e le dipendenze coinvolte. Apri il ticket almeno 30 giorni prima della data di applicazione in modo che il nostro team possa pianificare il lavoro.

* **Inattività:** Adobe confermerà con te la finestra prevista durante la pianificazione.

* **Test:** Aggiorna e convalida un ambiente non di produzione prima della produzione. Come minimo, convalida l’estrazione, la ricerca, il carrello ed eventuali integrazioni personalizzate. I requisiti si applicano a tutti gli ambienti, pertanto pianifica l’aggiornamento di ogni ambiente anziché della sola produzione.

* **Compatibilità:** La maggior parte di queste modifiche sono aggiornamenti della versione all&#39;interno dello stesso software e comportano un rischio ridotto. I seguenti aspetti meritano maggiore attenzione:

  * **Elasticsearch in OpenSearch** e **Redis in Valkey** sono migrazioni a software diverso anziché aggiornamenti di versione. Potrebbe essere necessario aggiornare il codice personalizzato, le estensioni o la configurazione che fa riferimento al servizio originale.
  * **PHP da 8.1 a 8.2** può far emergere elementi obsoleti nel codice personalizzato e nelle estensioni di terze parti.

Se utilizzi estensioni di terze parti, conferma con i fornitori delle estensioni che le loro versioni correnti supportano le versioni di destinazione. Se si lavora con un integratore di soluzioni, coinvolgerlo nella pianificazione e nella convalida.

### Azione 2: passare a una versione supportata di Adobe Commerce

Se devi aggiornare la versione di Adobe Commerce su Cloud, hai due opzioni:

1. [Passare a una versione supportata di Adobe Commerce on Cloud](#upgrade-to-adobe-commerce-on-cloud-version-249)
1. [Migrazione ad Adobe Commerce as a Cloud Service (piattaforma SaaS)](#migrate-to-adobe-commerce-as-a-cloud-service)

La data di applicazione per la versione corrente si applica indipendentemente dall’opzione scelta.

**Tabella 3: Linee guida e scadenze per l&#39;aggiornamento a una versione supportata di Adobe Commerce on Cloud**

| Versione corrente | Azione | Data di applicazione |
| --- | --- | --- |
| Utilizzo di Adobe Commerce su Cloud versione 2.4.4 o 2.4.5 | Effettua l’aggiornamento a Adobe Commerce on Cloud versione 2.4.9 (o l’ultima versione) o effettua la migrazione ad Adobe Commerce as a Cloud Service | 1 giugno 2027 |
| Utilizzo di Adobe Commerce su Cloud versione 2.4.6 o 2.4.7 | Effettua l’aggiornamento a Adobe Commerce on Cloud versione 2.4.9 (o l’ultima versione) o effettua la migrazione ad Adobe Commerce as a Cloud Service | 1 giugno 2028 |
| Utilizzo di Adobe Commerce su Cloud versioni 2.4.8 o 2.4.9 | Al momento non è necessaria alcuna azione di aggiornamento della versione di Adobe Commerce su Cloud. Le scadenze relative alle dipendenze software di cui all&#39;azione 1 sono ancora valide. | n/d |

## Confrontare le opzioni

Per decidere quale opzione soddisfa le tue esigenze, consulta la tabella seguente che confronta Adobe Commerce on Cloud versione 2.4.9 con Adobe Commerce as a Cloud Service.

**Tabella 4: confronto tra Adobe Commerce su Cloud e Adobe Commerce as a Cloud Service**

| | Adobe Commerce su Cloud versione 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| Che cos’è | L’ultima versione di Adobe Commerce con copertura totale della sicurezza, correzioni di qualità e aggiornamenti delle dipendenze dalla piattaforma. | Piattaforma commerce completamente gestita di Adobe, progettata per l&#39;innovazione continua senza sovraccarichi di upgrade. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| Consigliato per te se | Per il momento è necessario continuare a gestire l&#39;infrastruttura, gli aggiornamenti e le patch. Puoi eseguire la migrazione ad Adobe Commerce as a Cloud Service quando lo desideri. | Desideri lasciare i cicli di aggiornamento indietro per sempre, ridurre il costo totale di proprietà e ottenere automaticamente le funzionalità più recenti di Adobe, senza alcun sforzo aggiuntivo. |
| Vantaggi chiave | Soddisfa ora i requisiti di sicurezza mantenendo la configurazione esistente. | Una vetrina fulminea e all’avanguardia, un catalogo altamente scalabile, la gestione nativa delle risorse digitali e l’intelligenza artificiale generativa integrata, il tutto su un’infrastruttura gestita da Adobe. |

## Cosa succede se non agisci?

Se un ambiente non soddisfa questi requisiti entro le date di applicazione in [Determinare le azioni richieste](#determine-your-required-actions), Adobe adotterà le misure appropriate. Ciò include la sospensione del traffico verso l’infrastruttura interessata e, di conseguenza, la vetrina dell’e-commerce non sarà più in linea.

Se un ambiente continua a non essere conforme dopo la sospensione del traffico, Adobe può interrompere i servizi cloud, avviando il processo di disattivazione. Con la disattivazione, tutti i dati e le risorse all’interno dell’ambiente di e-commerce ospitato, incluse tutte le istanze, gli ambienti e i rami, verranno eliminati definitivamente e non potranno essere ripristinati.

## Come Adobe ti aiuterà

Adobe offre strumenti e supporto per rendere la transizione più fluida possibile, indipendentemente dal fatto che si effettui l’aggiornamento o la migrazione.

### Aggiornamento ad Adobe Commerce on Cloud versione 2.4.9

* **Rapporto compatibilità aggiornamento:** Adobe fornisce un rapporto dettagliato che identifica esattamente ciò che richiede l&#39;aggiornamento ad Adobe Commerce versione 2.4.9, inclusi l&#39;ambito di tempo e costi. [Genera il tuo report di compatibilità per l&#39;aggiornamento](https://supportinsights.adobe.com/commerce/tab/main).

* **Aggiornamento dipendenze software:** Poiché non è possibile aggiornare direttamente le dipendenze software, [apri un ticket di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"} per consentire ad Adobe di gestire l&#39;aggiornamento. Per ulteriori dettagli, vedere [Configurare i servizi](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}.

### Migrazione ad Adobe Commerce as a Cloud Service

Adobe fornisce strumenti che riducono i costi e i tempi di migrazione ad Adobe Commerce as a Cloud Service. Questi strumenti sono applicabili solo alla migrazione. Non vengono utilizzati per l’aggiornamento di una versione in Adobe Commerce su Cloud. Consulta la [panoramica sulla migrazione](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) per la guida completa alla migrazione, inclusi i percorsi e le fasi di migrazione.

* **Valutazione della migrazione:** valuta la complessità della migrazione delle personalizzazioni. Consulta la [Panoramica dello strumento di valutazione della migrazione](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migrazione dati:** Lo strumento di [migrazione dati in massa e incrementale](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data) sposta i dati nel nuovo ambiente Adobe Commerce as a Cloud Service.

* **Migrazione dello storefront e delle estensioni:** Gli strumenti per sviluppatori e la migrazione [basata sull&#39;intelligenza artificiale di Adobe](https://developer.adobe.com/commerce/extensibility/developer-agent/), inclusi [!DNL Adobe Developer App Builder] e [!DNL Commerce Storefront powered by Edge Delivery Services], consentono di accelerare la modernizzazione dello storefront e la ridefinizione della piattaforma delle estensioni.

In caso di domande, contatta il team del tuo account, il Solution Account Manager, lo specialista del rinnovo o contatta [Servizi di supporto](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).
