---
title: Disattiva output modulo
description: Scopri come disabilitare l’output del modulo.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Disattiva output modulo

Per impostazione predefinita, tutti i moduli sono configurati in modo che l’output del modulo possa essere scritto in una visualizzazione. La disattivazione dell&#39;output offre un modo per disabilitare essenzialmente un modulo che non può essere disabilitato a causa di dipendenze complesse.

Ad esempio, il `Customer` il modulo dipende dal `Review` il modulo `Review` Impossibile disabilitare il modulo. Tuttavia, se non si desidera che i clienti forniscano le revisioni, è possibile disattivare l&#39;output dal `Review` modulo .

>[!INFO]
>
>Se un esercente ha utilizzato l’amministratore per disabilitare l’output del modulo in una versione precedente, è necessario configurare manualmente il sistema per migrare queste impostazioni.

La disattivazione dell&#39;output viene eseguita nelle seguenti classi:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>La disattivazione dell&#39;output del modulo non disattiva il modulo. Il modulo rimane abilitato e funzionante, ma non viene eseguito il rendering di blocchi, pagine o campi sul front-end o sul backend.

## Disattiva l’output del modulo in un’implementazione della pipeline

Per disabilitare l’output del modulo nella distribuzione della pipeline o in qualsiasi altra distribuzione, con più istanze dell’applicazione Commerce:

1. Modifica le `Backend` del modulo `config.xml` file.
1. Esporta le modifiche di configurazione.

### Modifica le `Backend` modulo `config.xml` file

1. Archivia l&#39;originale `config.xml` file.
1. Aggiungi righe simili alle seguenti `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` file , direttamente sotto `<default>` elemento:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Qui:

   - `<modules_disable_output>` contiene un elenco di moduli.
   - `<Magento_Newsletter></Magento_Newsletter>` specifica il modulo per cui disabilitare l&#39;output.
   - `1` è il flag che disabilita l&#39;output per `Magento_Newsletter` modulo .

Come risultato di questa configurazione, i clienti non possono più registrarsi per ricevere le newsletter.

### Esporta le modifiche alla configurazione

Esegui il comando seguente per esportare le modifiche di configurazione:

```bash
bin/magento app:config:dump
```

I risultati vengono scritti nella `<Magento_install_dir>/app/etc/config.php` file.

Quindi, cancella la cache per abilitare la nuova impostazione:

```bash
bin/magento cache:clean config
```

Vedi [Esporta la configurazione](../cli/export-configuration.md).

## Disattiva l&#39;output del modulo in una distribuzione semplice

La procedura per disabilitare l’output del modulo in una singola istanza di Commerce è più semplice perché le modifiche non devono essere distribuite.

1. Archivia l&#39;originale `<Magento_install_dir>/app/etc/config.php` file.
1. Aggiungi il `advanced` e `modules_disable_output` sezioni `config.php` file (se non esistono):

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

In questo esempio, l&#39;output per `Magento_Review` Il modulo è stato disabilitato e i clienti non possono più esaminare i prodotti.
Per riattivare l&#39;output, impostare il valore su `0`.
