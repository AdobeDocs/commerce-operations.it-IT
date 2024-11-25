---
title: Best practice per la distribuzione delle patch su larga scala
description: Scopri in che modo l’applicazione di patch centralizzate per Adobe Commerce può aiutarti a gestire i progetti aziendali.
role: Developer
feature: Best Practices
badge: label="Con il contributo di Anton Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Con il contributo di Anton Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Best practice per la distribuzione delle patch di Adobe Commerce su larga scala

Se gestisci più installazioni di Adobe Commerce, [l&#39;applicazione di patch](../../../upgrade/patches/apply.md) può essere un processo complesso. _L&#39;applicazione centralizzata delle patch_ è una best practice per le aziende. Consente di applicare le patch corrette a tutte le installazioni di Adobe Commerce. Questo argomento spiega come ottenere la distribuzione centralizzata delle patch per tutti i tipi di [patch](../../../upgrade/patches/overview.md) di Adobe Commerce.

>[!NOTE]
>
>Il seguente contenuto è stato originariamente pubblicato nel post [Distribuzione di patch di Adobe Commerce su scala](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) sul blog di Adobe Tech. È stato modificato per concentrarsi sui passaggi e sugli esempi di codice per l’implementazione di una strategia di applicazione di patch centralizzata. Per ulteriori dettagli sui diversi tipi di patch qui descritti, consulta il post originale.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce locale

## Strategia

Poiché esistono molti tipi diversi di patch e molti modi per applicarle, come si fa a sapere quale patch viene applicata per prima? Maggiore è il numero di patch disponibili, maggiore è la possibilità che vengano applicate allo stesso file o alla stessa riga di codice. Le patch vengono applicate nell&#39;ordine seguente:

1. **Le patch di sicurezza** fanno parte della base di codice statico di una versione di Adobe Commerce.
1. **Patch compositore** tramite `composer install` e `composer update` plug-in come [cweagans/compositore-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Tutte le **patch richieste** incluse nel pacchetto [Patch cloud per Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html).
1. **patch di qualità** selezionate incluse in [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Patch personalizzate** e patch di supporto Adobe Commerce nella directory `/m2-hotfixes` in ordine alfabetico in base al nome della patch.

   >[!IMPORTANT]
   >
   >Più patch si applicano, più complesso diventa il codice. Il codice complesso può rendere più difficile l’aggiornamento a una nuova versione di Adobe commerce e aumentare il costo totale di proprietà.

Se sei responsabile della gestione di più installazioni di Adobe Commerce, può essere difficile garantire che tutte le istanze abbiano installato lo stesso set di patch. Ogni installazione dispone del proprio archivio Git, della directory `/m2-hotfixes` e del file `composer.json`. L&#39;unica garanzia di cui disponi è che le **patch di sicurezza** e le **patch richieste** per gli utenti cloud sono tutte installate come parte della versione principale di Adobe Commerce.

Attualmente, non esiste un’unica soluzione centralizzata per questo problema, ma Composer offre un modo per colmare il divario. Il pacchetto [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) ti consente di [applicare patch dalle dipendenze](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Puoi creare un pacchetto Compositore che installa tutte le patch, quindi richiederlo in tutti i tuoi progetti.

Copre **patch di sicurezza**, **patch richieste** e **patch compositore**, ma le patch di qualità e il contenuto della directory `/m2-hotfixes`?

## Applicazione di patch e hotfix di qualità

È possibile installare patch di qualità sia sull&#39;infrastruttura cloud che nelle installazioni locali utilizzando il comando `vendor/bin/magento-patches apply`. È necessario assicurarsi che il comando `vendor/bin/magento-patches apply` venga eseguito dopo `composer install` operazioni.

>[!NOTE]
>
>Nell&#39;infrastruttura cloud è inoltre possibile installare patch di qualità inserendole nel file `.magento.env.yaml` del progetto. L&#39;esempio qui descritto richiede l&#39;utilizzo del comando `vendor/bin/magento-patches apply`.

È possibile specificare le patch da applicare nel file `composer.json` di un pacchetto componente Compositore personalizzato, quindi creare un pacchetto di plug-in che esegua il comando dopo `composer install` operazioni.

In sintesi, questo esempio di applicazione di patch centralizzata richiede la creazione di due pacchetti di Compositore personalizzati:

- **Pacchetto componenti:** `centralized-patcher`

   - Definisce l&#39;elenco di patch di qualità e `m2-hotfixes` da installare
   - Richiede il pacchetto `centralized-patcher-composer-plugin`, che esegue il comando `vendor/bin/magento-patches apply` dopo `composer install` operazioni

- **Pacchetto plug-in:** `centralized-patcher-composer-plugin`

   - Definisce una classe PHP `CentralizedPatcher` che legge l&#39;elenco delle patch di qualità dal pacchetto `centralized-patcher`
   - Esegue il comando `vendor/bin/magento-patches apply` per installare l&#39;elenco delle patch di qualità dopo `composer install` operazioni

### `centralized-patcher`

È possibile creare un pacchetto del componente Compositore (`centralized-patcher`) per gestire centralmente tutte le patch di qualità e `/m2-hotfixes` in tutte le installazioni di Adobe Commerce.

Il pacchetto del componente deve:

- Copiare il contenuto della directory `/m2-hotfixes` in tutte le installazioni durante la distribuzione.
- Definire l&#39;elenco delle patch di qualità da installare.
- Eseguire il comando `vendor/bin/magento-patches` per installare lo stesso elenco di patch di qualità in tutte le installazioni utilizzando il pacchetto del plug-in [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) come dipendenza.

Per creare il pacchetto del componente `centralized-patcher`:

1. Creare un file `composer.json` con il seguente contenuto:

   >[!NOTE]
   >
   >L&#39;attributo `require` nell&#39;esempio seguente mostra una dipendenza `require` dal [pacchetto di plug-in](#centralized-patcher-composer-plugin) che è necessario creare più tardi in questo esempio.

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

1. Creare una directory `/m2-hotfixes` nel pacchetto e aggiungerla all&#39;attributo `map` nel file `composer.json`. L&#39;attributo `map` contiene i file da copiare da questo pacchetto nella radice del progetto di destinazione a cui si desidera applicare la patch.

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
   >Il pacchetto `centralized-patcher` copia il contenuto della directory `/m2-hotfixes` nella directory m2-hotfixes del progetto di destinazione in `composer install`.  Poiché gli script di distribuzione cloud applicano gli hotfix m2 dopo `composer install`, tutti gli hotfix vengono installati dal meccanismo di distribuzione.

1. Definire le patch di qualità da installare nell&#39;attributo `quality-patches`.

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


L&#39;attributo `quality-patches` nell&#39;esempio di codice precedente contiene due patch dall&#39;[elenco completo delle patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).  Queste patch di qualità vengono installate in ogni progetto che richiede il pacchetto `centralized-patcher` utilizzando il comando `vendor/bin/magento-patches apply`.

A scopo di test, è possibile creare una patch di esempio (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>È necessario inserire le proprie patch nella directory `m2-hotfixes` insieme alle patch ricevute direttamente dal supporto Adobe Commerce.

Esempio di file patch (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

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

Poiché questo esempio utilizza il metodo locale per installare le patch di qualità, è necessario assicurarsi che il comando `vendor/bin/magento-patches apply` venga eseguito dopo `composer install` operazioni. Questo plug-in viene attivato dopo `composer install` operazioni, che esegue il comando `vendor/bin/magento-patches apply`.

Per creare il pacchetto del componente `centralized-patcher-compose-plugin`:

1. Creare un file `composer.json` con il seguente contenuto:

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

1. Creare un file PHP e definire una classe `CentralizedPatcher` per leggere l&#39;elenco delle patch di qualità dal pacchetto del componente [`centralized-patcher`](#centralized-patcher) e installarle immediatamente dopo ogni operazione `composer install`.

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
>Consulta gli [esempi di codice](#code-examples) per vedere in azione i due pacchetti descritti in questo esempio.


## Operazioni da eseguire con patch specifiche per il progetto

È possibile che esista uno scenario in cui solo il 95% delle patch è richiesto in tutti i progetti, mentre alcune patch si applicano solo a una specifica istanza. Il modo regolare per applicare la patch continua a funzionare. È possibile mantenere le patch specifiche del progetto nella directory `/m2-hotfixes` e installare le patch di qualità per progetto.

Se si utilizza questo approccio, **non** eseguire il commit delle patch nella directory `/m2-hotfixes` copiate nel progetto dal pacchetto del componente `centralized-patcher`. È possibile evitare commit accidentali aggiungendo `/m2-hotfixes` al file `.gitignore`. Dopo aver aggiornato il file `.gitignore`, ricorda che qualsiasi `/m2-hotfixes` specifico per il progetto deve essere aggiunto utilizzando il comando `git add –force`.

## Esecuzione di diverse versioni di Adobe Commerce

Assicurarsi di impostare la dipendenza corretta nel pacchetto del componente `centralized-patcher`. Ad esempio, potrebbe essere necessario Adobe Commerce 2.4.5-p2 per una versione specifica del pacchetto, che fornisce solo patch compatibili con Adobe Commerce 2.4.5-p2. È possibile che sia disponibile un’altra versione del pacchetto compatibile con Adobe Commerce 2.4.4.

## Comprensione del risultato

Come per Adobe Commerce sull&#39;infrastruttura cloud, questo articolo presuppone che il processo di distribuzione utilizzi il comando `composer install` e non `composer update` o `git pull` per distribuire il nuovo codice ai server. Il flusso dell&#39;installazione centralizzata delle patch sarà quindi il seguente:

1. Installazione del compositore

   - Installa Adobe Commerce, incluse le patch funzionali e di sicurezza -p1 o -p2
   - Combina `/m2-hotfixes` centralizzato e patch di supporto con `/m2-hotfixes` specifico per il progetto e patch di supporto
   - Applica tutte le patch installate con il pacchetto Compositore `cweagans/composer-patches`

1. Dopo `composer install`

   - Il plug-in Composer installa le patch di qualità centralizzate

1. Distribuzione

   - Le patch richieste e le patch di qualità specifiche del progetto vengono installate in base al file `.magento.env.yaml` (solo progetti Adobe Commerce su infrastrutture cloud).
   - Le patch personalizzate e quelle di supporto della directory `/m2-hotfixes` vengono installate in ordine alfabetico in base al nome della patch.

In questo modo è possibile gestire centralmente tutte le patch per tutte le installazioni e garantire al meglio la sicurezza e la stabilità degli store Adobe Commerce. Per controllare lo stato della patch, utilizzare i metodi seguenti:

- [Progetti infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Progetti on-premise](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Esempi di codice

- [Patch centralizzate nel Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Patch centralizzate in Adobe Commerce sull&#39;infrastruttura cloud](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Plug-in del Compositore patch centralizzato](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Componente patch centralizzato](https://github.com/AntonEvers/centralized-patcher)
