---
title: Archiviazione remota per Commerce su infrastruttura cloud
description: Consulta le linee guida per la configurazione dell’archiviazione remota per Adobe Commerce sull’infrastruttura cloud.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Configurare l’archiviazione remota per l’infrastruttura Commerce on Cloud

A partire dal `ece-tools` 2002.1.5, è possibile utilizzare una variabile di ambiente per abilitare il modulo di Archiviazione remota; tuttavia, il modulo di Archiviazione remota dispone di _limitato_ supporto per Adobe Commerce su infrastruttura cloud. L&#39;Adobe non è in grado di risolvere completamente i problemi relativi al servizio adattatore di archiviazione di terze parti.

## Variabile di ambiente

Il `REMOTE_STORAGE` viene utilizzata durante il [fase di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) di un progetto di infrastruttura cloud.

### `REMOTE_STORAGE`

- **Predefinito**—_Non impostato_
- **Versione**—Commerce 2.4.2 e versioni successive

Configurare un _scheda di storage_ per memorizzare i file multimediali in un contenitore di archiviazione remota persistente utilizzando un servizio di archiviazione, ad esempio AWS S3. Abilita il modulo Archiviazione remota per migliorare le prestazioni nei progetti Cloud con configurazioni complesse e multiserver che devono condividere le risorse. Di seguito è riportato un esempio di configurazione dell&#39;archiviazione remota utilizzando `.magento.env.yaml` file:

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

### Imposta variabile con Cloud CLI

Imposta il `REMOTE_STORAGE` variabile come [variabile a livello di ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) in modo che i file non vengano condivisi tra gli ambienti di produzione, staging e integrazione. L&#39;impostazione delle variabili a livello di ambiente offre la flessibilità di utilizzare solo lo storage remoto in determinati ambienti, ad esempio escludendo l&#39;utilizzo dell&#39;ambiente di integrazione dello storage remoto.

**Per aggiungere la variabile di archiviazione remota utilizzando Cloud CLI**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Questo crea un `REMOTE_STORAGE` con la configurazione JSON specificata. Il `REMOTE_STORAGE` La variabile richiede una stringa JSON per configurare l’archiviazione remota. Di seguito è riportato un esempio di configurazione JSON:

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

Dopo aver creato la configurazione e la distribuzione, i registri di distribuzione devono includere informazioni sulla configurazione dell’archiviazione remota, ad esempio `INFO: Remote storage driver set to: "aws-s3"`

### Imposta variabile con Project Web Interface

In alternativa, è possibile utilizzare Project Web Interface per aggiungere la variabile all&#39;ambiente appropriato.

**Per aggiungere la variabile di archiviazione remota tramite Project Web Interface**:

1. In _Interfaccia Web di Project_, seleziona l’ambiente da sinistra.

1. Fai clic su **Configurare l’ambiente** icona.

1. In _Configurare l’ambiente_ , fare clic sul pulsante **Variabili** scheda.

1. Clic **Aggiungi variabile**.

1. In _Nome_ campo, immetti `REMOTE_STORAGE`

1. In _Valore_ , aggiungi la configurazione JSON.

1. Seleziona **Valore JSON** e **Sensibile**; deseleziona **Ereditabilità per ambienti figlio**.

1. Clic **Aggiungi variabile**.

### Usa autenticazione facoltativa

Il `key` e `secret` sono facoltativi. Quando crei la variabile, puoi nascondere `key` e `secret` selezionando la `sensitive` opzione. Con questa impostazione, i valori non sono visibili nell’interfaccia web. Consulta [Visibilità variabile](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) nel _Guida di Commerce su infrastruttura cloud_.

Se desideri utilizzare un metodo di autenticazione diverso, ometti la `key` e `secret` dalla configurazione JSON,. Configura il metodo di autenticazione alternativo e verifica che il server sia autorizzato per il bucket S3.

### Sincronizza l&#39;archiviazione remota

Dopo aver abilitato il modulo Archiviazione remota, sincronizzare i file multimediali correnti con il percorso dell&#39;archivio remoto.

**Per avviare la sincronizzazione**:

1. Utilizzare SSH per accedere all&#39;ambiente remoto con lo storage remoto configurato.

1. Avvia la sincronizzazione.

```bash
bin/magento remote-storage:sync 
```

## Configurazione rapida

Se scegli di utilizzare la soluzione di archiviazione remota con un progetto di infrastruttura cloud Adobe Commerce on, utilizza [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) linee guida in _Fastly_ per garantire il funzionamento di Fastly Image Optimization con AWS S3.

Preparati con il [Credenziali rapide](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Nei progetti Pro, utilizza SSH per connettersi al server e ottenere le credenziali Fastly dal `/mnt/shared/fastly_tokens.txt` file. Gli ambienti di staging e produzione dispongono di credenziali univoche. È necessario ottenere le credenziali per ogni ambiente.

Continua a configurare l’archiviazione remota per i progetti cloud con le seguenti attività:

1. Configurare un [Integrazione back-end rapida](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crea logica VCL per [Autenticazione AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Crea logica VCL per [richieste back-end al bucket AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
