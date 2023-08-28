---
title: Best practice per la distribuzione delle patch su larga scala
description: Scopri in che modo l’applicazione di patch centralizzate per Adobe Commerce può aiutarti a gestire i progetti aziendali.
role: Developer
feature: Best Practices
badge: label="Contribuito da Anton Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Con il contributo di Anton Evers"
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Best practice per la distribuzione delle patch di Adobe Commerce su larga scala

Se gestisci più installazioni di Adobe Commerce, [applicazione patch](../../../upgrade/patches/apply.md) può essere un processo complesso. _Applicazione centralizzata di patch_ è una parte essenziale di [architettura di riferimento globale](../../architecture/global-reference/overview.md) e una buona pratica per le imprese. Consente di applicare le patch corrette a tutte le installazioni di Adobe Commerce. Questo argomento spiega come ottenere una distribuzione centralizzata delle patch per tutti i tipi di Adobe Commerce [patch](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Il seguente contenuto è stato originariamente pubblicato in [Distribuzione delle patch di Adobe Commerce su larga scala](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) post sull&#39;Adobe Blog di tecnologia. È stato modificato per concentrarsi sui passaggi e sugli esempi di codice per l’implementazione di una strategia di applicazione di patch centralizzata. Per ulteriori dettagli sui diversi tipi di patch qui descritti, consulta il post originale.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce locale

## Strategia

Poiché esistono molti tipi diversi di patch e molti modi per applicarle, come si fa a sapere quale patch viene applicata per prima? Maggiore è il numero di patch disponibili, maggiore è la possibilità che vengano applicate allo stesso file o alla stessa riga di codice. Le patch vengono applicate nell&#39;ordine seguente:

1. **Patch di sicurezza** fanno parte della base di codice statico di una versione di Adobe Commerce.
1. **Patch del compositore** da a `composer install` e `composer update` plug-in come [cweagans/compositore-patch](https://packagist.org/packages/cweagans/composer-patches).
1. Tutti **patch richieste** incluso nel [Patch cloud per Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) pacchetto.
1. Selezionato **patch di qualità** incluso nel [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Patch personalizzate** e le patch di supporto Adobe Commerce in `/m2-hotfixes` in ordine alfabetico in base al nome della patch.

   >[!IMPORTANT]
   >
   >Più patch si applicano, più complesso diventa il codice. Il codice complesso può rendere più difficile l’aggiornamento a una nuova versione di Adobe commerce e aumentare il costo totale di proprietà.

Se sei responsabile della gestione di più installazioni di Adobe Commerce, può essere difficile garantire che tutte le istanze abbiano installato lo stesso set di patch. Ogni installazione dispone di un proprio archivio Git, `/m2-hotfixes` directory e `composer.json` file. L&#39;unica garanzia di cui si dispone è che il **patch di sicurezza** e **patch richieste** per gli utenti cloud, sono tutti installati come parte della versione principale di Adobe Commerce.

Attualmente, non esiste un’unica soluzione centralizzata per questo problema, ma Composer offre un modo per colmare il divario. Il [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) consente di: [applicare patch dalle dipendenze](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Puoi creare un pacchetto Compositore che installa tutte le patch, quindi richiederlo in tutti i tuoi progetti.

Che copre **patch di sicurezza**, **patch richieste**, e **Patch del compositore**, ma per quanto riguarda le patch di qualità e il contenuto della `/m2-hotfixes` directory?

## Applicazione di patch e hotfix di qualità

È possibile installare patch di qualità sia sull&#39;infrastruttura cloud che nelle installazioni locali utilizzando `vendor/bin/magento-patches apply` comando. È necessario assicurarsi che `vendor/bin/magento-patches apply` comando eseguito dopo `composer install` operazioni.

>[!NOTE]
>
>Sull’infrastruttura cloud, puoi anche installare patch di qualità inserendole nel file `.magento.env.yaml` file. L’esempio qui descritto richiede l’utilizzo di `vendor/bin/magento-patches apply` comando.

È possibile specificare le patch da applicare nel `composer.json` file di un pacchetto di componenti Compositore personalizzato, quindi crea un pacchetto di plug-in che esegue il comando dopo `composer install` operazioni.

In sintesi, questo esempio di applicazione di patch centralizzata richiede la creazione di due pacchetti di Compositore personalizzati:

- **Pacchetto componenti:** `centralized-patcher`

   - Definisce l&#39;elenco delle patch di qualità e `m2-hotfixes` per installare
   - Richiede `centralized-patcher-composer-plugin` , che esegue `vendor/bin/magento-patches apply` comando dopo `composer install` operazioni

- **Pacchetto plug-in:** `centralized-patcher-composer-plugin`

   - Definisce un `CentralizedPatcher` Classe PHP che legge l&#39;elenco delle patch di qualità dal `centralized-patcher` pacchetto
   - Esegue il comando `vendor/bin/magento-patches apply` per installare l&#39;elenco delle patch di qualità dopo `composer install` operazioni

### `centralized-patcher`

Puoi creare un pacchetto di componenti Compositore (`centralized-patcher`) per gestire centralmente tutte le patch di qualità e `/m2-hotfixes` in tutte le installazioni di Adobe Commerce.

Il pacchetto del componente deve:

- Copia il contenuto del `/m2-hotfixes` in tutte le installazioni durante la distribuzione.
- Definire l&#39;elenco delle patch di qualità da installare.
- Esegui il `vendor/bin/magento-patches` per installare lo stesso elenco di patch di qualità in tutte le installazioni (utilizzando [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) pacchetto del plug-in come dipendenza).

Per creare `centralized-patcher` pacchetto componente:

1. Creare un `composer.json` file con i seguenti contenuti:

   >[!NOTE]
   >
   >Il `require` nell&#39;esempio seguente viene illustrato un attributo `require` dipendenza dal [pacchetto del plug-in](#centralized-patcher-composer-plugin) che è necessario creare più avanti in questo esempio.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Creare un `/m2-hotfixes` all&#39;interno del pacchetto e aggiungerlo al `map` attributo in `composer.json` file. Il `map` L&#39;attributo contiene i file da copiare da questo pacchetto nella directory principale del progetto di destinazione a cui si desidera applicare la patch.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >Il `centralized-patcher` copia il contenuto del pacchetto `/m2-hotfixes` nella directory m2-hotfixes del progetto di destinazione su `composer install`.  Poiché gli script di distribuzione cloud applicano gli hotfix m2 dopo `composer install`, tutti gli hotfix vengono installati dal meccanismo di distribuzione.

1. Definire le patch di qualità da installare in `quality-patches` attributo.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


Il `quality-patches` nell&#39;esempio di codice precedente contiene due patch del [elenco completo delle patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) come esempio.  Queste patch di qualità vengono installate in ogni progetto che richiede `centralized-patcher` pacchetto che utilizza `vendor/bin/magento-patches apply` comando.

A scopo di test, puoi creare una patch di esempio (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Posizionare i propri cerotti nella `m2-hotfixes` insieme alle patch ricevute direttamente dal supporto Adobe Commerce.

Un esempio di file patch (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Poiché in questo esempio viene utilizzato il metodo on-premise per installare le patch di qualità, è necessario assicurarsi che `vendor/bin/magento-patches apply` comando eseguito dopo `composer install` operazioni. Questo plug-in viene attivato dopo `composer install` operazioni, che esegue `vendor/bin/magento-patches apply` comando.

Per creare `centralized-patcher-compose-plugin` pacchetto componente:

1. Creare un `composer.json` file con i seguenti contenuti:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Creare un file PHP e definire un `CentralizedPatcher` classe per leggere l&#39;elenco delle patch di qualità dalla [`centralized-patcher`](#centralized-patcher) e installarli immediatamente dopo ogni `composer install` operazione.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Consulta la sezione [esempi di codice](#code-examples) per vedere in azione i due pacchetti descritti in questo esempio.


## Operazioni da eseguire con patch specifiche per il progetto

È possibile che esista uno scenario in cui solo il 95% delle patch è richiesto in tutti i progetti, mentre alcune patch si applicano solo a una specifica istanza. Il modo regolare per applicare la patch continua a funzionare. È possibile mantenere le patch specifiche del progetto in `/m2-hotfixes` e installare patch di qualità per progetto.

Se si utilizza questo approccio, **non** eseguire il commit di tutte le patch in `/m2-hotfixes` directory che sono state copiate nel progetto da `centralized-patcher` pacchetto di componenti. È possibile evitare commit accidentali aggiungendo `/m2-hotfixes` al tuo `.gitignore` file. Dopo aver aggiornato `.gitignore` file, ricorda che qualsiasi progetto-specifico `/m2-hotfixes` deve essere aggiunto utilizzando `git add –force` comando.

## Esecuzione di diverse versioni di Adobe Commerce

Assicurati di impostare la dipendenza corretta nel `centralized-patcher` pacchetto di componenti. Ad esempio, potrebbe essere necessario Adobe Commerce 2.4.5-p2 per una versione specifica del pacchetto, che fornisce solo patch compatibili con Adobe Commerce 2.4.5-p2. È possibile che sia disponibile un’altra versione del pacchetto compatibile con Adobe Commerce 2.4.4.

## Comprensione del risultato

Come per Adobe Commerce sull’infrastruttura cloud, questo articolo presuppone che il processo di distribuzione utilizzi `composer install` comando e non `composer update` o `git pull` per distribuire il nuovo codice sui server. Il flusso dell&#39;installazione centralizzata delle patch sarà quindi il seguente:

1. Installazione del compositore

   - Installa Adobe Commerce, incluse le patch funzionali e di sicurezza -p1 o -p2
   - Combina centralizzato `/m2-hotfixes` e patch di supporto con specifiche per il progetto `/m2-hotfixes` e patch di supporto
   - Applica tutte le patch installate con `cweagans/composer-patches` Pacchetto Compositore

1. Dopo `composer install`

   - Il plug-in Composer installa le patch di qualità centralizzate

1. Distribuzione

   - Le patch richieste e le patch di qualità specifiche del progetto vengono installate in base al `.magento.env.yaml` file (solo Adobe Commerce su progetti di infrastruttura cloud).
   - Patch personalizzate e patch di supporto da `/m2-hotfixes` vengono installate in ordine alfabetico in base al nome della patch.

In questo modo è possibile gestire centralmente tutte le patch per tutte le installazioni e garantire al meglio la sicurezza e la stabilità degli store Adobe Commerce. Per controllare lo stato della patch, utilizzare i metodi seguenti:

- [Progetti di infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Progetti on-premise](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Esempi di codice

- [Patch centralizzate nel Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Patch centralizzate in Adobe Commerce su infrastruttura cloud](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Plug-in Compositore patcher centralizzato](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Componente patcher centralizzato](https://github.com/AntonEvers/centralized-patcher)
