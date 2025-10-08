---
title: Evidenziatore URN
description: Scopri come impostare l’evidenziazione URN nell’IDE per lo sviluppo Adobe Commerce. Scopri la configurazione dello schema XSD e l’ottimizzazione dello sviluppo.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Panoramica dell’evidenziatore URN

{{file-system-owner}}

Il codice Commerce fa riferimento a tutti gli schemi XSD come [URN (Uniform Resource Names)](https://www.ietf.org/rfc/rfc2141.txt). Se stai sviluppando codice e devi fare riferimento a XSD, questo comando configura l’ambiente di sviluppo integrato (IDE) per riconoscere ed evidenziare gli URN. Questo semplifica lo sviluppo.

Per impostazione predefinita, un IDE come PhpStorm non è configurato per riconoscere gli URN e, di conseguenza, vengono visualizzati in rosso come segue:

![PhpStorm non configurato per riconoscere URN](../../assets/configuration/urn-before.png)

Il comando `bin/magento dev:urn-catalog:generate` consente all&#39;IDE (attualmente solo PhpStorm e Visual Studio Code) di riconoscere ed evidenziare gli URN come segue:

![Abilita IDE per riconoscere URN](../../assets/configuration/urn-after.png)

In particolare, questo comando crea la seguente configurazione PhpStorm:

![Esempio di configurazione PhpStorm](../../assets/configuration/urn-settings.png)

## Configurare l’IDE

Attualmente sono supportati solo PhpStorm e Visual Studio Code.

Sintassi del comando:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Dove `<path>` è il percorso del file PhpStorm `misc.xml`, che si trova rispetto alla directory principale del progetto. In genere, `<path>` è `.idea/misc.xml`.

>[!INFO]
>
>Per mantenere aggiornati &quot;Schemi e DTD&quot;, eseguire il comando `dev:urn-catalog:generate` ogni volta che si aggiungono, modificano o rimuovono moduli di Commerce 2 contenenti `*.xsd` file.
