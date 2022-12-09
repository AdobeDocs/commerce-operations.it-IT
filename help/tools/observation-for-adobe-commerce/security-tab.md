---
title: "Il [!UICONTROL Security] scheda"
description: Scopri le [!UICONTROL Security] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 297c3fed4c0f7ad1a3cb40addef1d33fa8d41525
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# La [!UICONTROL Security] scheda

La **[!UICONTROL Security]** tab spiega i problemi di sicurezza e ne isola le cause potenziali. Vengono inoltre descritti i fotogrammi della scheda.

## [!UICONTROL API calls by IP, details by URL]

La **[!UICONTROL API calls by IP, details by URL]** Il frame mostra una serie di chiamate API per IP in un arco temporale selezionato. In questo frame vengono visualizzati l’indirizzo IP e l’URL API a cui è stato effettuato l’accesso dall’indirizzo IP.

![Chiamate API per IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

La **[!UICONTROL Forgot Password]** l&#39;intervallo di accesso mostra il numero di tentativi di password dimenticati in un arco temporale selezionato. L’alta attività contro un indirizzo IP può essere un attacco sul sito.

![Password dimenticata](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

La **[!UICONTROL Create Account access]** mostra il numero di nuove attività dell’account in un arco temporale selezionato. L&#39;alta attività da un singolo indirizzo IP può indicare un attacco.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

La **[!UICONTROL POST activities]** la cornice mostra `POST` attività per il sito, sfaccettate su `client_ip` dal [!DNL Fastly] registri. Mostra anche l’URL a cui si accede dall’indirizzo IP.

![Attività POST](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

La **[!UICONTROL POST activities summary table]** il riquadro mostra il riepilogo `POST` attività per il sito, sfaccettate su `client_ip` dal [!DNL Fastly] registri. Mostra anche il conteggio dell’URL a cui si accede dall’indirizzo IP. Il conteggio viene eseguito per l&#39;intervallo temporale selezionato.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

La **[!UICONTROL POST activities details table]** la cornice mostra `POST` attività per il sito dal [!DNL Fastly] registri. Mostra anche tutti i dettagli dal [!DNL Fastly] registra queste richieste. È limitato alle ultime 2000 richieste.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

La **[!UICONTROL Guest Carts activities]** frame mostra il numero di attività del carrello guest in un arco temporale selezionato, facet per indirizzo IP e URL a cui si accede. I carrelli degli ospiti possono essere utilizzati in un attacco carding. Questo fotogramma mostra il numero totale di richieste in cui si accede agli URL dei carrelli ospite.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

La **[!UICONTROL API – forgot password, create account by Countries]** frame mostra il numero di account creati e le richieste per reimpostare una password dimenticata in un arco temporale selezionato. È fattibile mostrare anche il paese di origine della richiesta. Questo quadro si concentra sul paese di origine della richiesta.

![paesi dimenticati dell&#39;api](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

La **[!UICONTROL API - forgot password, create account by Countries and IP address]** frame mostra il numero di account creati e le richieste per reimpostare una password dimenticata in un arco temporale selezionato. Viene sfaccettato di mostrare anche l’indirizzo IP, l’URL a cui si accede e il paese di origine della richiesta. Questo frame si concentra sul conteggio di IP.

![api-dimenticata-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

La **[!UICONTROL Guest cart activities by IP]** frame mostra le attività del carrello guest per IP nell’arco temporale selezionato.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

La **[!UICONTROL Guest cart activities by Countries]** Il frame mostra le attività del carrello dei visitatori per paesi in un arco temporale selezionato.

![paese ospite](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
