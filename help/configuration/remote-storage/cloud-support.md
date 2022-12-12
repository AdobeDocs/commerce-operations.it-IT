---
title: Archiviazione remota per Commerce su infrastruttura cloud
description: Consulta le indicazioni su come configurare l’archiviazione remota per Adobe Commerce sull’infrastruttura cloud.
source-git-commit: 0653d90d92e264b62fcc648f2b1307c013e9be54
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Configurare lo storage remoto per l’infrastruttura Commerce su Cloud

A partire da `ece-tools` package 2002.1.5, è possibile utilizzare una variabile di ambiente per abilitare il modulo di archiviazione remota; tuttavia, il modulo di archiviazione remota ha _limitato_ supporto su Adobe Commerce sull’infrastruttura cloud. Impossibile risolvere completamente i problemi relativi al servizio dell&#39;adattatore di archiviazione di terze parti.

## Variabile di ambiente

La `REMOTE_STORAGE` viene utilizzata durante la [fase di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) di un progetto di infrastruttura cloud.

### `REMOTE_STORAGE`

- **Predefinito**—_Non impostato_
- **Versione**—Commerce 2.4.2 e successivi

Configura un _scheda di memoria_ per memorizzare i file multimediali in un contenitore di archiviazione remoto persistente utilizzando un servizio di archiviazione, ad esempio AWS S3. Attiva il modulo Archiviazione remota per migliorare le prestazioni sui progetti Cloud con configurazioni complesse e con più server che devono condividere le risorse. Di seguito è riportato un esempio di configurazione dell&#39;archiviazione remota utilizzando `.magento.env.yaml` file:

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Imposta la variabile con Cloud CLI

Imposta la `REMOTE_STORAGE` come variabile [variabile a livello di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) in modo che i file non vengano condivisi tra ambienti di produzione, staging e integrazione. L&#39;impostazione delle variabili a livello di ambiente offre la flessibilità di utilizzare solo lo storage remoto in ambienti specifici, ad esempio escludendo l&#39;utilizzo dell&#39;ambiente di integrazione dello storage remoto.

**Per aggiungere la variabile di archiviazione remota utilizzando Cloud CLI**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Questo crea un `REMOTE_STORAGE` con la configurazione JSON specificata. La `REMOTE_STORAGE` prende una stringa JSON per configurare l&#39;archiviazione remota. Di seguito è riportato un esempio di configurazione JSON.

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

Dopo aver creato la configurazione e implementato, i registri di distribuzione devono includere informazioni sulla configurazione dello storage remoto, ad esempio `INFO: Remote storage driver set to: "aws-s3"`

### Imposta variabile con interfaccia Web di Project

In alternativa, è possibile utilizzare l&#39;interfaccia Web di Project per aggiungere la variabile all&#39;ambiente appropriato.

**Aggiunta della variabile di archiviazione remota tramite l&#39;interfaccia Web di Project**:

1. In _Interfaccia Web progetto_, seleziona l’ambiente da sinistra.

1. Fai clic sul pulsante **Configurare l’ambiente** icona.

1. In _Configurare l’ambiente_ visualizzazione, fai clic su **Variabili** scheda .

1. Fai clic su **Aggiungi variabile**.

1. In _Nome_ campo, immettere `env:REMOTE_STORAGE`

1. In _Valore_ aggiungi la configurazione JSON.

1. Seleziona **Valore JSON** e **Sensibile**; deseleziona **Ereditabile per ambienti figlio**.

1. Fai clic su **Aggiungi variabile**.

### Usa autenticazione opzionale

La `key` e `secret` sono facoltativi. Quando crei la variabile , puoi nascondere la variabile `key` e `secret` selezionando la `sensitive` opzione . Con questa impostazione, i valori non sono visibili nell’interfaccia web. Vedi [Visibilità variabile](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) in _Guida a Commerce on Cloud Infrastructure_.

Se desideri utilizzare un metodo di autenticazione diverso, ometti il `key` e `secret` dalla configurazione JSON, . Configura il metodo di autenticazione alternativo e verifica che il server sia autorizzato al bucket S3.

### Sincronizzazione dell&#39;archiviazione remota

Dopo aver abilitato il modulo Archiviazione remota, sincronizzare i file multimediali correnti con la posizione dell&#39;archivio remoto.

**Per avviare la sincronizzazione**:

1. Utilizzare SSH per accedere all&#39;ambiente remoto con archiviazione remota configurata.

1. Avvia la sincronizzazione.

```bash
bin/magento remote-storage:sync 
```

## Configurazione definitiva

Se scegli di utilizzare la soluzione di archiviazione remota con un progetto di infrastruttura cloud Adobe Commerce, utilizza la [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) guida _Favoloso_ per garantire il funzionamento di Flast Image Optimization con AWS S3.

Preparati con il tuo [Credenziali definitive](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Nei progetti Pro, utilizza SSH per connetterti al server e ottenere le credenziali Flast dal `/mnt/shared/fastly_tokens.txt` file. Gli ambienti di staging e produzione dispongono di credenziali univoche. Devi ottenere le credenziali per ogni ambiente.

Continua a configurare l’archiviazione remota per i progetti cloud con le seguenti attività:

1. Configura un [Integrazione di back-end](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crea logica VCL per [Autenticazione AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Crea logica VCL per [richieste di back-end al bucket AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
