---
title: Funzionamento delle patch
description: Scopri i diversi tipi di patch per Adobe Commerce e come funzionano.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Funzionamento delle patch

>[!WARNING]
>
>Si consiglia vivamente di eseguire il test di tutte le patch in un ambiente di staging o di sviluppo prima di distribuirle in produzione. Si consiglia inoltre di eseguire il backup dei dati prima di applicare una patch. Consulta [Backup e ripristino del file system](../../installation/tutorials/backup.md).

I file patch (o diff) sono file di testo che contengono una nota:

- File da modificare.
- Il numero di riga per iniziare la modifica e il numero di righe da modificare.
- Il nuovo codice da scambiare.

Quando viene eseguito il programma patch, il file viene letto e vengono apportate le modifiche specificate ai file.

Esistono tre tipi di patch:

- **Hotfix**- Patch pubblicate nell&#39;Adobe [Centro sicurezza](https://magento.com/security/patches).
- **Singole patch**- Patch create e distribuite su base individuale dal supporto Adobe Commerce.
- **Patch personalizzate**- Patch non ufficiali che è possibile creare da un commit Git.

## Hotfix

Gli hotfix sono patch che presentano problemi di sicurezza ad alto impatto o problemi di qualità che interessano molti commercianti. Queste correzioni vengono applicate alla versione patch successiva per la versione secondaria applicabile. Adobe rilascia gli hotfix in base alle esigenze.

Puoi trovare gli hotfix in [Centro sicurezza](https://magento.com/security/patches). Seguire le istruzioni riportate nella pagina per scaricare il file di patch, in base alla versione e al tipo di installazione. Utilizza il [riga di comando](../patches/apply.md#) o [Compositore](../patches/apply.md) per applicare patch di correzione rapida.

>[!NOTE]
>
>Gli hotfix possono contenere modifiche non compatibili con le versioni precedenti.

## Singole patch

Le singole patch contengono correzioni di qualità a basso impatto per un problema specifico. Queste correzioni sono applicate alla versione secondaria supportata più di recente (ad esempio, 2.4.x), ma potrebbero mancare nella versione secondaria supportata precedente (ad esempio, 2.3.x). Adobe rilascia singole patch in base alle esigenze.

Utilizza il [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} per applicare singole patch.

>[!NOTE]
>
>Le singole patch non contengono modifiche non compatibili con le versioni precedenti.

## Patch personalizzate

A volte ci vuole un po’ di tempo perché il team ingegneristico Adobe includa una correzione di bug effettuata su GitHub in una versione di Adobe Commerce o Magento Open Source Composer. Nel frattempo, puoi creare una patch da GitHub e utilizzare [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) per applicarlo all’installazione basata su Compositore.

Utilizza il [riga di comando](apply.md#command-line) o [Compositore](apply.md#composer) per applicare patch personalizzate.

Esistono diversi modi per creare file di patch personalizzati. L’esempio seguente si concentra sulla creazione di una patch da un commit Git noto.

Per creare una patch personalizzata:

1. Creare un `patches/composer` nel progetto locale.
1. Identifica il commit GitHub o la richiesta di pull da utilizzare per la patch. In questo esempio viene utilizzato [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) commit, collegato al problema GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Aggiungi `.patch` o `.diff` estensioni dell&#39;URL di commit. Utilizzare `.diff` per un file di dimensioni inferiori. Ad esempio: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Salvare la pagina come file in `patches/composer` directory. Ad esempio: `github-issue-6474.diff`.
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

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Riga di comando](/help/upgrade/patches/apply.md#command-line)
- [Compositore](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Per applicare una patch a un progetto di infrastruttura cloud di Adobe Commerce, consulta [Applicare le patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nel _Guida di Commerce su Cloud_.
