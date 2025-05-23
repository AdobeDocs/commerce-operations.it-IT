---
title: Proteggere il sito e l'infrastruttura Commerce
description: Mantenere la sicurezza implementando le best practice per la sicurezza durante la configurazione e l’aggiornamento delle installazioni di Adobe Commerce.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Proteggere il sito e l&#39;infrastruttura Commerce

La creazione e la manutenzione di un ambiente sicuro per i progetti Adobe Commerce implementati nell’infrastruttura cloud è una responsabilità condivisa tra i clienti Adobe Commerce, i partner delle soluzioni e Adobe. L’obiettivo di questa guida è quello di fornire best practice per il lato del cliente nell’equazione.

Anche se non è possibile eliminare tutti i rischi per la sicurezza, l&#39;applicazione di queste best practice rafforza la postura di sicurezza delle installazioni Commerce. Un sito e un&#39;infrastruttura sicuri rendono meno attraente il target di attacchi dannosi, garantiscono la sicurezza della soluzione e delle informazioni riservate dei clienti e contribuiscono a ridurre al minimo gli incidenti relativi alla sicurezza che possono causare interruzioni del sito e costose indagini.

>[!NOTE]
>
>Per informazioni sui ruoli e sulle responsabilità per la protezione e la gestione dei progetti Adobe Commerce nell&#39;infrastruttura cloud, vedere [Modello di responsabilità condivisa](https://experienceleague.adobe.com/it/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)) nella _Guida alla sicurezza e alla conformità di Adobe Commerce_.

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Raccomandazioni prioritarie

Adobe considera le seguenti raccomandazioni come della massima priorità per tutti i clienti. Implementa queste best practice chiave per la sicurezza in tutte le distribuzioni di Commerce:

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Abilita l&#39;autenticazione a due fattori per l&#39;amministratore e tutte le connessioni SSH**

- [Sicurezza per l&#39;amministratore di Commerce](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html?lang=it)

- [Connessioni SSH sicure](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html?lang=it) (infrastruttura cloud)

Quando MFA è abilitato in un progetto, tutti gli account Adobe Commerce su infrastrutture cloud con accesso SSH devono seguire un flusso di lavoro di autenticazione. Questo flusso di lavoro richiede un codice di autenticazione a due fattori (2FA) o un token API e un certificato SSH per accedere all’ambiente.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Proteggi amministratore**

- [Configurare un URL amministratore non predefinito](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=it#use-a-custom-admin-url) invece di utilizzare il `admin` predefinito o un termine comune come `backend`. Questa configurazione riduce l’esposizione agli script che tentano di ottenere l’accesso non autorizzato al sito.

- [Configurare le impostazioni di protezione avanzate](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=it) - Aggiungere una chiave segreta agli URL, richiedere che le password facciano distinzione tra maiuscole e minuscole e limitare la durata della sessione di amministrazione, l&#39;intervallo di durata della password e il numero di tentativi di accesso consentiti prima di bloccare un account utente amministratore. Per una maggiore sicurezza, configurare la durata dell&#39;inattività della tastiera prima della scadenza della sessione corrente e richiedere che il nome utente e la password siano sensibili all&#39;uso di maiuscole e minuscole.

- [Abilita ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html?lang=it) per proteggere l&#39;amministratore da attacchi di forza bruta automatizzati.

- Segui il principio del privilegio minimo quando assegni [Autorizzazioni amministratore](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html?lang=it) a ruoli e ruoli agli account utente amministratore.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Esegui l&#39;aggiornamento all&#39;ultima versione di Adobe Commerce**

Aggiorna il codice [aggiornando il progetto Commerce all&#39;ultima versione](#upgrade-to-the-latest-release) di Adobe Commerce, Commerce Services ed estensioni, incluse patch di sicurezza, hotfix e altre patch fornite da Adobe.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Valori di configurazione sensibili protetti**

Utilizza [gestione configurazione](../../../configuration/cli/set-configuration-values.md) per bloccare i valori di configurazione critici.

I comandi CLI `lock config` e `lock env` configurano le variabili di ambiente per impedirne l&#39;aggiornamento da parte dell&#39;amministratore. Il comando scrive il valore nel file `<Commerce base dir>/app/etc/env.php`. Per i progetti di infrastruttura cloud di Commerce, vedere [Gestione configurazione archivio](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=it#sensitive-data).

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Esegui analisi protezione**

Utilizzare il servizio [Commerce Security Scan](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=it) per monitorare tutti i siti Adobe Commerce per individuare rischi di protezione noti e malware e per ricevere aggiornamenti delle patch e notifiche di protezione.

## Garantire la sicurezza delle estensioni e del codice personalizzato

Quando estendi Adobe Commerce aggiungendo estensioni di terze parti da Adobe Commerce Marketplace o aggiungi codice personalizzato, assicurati che queste personalizzazioni siano sicure applicando le seguenti best practice:

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Scegli un partner o un integratore di soluzioni (SI) esperto in materia di sicurezza**. Assicurati integrazioni sicure e distribuzione sicura del codice personalizzato selezionando le organizzazioni che seguono procedure di sviluppo sicure e hanno una solida esperienza nel prevenire e risolvere i problemi di sicurezza.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utilizza estensioni sicure**—Identifica le estensioni più appropriate e sicure per le distribuzioni di Commerce consultando il tuo integratore o sviluppatore di soluzioni e seguendo le [best practice per le estensioni di Adobe](../planning/extensions.md).

- Solo le estensioni sorgente provengono da Adobe Commerce Marketplace o tramite l’integratore di soluzioni. Se l’estensione proviene da un integratore, assicurati che la proprietà della licenza dell’estensione sia trasferibile, nel caso in cui l’integratore cambi.

- Ridurre l&#39;esposizione ai rischi limitando il numero di estensioni e fornitori.

- Se possibile, controlla il codice dell’estensione per sicurezza prima di eseguire l’integrazione con l’applicazione Commerce.

- Assicurati che gli sviluppatori di estensioni PHP seguano le linee guida per lo sviluppo, i processi e le best practice per la sicurezza di Adobe Commerce. In particolare, gli sviluppatori devono evitare di utilizzare le funzionalità PHP che possono portare all&#39;esecuzione di codice remoto o a una crittografia debole. Vedi [Sicurezza](https://developer.adobe.com/commerce/php/best-practices/security/) nella *Guida alle best practice per gli sviluppatori di estensioni*.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Codice di controllo**—Controlla il server e l&#39;archivio del codice sorgente per individuare eventuali problemi di sviluppo. Assicurati che non vi siano file di registro accessibili, directory .git visibili pubblicamente, tunnel per eseguire istruzioni SQL, immagini di database, file di informazioni php o altri file non protetti che non sono necessari e che potrebbero essere utilizzati in un attacco.

## Effettua l’aggiornamento alla versione più recente

Adobe rilascia continuamente componenti della soluzione aggiornati per migliorare la sicurezza e proteggere meglio i clienti da possibili compromessi. L’aggiornamento alla versione più recente dell’applicazione Adobe Commerce, dei servizi installati e delle estensioni e l’applicazione delle patch correnti rappresenta la prima e migliore linea di difesa contro le minacce alla sicurezza.

Commerce in genere rilascia aggiornamenti di sicurezza su base trimestrale, ma si riserva il diritto di rilasciare aggiornamenti rapidi per gravi minacce alla sicurezza in base alla priorità e ad altri fattori.

Per informazioni sulle versioni di Adobe Commerce disponibili, sui cicli di rilascio e sul processo di aggiornamento e patch, consulta le risorse seguenti:

- [Versioni rilasciate](../../../release/versions.md)
- [Disponibilità del prodotto](../../../release/product-availability.md) (servizi Adobe Commerce ed estensioni create da Adobe)
- [criteri del ciclo di vita Adobe Commerce](../../../release/lifecycle-policy.md)
- [Guida all’aggiornamento](../../../upgrade/overview.md)
- [Come applicare le patch](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Ottieni le informazioni di sicurezza più recenti e attenua i problemi di sicurezza noti sottoscrivendo il [Servizio di notifica di sicurezza di Adobe](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## Sviluppo di un piano di disaster recovery

Se il sito Commerce è compromesso, è possibile controllare i danni e ripristinare rapidamente le normali operazioni aziendali sviluppando e implementando un piano completo di disaster recovery.

Se un cliente richiede il ripristino di un’istanza di Commerce a causa di un guasto irreparabile, Adobe può fornire al cliente i file di backup. Il cliente e l&#39;integratore di soluzioni, se applicabile, possono eseguire il ripristino.

Come parte di un piano di disaster recovery, Adobe consiglia vivamente ai clienti di [esportare la configurazione dell&#39;applicazione Adobe Commerce](../../../configuration/cli/export-configuration.md) per facilitare la ridistribuzione, se necessaria per scopi di business continuity. Il motivo principale per esportare la configurazione nel file system è che la configurazione del sistema ha la precedenza sulla configurazione del database. In un file system di sola lettura, l&#39;applicazione deve essere ridistribuita per modificare le impostazioni di configurazione sensibili, fornendo un ulteriore livello di protezione.

### Informazioni aggiuntive

**Adobe Commerce implementato nell&#39;infrastruttura cloud**

- [Backup e disaster recovery](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=it#backup-and-disaster-recovery)

- [Archivia la gestione della configurazione per Adobe Commerce nell&#39;infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=it)

**Adobe Commerce distribuito nei locali**

- [Esporta impostazioni di configurazione](../../../configuration/cli/export-configuration.md)

   - [Importa impostazioni di configurazione](../../../configuration/cli/import-configuration.md)

   - [Backup e rollback del file system, dei supporti e del database](../../../installation/tutorials/backup.md)

## Mantenere un sito e un&#39;infrastruttura sicuri

In questa sezione vengono riepilogate le best practice per mantenere la sicurezza dei siti e dell’infrastruttura per un’installazione di Adobe Commerce. Molte di queste best practice si concentrano sulla protezione dell’infrastruttura informatica in generale, pertanto alcune delle raccomandazioni potrebbero già essere implementate.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Blocca accesso non autorizzato**—Collabora con il tuo partner di hosting per configurare un tunnel VPN per bloccare l&#39;accesso non autorizzato al sito Commerce e ai dati dei clienti. Imposta un tunnel SSH per bloccare l’accesso non autorizzato all’applicazione Commerce.

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Utilizza un firewall dell&#39;applicazione Web**. Analizzare il traffico e individuare i pattern sospetti, ad esempio le informazioni sulla carta di credito inviate a un indirizzo IP sconosciuto utilizzando un firewall dell&#39;applicazione Web.

Le installazioni di Adobe Commerce distribuite nell&#39;infrastruttura cloud possono utilizzare i servizi WAF incorporati disponibili con l&#39;integrazione di [Fastly Services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=it)

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Configura impostazioni avanzate di sicurezza delle password**—Configura password sicure e modificale almeno ogni 90 giorni, come consigliato dallo standard PCI Data Security nella sezione 8.2.4. Consulta [Configurare le impostazioni di sicurezza dell&#39;amministratore](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=it).

![Elenco di controllo](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Usa HTTPS**. Se il sito Commerce è stato appena implementato, avviare l&#39;intero sito utilizzando HTTPS. Non solo Google utilizza HTTPS come fattore di classificazione, ma molti utenti non considerano nemmeno l’acquisto da un sito, a meno che non sia protetto con HTTPS.

## Protect contro il malware

Gli attacchi di malware che colpiscono i siti di e-commerce sono troppo comuni e gli attori della minaccia sviluppano continuamente nuovi modi per raccogliere informazioni personali e sulla carta di credito dalle transazioni.

Tuttavia, Adobe ha scoperto che la maggior parte dei compromessi sui siti non sono dovuti a un hacker innovativo. Piuttosto, gli attori che si occupano di minacce spesso sfruttano vulnerabilità esistenti e senza patch, password scadenti e impostazioni di proprietà e autorizzazioni inadeguate nel file system.

Negli attacchi più comuni, il codice dannoso viene iniettato nell&#39;intestazione o nel piè di pagina assoluto di un archivio clienti. In questo caso, il codice raccoglie i dati del modulo che un cliente inserisce nella vetrina, inclusi le credenziali di accesso del cliente e i dati del modulo di pagamento. Quindi, questi dati vengono inviati a un’altra posizione per scopi dannosi anziché al backend di Commerce. Inoltre, il malware può compromettere l’amministratore nell’eseguire il codice che sostituisce il modulo di pagamento originale con un modulo falso che sostituisce tutte le protezioni impostate dal provider di pagamenti.

Gli skimmer di carte di credito lato client sono un tipo di malware che incorpora il codice nel contenuto del sito web di un commerciante che può essere eseguito nel browser di un utente come mostrato nella figura seguente.

![Flusso di dati per attacchi malware destinati a siti e-commerce](../../../assets/playbooks/malware-data-flow.svg)

Quando si verificano determinate azioni, ad esempio l’invio di un modulo o la modifica di un valore di campo, lo skimmer serializza i dati e li invia agli endpoint di terze parti. Questi endpoint sono in genere altri siti web compromessi che fungono da relè per l’invio dei dati alla destinazione finale.


>[!TIP]
>
>Se un sito Commerce è interessato da un attacco di malware, seguire le best practice di Adobe Commerce per [rispondere a un problema di sicurezza](../maintenance/respond-to-security-incident.md).

### Conoscere gli attacchi più comuni

Di seguito è riportato un elenco delle categorie comuni di attacchi che Adobe consiglia a tutti i clienti Commerce di essere a conoscenza e di adottare misure di protezione contro:

- **Defacing del sito** - Un utente malintenzionato danneggia un sito Web modificandone l&#39;aspetto visivo o aggiungendo i propri messaggi. Sebbene l&#39;accesso al sito e agli account utente sia stato compromesso, le informazioni sui pagamenti rimangono spesso protette.

- **Botnet**: il server Commerce del cliente diventa parte di una botnet che invia messaggi di posta indesiderata. Anche se i dati utente non sono generalmente compromessi, il nome di dominio del cliente potrebbe essere inserito nell&#39;elenco Bloccati dai filtri anti-spam, impedendo la consegna di qualsiasi e-mail dal dominio. In alternativa, il sito del cliente diventa parte di una botnet causando un attacco Distributed Denial of Service (DDoS) su un altro sito/i. La botnet può bloccare il traffico IP in entrata verso il server Commerce, impedendo ai clienti di effettuare acquisti.

- **Attacchi diretti al server**: i dati sono compromessi, sono installati backdoor e malware e le operazioni del sito sono interessate. Le informazioni di pagamento non memorizzate sul server hanno meno probabilità di essere compromesse da questi attacchi.

- **Acquisizione di carte silenziose**. In questo attacco più disastroso, gli intrusi installano malware nascosto o software di acquisizione delle carte, o peggio, modificano il processo di pagamento per raccogliere i dati della carta di credito. Quindi, i dati vengono inviati a un altro sito per la vendita sul dark web. Tali attacchi possono passare inosservati per un periodo di tempo prolungato e possono compromettere gravemente gli account dei clienti e le informazioni finanziarie.

- **Registrazione chiavi invisibile all&#39;utente** - L&#39;attore minaccia installa sul server del cliente il codice di registrazione chiavi per raccogliere le credenziali utente amministratore in modo che possano accedere e avviare altri attacchi senza essere rilevati.

### Protect contro gli attacchi di individuazione password

Gli attacchi di brute force password indovinare possono causare l’accesso non autorizzato dell’amministratore. Protect il tuo sito da questi attacchi seguendo queste best practice:

- Identificare e proteggere tutti i punti in cui è possibile accedere all&#39;installazione di Commerce dall&#39;esterno.

  Puoi proteggere l&#39;accesso all&#39;amministratore, che in genere richiede la massima protezione, seguendo [le raccomandazioni sulla priorità di Adobe](#priority-recommendations) durante la configurazione del progetto Commerce.

- Controllare l&#39;accesso al sito Commerce impostando un elenco di controllo di accesso che consenta l&#39;accesso solo agli utenti provenienti da un indirizzo IP o una rete specifici.

  Puoi utilizzare un ACL Fastly Edge con uno snippet di codice VCL personalizzato per filtrare le richieste in ingresso e consentire l’accesso per indirizzo IP. Consulta [VCL personalizzato per consentire le richieste](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html?lang=it).


  >[!TIP]
  >
  >Se si utilizza una forza lavoro remota, assicurarsi che gli indirizzi IP dei dipendenti remoti siano inclusi nell&#39;elenco degli indirizzi con l&#39;autorizzazione per accedere al sito Commerce.

### Impedire gli exploit di clickjacking

Adobe protegge il tuo archivio dagli attacchi di clickjacking fornendo l&#39;intestazione di richiesta HTTP `X-Frame-Options` che puoi includere nelle richieste alla vetrina. Consulta [Previeni gli exploit di clickjacking](../../../configuration/security/xframe-options.md) nella *Guida alla configurazione di Adobe Commerce*.
