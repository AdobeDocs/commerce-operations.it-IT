---
title: Ottieni il software Adobe Commerce
description: Scopri come scaricare il software Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Ottieni il software Adobe Commerce

Sei tra i 240.000 commercianti in tutto il mondo che hanno dato fiducia al nostro software di eCommerce. Sono state raccolte alcune informazioni per aiutarti a iniziare con l’installazione.

## Come ottenere il software

Controlla la disponibilità di nuove funzionalità e versioni interessanti e scopri come ottenerle nella [pagina sulla disponibilità del prodotto](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

Per informazioni introduttive sull’installazione di Adobe Commerce, consulta la tabella seguente.

<table>
    <tbody>
        <tr>
            <th>Esigenze dell’utente</th>
            <th>Descrizione</th>
            <th>Passaggi di installazione e aggiornamento di alto livello</th>
            <th>Collegamento per iniziare</th>
        </tr>
    <tr>
        <td><p>Integratore, packager</p></td>
        <td><p>Vuole il controllo completo su tutti i componenti installati, ha accesso al server applicazioni, altamente tecnico, potrebbe ricompilare Magento Open Source con altri componenti.</p>
        </td>
        <td><ol><li>Crea un Compositore <em>progetto</em> contenente l'elenco dei componenti da utilizzare.</li>
            <li>Utilizza Composer per aggiornare le dipendenze del pacchetto; utilizza <code>composer create-project</code> per ottenere il metapackage Composer.</li>
            <li>Installa l'applicazione utilizzando la <a href="../advanced.md">riga di comando</a>.</li>
        <li>Aggiorna l'applicazione e le estensioni utilizzando la <a href="../../upgrade/implementation/perform-upgrade.md">riga di comando</a>.</li></ol></td>
        <td><p><a href="../composer.md">Ottieni il metapacchetto</a></p></td>
    </tr>
    <tr>
        <td><p>Sviluppatore partecipante</p></td>
        <td><p>Contribuisce alla base di codice di Magento Open Source, ai file bug e personalizza l’applicazione. Estremamente tecnico, dispone di un proprio server di sviluppo, comprende Composer e GitHub.</p>
            <p><em>impossibile</em> utilizzare l'applicazione in un ambiente di produzione.</p>
      <p>È necessario eseguire l'aggiornamento utilizzando <a href="../../upgrade/developer/git-installs.md">Compositore e comandi Git</a>.</p></td>
        <td><ol><li>Clona l’archivio GitHub.</li>
            <li>Utilizza Compositore per aggiornare le dipendenze del pacchetto.</li>
            <li>Installa l'applicazione utilizzando <a href="../advanced.md">riga di comando</a>.</li>
            <li>Aggiorna l'applicazione utilizzando <a href="../../upgrade/developer/git-installs.md">Compositore e comandi Git</a>.</li>
            <li>Personalizza il codice nella directory <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonare l’archivio GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informazioni utili

Utilizzare i collegamenti sul lato sinistro della pagina per spostarsi tra gli argomenti di ogni parte dell&#39;installazione.

## Autorizzazioni server richieste

I sistemi UNIX richiedono privilegi `root` per installare e configurare software come un server Web, PHP. Se devi installare questo software, assicurati di disporre dell&#39;accesso `root`.

*non* installare l&#39;applicazione nella directory principale dei documenti del server Web come utente `root` perché il server Web potrebbe non essere in grado di interagire con tali file.

Sono necessari i privilegi di `root` per creare il [proprietario del file system](file-system/overview.md) e aggiungerlo al gruppo del server Web. Utilizzare il proprietario del file system per eseguire `bin/magento` comandi dalla riga di comando e per impostare processi cron, che consentono di pianificare le attività.
