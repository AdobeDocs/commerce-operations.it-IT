---
title: Disattiva output modulo
description: Scopri come disabilitare l’output del modulo.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: fee09845777e23717e618ac57df4158d6b172d4f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Disattiva output modulo

Per impostazione predefinita, tutti i moduli sono configurati in modo che l’output del modulo possa essere scritto in una vista. La disattivazione dell’output offre un modo per disabilitare essenzialmente un modulo che non può essere disabilitato a causa di dipendenze rigide.

Ad esempio, il modulo `Customer` dipende dal modulo `Review`, pertanto non è possibile disabilitare il modulo `Review`. Tuttavia, se non si desidera che i clienti forniscano recensioni, è possibile disattivare l&#39;output dal modulo `Review`.

>[!INFO]
>
>Se un esercente ha utilizzato l’amministratore per disabilitare l’output del modulo in una versione precedente, devi configurare manualmente il sistema per migrare queste impostazioni.

La disattivazione dell&#39;output viene eseguita nelle seguenti classi:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>La disabilitazione dell’output del modulo non comporta la disabilitazione del modulo. Il modulo rimane abilitato e funzionante, ma non viene eseguito il rendering di blocchi, pagine o campi sul front-end o sul back-end.

## Disattivare l’output del modulo in una distribuzione della pipeline

Per disabilitare l’output del modulo nella distribuzione della pipeline o in qualsiasi altra distribuzione, con più istanze dell’applicazione Commerce:

1. Modificare il file `config.xml` del modulo `Backend`.
1. Esporta le modifiche di configurazione.

### Modifica il file `config.xml` del modulo `Backend`

1. Archivia il file `config.xml` originale.
1. Aggiungere righe simili alle seguenti al file `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`, direttamente sotto l&#39;elemento `<default>`:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Qui:

   - `<modules_disable_output>` contiene un elenco di moduli.
   - `<Magento_Newsletter></Magento_Newsletter>` specifica per quale modulo disabilitare l&#39;output.
   - `1` è il flag che disabilita l&#39;output per il modulo `Magento_Newsletter`.

Come risultato di questa configurazione, i clienti non possono più registrarsi per ricevere newsletter.

### Esportare le modifiche di configurazione

Esegui il comando seguente per esportare le modifiche di configurazione:

```bash
bin/magento app:config:dump
```

I risultati vengono scritti nel file `<Magento_install_dir>/app/etc/config.php`.

Quindi, cancella la cache per abilitare la nuova impostazione:

```bash
bin/magento cache:clean config
```

Vedere [Esportare la configurazione](../cli/export-configuration.md).

## Disattivare l’output del modulo in una distribuzione semplice

La procedura per disabilitare l’output del modulo su una singola istanza di Commerce è più semplice perché le modifiche non devono essere distribuite.

1. Archivia il file `<Magento_install_dir>/app/etc/config.php` originale.
1. Aggiungere le sezioni `advanced` e `modules_disable_output` al file `config.php` (se non esistono):

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

In questo esempio, l&#39;output per il modulo `Magento_Review` è stato disabilitato e i clienti non possono più esaminare i prodotti.

### Riattiva output modulo

Per riabilitare l&#39;output, impostare il valore del modulo su `0` oppure rimuovere la riga o il modulo dal file `config.php`.
