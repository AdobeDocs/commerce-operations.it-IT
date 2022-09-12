---
title: Scarica il software Adobe Commerce
description: Scopri come scaricare il software Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Scarica il software Adobe Commerce

Sei tra i 240.000 commercianti di tutto il mondo che hanno fiducia nel nostro software eCommerce. Abbiamo raccolto alcune informazioni per aiutarti a iniziare l&#39;installazione.

## Come ottenere il software

Verifica la disponibilità di nuove funzioni e versioni entusiasmanti e scopri come utilizzarle [pagina di disponibilità del prodotto](https://devdocs.magento.com/release/availability.html).

Per iniziare a installare Adobe Commerce o Magenti Open Source, consulta la tabella seguente.

<table>
    <tbody>
        <tr>
            <th>Requisiti utente</th>
            <th>Descrizione</th>
            <th>Procedura di installazione e aggiornamento di alto livello</th>
            <th>Collegamento iniziale</th>
        </tr>
    <tr>
        <td><p>Integratore, imballatore</p></td>
        <td><p>Vuole il pieno controllo su tutti i componenti installati, ha accesso all'application server, altamente tecnico, potrebbe riconfezionare il Magento Open Source con altri componenti.</p>
        </td>
        <td><ol><li>Crea un Compositore <em>progetto</em> che contiene l’elenco dei componenti da utilizzare.</li>
            <li>Utilizza il Compositore per aggiornare le dipendenze dei pacchetti; utilizza <code>composer create-project</code> per ottenere il metapackage Composer.</li>
            <li>Installa l'applicazione utilizzando <a href="../advanced.md">riga di comando</a>.</li>
        <li>Aggiorna l'applicazione e le estensioni utilizzando  <a href="../../upgrade/implementation/perform-upgrade.md">riga di comando</a>.</li></ol></td>
        <td><p><a href="../composer.md">Ottieni il metapackage</a></p></td>
    </tr>
    <tr>
        <td><p>Sviluppatore collaboratore</p></td>
        <td><p>Contribuisce alla base di codice del Magento Open Source, ai bug dei file e personalizza l’applicazione. Altamente tecnico, dispone di un proprio server di sviluppo, comprende Composer e GitHub.</p>
            <p>You <em>impossibile</em> utilizzare l'applicazione in un ambiente di produzione.</p>
      <p>È necessario eseguire l'aggiornamento utilizzando <a href="../../upgrade/developer/git-installs.md">Compositore e comandi Git</a>.</p></td>
        <td><ol><li>Duplica l’archivio GitHub.</li>
            <li>Utilizza Compositore per aggiornare le dipendenze dei pacchetti.</li>
            <li>Installa l'applicazione utilizzando <a href="../advanced.md">riga di comando</a>.</li>
            <li>Aggiorna l'applicazione utilizzando <a href="../../upgrade/developer/git-installs.md">Compositore e comandi Git</a>.</li>
            <li>Personalizza il codice sotto il <code>app/code</code> directory.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonare l’archivio GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informazioni utili

Utilizza i collegamenti sul lato sinistro della pagina per navigare negli argomenti relativi a ciascuna parte dell’installazione.

## Autorizzazioni necessarie per il server

I sistemi UNIX richiedono `root` privilegi per installare e configurare software come un server web, PHP. Se devi installare questo software, assicurati di `root` accesso.

Do *not* installa l&#39;applicazione nel docroot del server web come `root` utente perché il server web potrebbe non essere in grado di interagire con tali file.

Hai bisogno di `root` privilegi per creare [proprietario del file system](file-system/overview.md) e aggiungere il proprietario al gruppo del server web. Utilizzi le [proprietario del file system](https://glossary.magento.com/magento-file-system-owner) per eseguire `bin/magento` comandi dalla riga di comando e per impostare i lavori cron, che pianificano le attività per l&#39;utente.
