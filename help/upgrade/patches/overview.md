---
title: Funzionamento delle patch
description: Scopri i diversi tipi di patch per Adobe Commerce e Magenti Open Source e come funzionano.
source-git-commit: 38b054bbae8ba116557ce367c8397c646c837558
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Funzionamento delle patch

>[!WARNING]
>
>È consigliabile testare tutte le patch in un ambiente di staging o di sviluppo prima di distribuirle in produzione. Si consiglia inoltre vivamente di eseguire il backup dei dati prima di applicare una patch. Vedi [Eseguire il backup e il rollback del file system](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

I file di patch (o diff) sono file di testo che annotano:

- File da modificare.
- Numero della riga per iniziare la modifica e numero di righe da modificare.
- Il nuovo codice da scambiare.

Quando il [patch](https://en.wikipedia.org/wiki/Patch_(Unix)) viene eseguito, il file viene letto e vengono apportate le modifiche specificate ai file.

Esistono tre tipi di patch:

- **Hotfix**- Patch pubblicate da Adobe nel [Centro sicurezza PC](https://magento.com/security/patches).
- **Patch singole**: patch create e distribuite dal supporto Adobe Commerce su base individuale.
- **Patch personalizzate**- Patch non ufficiali che è possibile creare da un commit git.

## Hotfix

Gli hotfix sono patch che contengono correzioni di qualità o di sicurezza ad alto impatto che interessano molti merchants. Queste correzioni vengono applicate alla prossima versione della patch per la versione secondaria applicabile. Adobe rilascia gli hotfix in base alle esigenze.

Puoi trovare gli hotfix nella sezione [Centro sicurezza PC](https://magento.com/security/patches). Segui le istruzioni riportate nella pagina per scaricare il file della patch, a seconda della versione e del tipo di installazione. Utilizza la [riga di comando](../patches/apply.md#) o [Compositore](../patches/apply.md) per applicare patch hotfix.

>[!NOTE]
>
>Le hotfix possono contenere modifiche incompatibili con le versioni precedenti.

## Patch singole

Le singole patch contengono correzioni di qualità a basso impatto per un problema specifico. Queste correzioni vengono applicate alla versione minore supportata più di recente (ad esempio, 2.4.x), ma potrebbero mancare dalla versione secondaria supportata precedente (ad esempio, 2.3.x). Adobe rilascia le singole patch in base alle esigenze.

Utilizza la [Strumento Patch di qualità](https://devdocs.magento.com/quality-patches/tool.html) applicare patch singole.

>[!NOTE]
>
>Le singole patch non contengono modifiche incompatibili con le versioni precedenti.

## Patch personalizzate

A volte ci vuole un po&#39; di tempo prima che il team di ingegneria di Adobe includa una correzione di bug eseguita su GitHub in una versione di Adobe Commerce o del Compositore di Magento Open Source. Nel frattempo, puoi creare una patch da GitHub e utilizzare il [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) plug-in per applicarlo all&#39;installazione basata su Composer.

Utilizza la [riga di comando] o [Compositore] per applicare patch personalizzate.

Esistono molti modi per creare file di patch personalizzati. L’esempio seguente si concentra sulla creazione di una patch da un commit git noto.

Per creare una patch personalizzata:

1. Crea un `patches/composer` nel progetto locale.
1. Identifica la richiesta di commit o pull GitHub da utilizzare per la patch. In questo esempio viene utilizzato [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) commit, collegato al problema GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Aggiungi `.patch` o `.diff` estensioni dell&#39;URL di commit. Utilizzo `.diff` per file di dimensioni inferiori. Ad esempio: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Salva la pagina come file nel `patches/composer` directory. Ad esempio: `github-issue-6474.diff`.
1. Modifica il file e rimuovi `app/code/<VENDOR>/<PACKAGE>` da tutti i percorsi in modo che siano relativi al `vendor/<VENDOR>/<PACKAGE>` directory.

   >[!NOTE]
   >
   >Gli editor di testo che rimuovono automaticamente gli spazi vuoti finali o aggiungono nuove righe possono interrompere la patch. Utilizza un semplice editor di testo per apportare queste modifiche.

L’esempio seguente mostra il file DIFF menzionato in precedenza dopo la rimozione di tutte le istanze di `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();
 
                 return this;
             },
```

## Applicazione delle patch

È possibile applicare le patch utilizzando uno dei seguenti metodi:

- [Strumento Patch di qualità](https://devdocs.magento.com/quality-patches/tool.html)
- [Riga di comando](../patches/apply.md#command-line)
- [Compositore](../patches/apply.md#composer)

>[!NOTE]
>
>Per applicare una patch a un progetto di infrastruttura cloud Adobe Commerce, vedi [Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) in _Guida a Cloud_.
