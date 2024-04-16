---
title: Ottieni il software Adobe Commerce
description: Scopri come scaricare il software Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Ottieni il software Adobe Commerce

Sei tra i 240.000 commercianti in tutto il mondo che hanno dato fiducia al nostro software di eCommerce. Sono state raccolte alcune informazioni per aiutarti a iniziare con l’installazione.

## Come ottenere il software

Controlla la disponibilità di nuove funzioni e versioni e scopri come inserirle nel nostro [pagina sulla disponibilità del prodotto](https://devdocs.magento.com/release/availability.html).

Consulta la tabella seguente per iniziare a installare Adobe Commerce o Magento Open Source.

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
        <td><p>Vuole il controllo completo su tutti i componenti installati, ha accesso al server applicazioni, altamente tecnico, potrebbe riconfezionare il Magento Open Source con altri componenti.</p>
        </td>
        <td><ol><li>Crea un Compositore <em>progetto</em> che contiene l’elenco dei componenti da utilizzare.</li>
            <li>Utilizza il Compositore per aggiornare le dipendenze del pacchetto; utilizza <code>composer create-project</code> per ottenere il metapacchetto Compositore.</li>
            <li>Installa l'applicazione utilizzando <a href="../advanced.md">riga di comando</a>.</li>
        <li>Aggiorna l'applicazione e le estensioni utilizzando  <a href="../../upgrade/implementation/perform-upgrade.md">riga di comando</a>.</li></ol></td>
        <td><p><a href="../composer.md">Ottieni il metapacchetto</a></p></td>
    </tr>
    <tr>
        <td><p>Sviluppatore partecipante</p></td>
        <td><p>Contribuisce alla base di codice del Magento Open Source, ai file bug e personalizza l’applicazione. Estremamente tecnico, dispone di un proprio server di sviluppo, comprende Composer e GitHub.</p>
            <p>Tu <em>non può</em> utilizzare l'applicazione in un ambiente di produzione.</p>
      <p>È necessario eseguire l’aggiornamento tramite <a href="../../upgrade/developer/git-installs.md">Compositore e comandi Git</a>.</p></td>
        <td><ol><li>Clona l’archivio GitHub.</li>
            <li>Utilizza Compositore per aggiornare le dipendenze del pacchetto.</li>
            <li>Installa l'applicazione utilizzando <a href="../advanced.md">riga di comando</a>.</li>
            <li>Aggiorna l'applicazione tramite <a href="../../upgrade/developer/git-installs.md">Compositore e comandi Git</a>.</li>
            <li>Personalizza il codice in <code>app/code</code> directory.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonare l’archivio GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informazioni utili

Utilizzare i collegamenti sul lato sinistro della pagina per spostarsi tra gli argomenti di ogni parte dell&#39;installazione.

## Autorizzazioni server richieste

I sistemi UNIX richiedono `root` privilegi per installare e configurare software come un server web, PHP. Se è necessario installare questo software, assicurarsi di avere `root` accesso.

Esegui *non* installare l’applicazione nella directory principale dei documenti del server web come `root` perché il server web potrebbe non essere in grado di interagire con tali file.

Hai bisogno di `root` privilegi per creare [proprietario del file system](file-system/overview.md) e aggiungi tale proprietario al gruppo del server web. Utilizzare il proprietario del file system per eseguire `bin/magento` comandi dalla riga di comando e per impostare i processi cron, che consentono di pianificare le attività.
