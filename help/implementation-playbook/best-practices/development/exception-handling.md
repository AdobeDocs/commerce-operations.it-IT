---
title: Best practice per la gestione delle eccezioni
description: Scopri i metodi consigliati per la registrazione delle eccezioni durante lo sviluppo di progetti Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Best practice per la gestione delle eccezioni

Se non viene scritta un&#39;eccezione in `exception.log` file con il modello di eccezione come contesto, non viene riconosciuto e analizzato correttamente in New Relic o in altri archivi di registro compatibili con il monologo PSR-3. La registrazione solo di una parte dell’eccezione (o la registrazione nel file errato) causa bug nella produzione quando le eccezioni vengono ignorate.

## Gestione delle eccezioni corretta

L&#39;elenco di controllo seguente fornisce alcuni esempi per dimostrare la corretta gestione delle eccezioni.

### ![corretto](../../../assets/yes.svg) Scrivi nel registro eccezioni

Scrivere nel registro eccezioni utilizzando il modello seguente, indipendentemente da ulteriori azioni, a meno che non vi sia un motivo valido per non farlo.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Questo approccio salva automaticamente `$e->getMessage` al messaggio di registro e al `$e` oggetto al contesto, seguendo la [Contesto standard PSR-3](https://www.php-fig.org/psr/psr-3/#13-context). Questa operazione viene eseguita in `\Magento\Framework\Logger\Monolog::addRecord`.

### ![corretto](../../../assets/yes.svg) Disattiva segnali

Disattiva i segnali non registrando le eccezioni che fanno parte del flusso di operazioni previsto. Non è necessaria alcuna azione di follow-up quando si verifica l’eccezione, pertanto non è necessario registrarla e analizzarla quando si verifica. Aggiungete un commento che indica il motivo dell&#39;audio disattivato e che è intenzionale. Combina con `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![corretto](../../../assets/yes.svg) Eccezioni di downgrade

Eseguire il downgrade delle eccezioni seguendo la [Contesto standard PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![corretto](../../../assets/yes.svg) La registrazione viene sempre prima

Come best practice, la registrazione viene sempre prima nel codice per evitare casi in cui viene generata un’altra eccezione o un errore irreversibile prima di scrivere nel registro.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![corretto](../../../assets/yes.svg) Registra i messaggi e l&#39;intera traccia dell&#39;eccezione

Registra i messaggi e l&#39;intera traccia dell&#39;eccezione seguendo [Contesto standard PSR-3](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Gestione delle eccezioni non corretta

Gli esempi seguenti mostrano una gestione errata delle eccezioni.

### ![errato](../../../assets/no.svg) Logica prima della registrazione

La logica prima della registrazione può causare un’altra eccezione o un errore irreversibile, che impedisce la registrazione dell’eccezione e deve essere sostituita da [esempio corretto](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![errato](../../../assets/no.svg) Vuoto `catch`

Vuoto `catch` I blocchi possono essere un segno di disattivazione involontaria e devono essere sostituiti da [esempio corretto](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![errato](../../../assets/no.svg) Doppia localizzazione

Se l&#39;eccezione localizzata rilevata non è ancora stata tradotta, risolvere il problema nel punto in cui viene generata la prima volta.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![errato](../../../assets/no.svg) Registra messaggi e traccia in diversi file di registro

Il codice seguente registra erroneamente l&#39;analisi dello stack per un&#39;eccezione come stringa in un file di registro.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Questo approccio introduce interruzioni di riga nel messaggio, non conforme a PSR-3. L&#39;eccezione, inclusa la traccia dello stack, deve far parte del contesto del messaggio per garantire che venga salvata correttamente con il messaggio in New Relic o in un altro archivio di registro compatibile con il monologo PSR-3.

Per risolvere il problema, sostituisci il codice seguendo gli esempi corretti mostrati nella [Scrivi nel registro eccezioni](#write-to-the-exception-log) o [Eccezioni di downgrade](#downgrade-exceptions).

### ![errato](../../../assets/no.svg) Eccezioni di downgrade senza contesto

L’eccezione viene ridotta a errore, che non consente la trasmissione di un oggetto, ma solo di una stringa, da cui deriva `getMessage()`. Questo causa la perdita della traccia e deve essere sostituito dagli esempi corretti mostrati in [Scrivi nel registro eccezioni](#write-to-the-exception-log) o [Eccezioni di downgrade](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![errato](../../../assets/no.svg) Registra solo il messaggio nel registro eccezioni

Invece di passare l’oggetto `$e`, solo `$e->getMessage()` è stato superato. Questo causa la perdita della traccia e deve essere sostituito dagli esempi corretti mostrati [Scrivi nel registro eccezioni](#write-to-the-exception-log) o [Eccezioni di downgrade](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![errato](../../../assets/no.svg) Mancante `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Omissione del `phpcs:ignore` line attiva un avviso in PHPCS e non deve trasmettere il CI. Questo deve essere sostituito dall&#39;esempio corretto mostrato nella [Disattiva segnali](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
