---
title: Il [!UICONTROL Security] scheda
description: Scopri di più su [!UICONTROL Security] scheda di [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Il [!UICONTROL Security] scheda

Il **[!UICONTROL Security]** Questa scheda spiega i problemi di sicurezza e ne isola le potenziali cause. Vengono inoltre descritte le cornici della scheda.

## [!UICONTROL API calls by IP, details by URL]

Il **[!UICONTROL API calls by IP, details by URL]** mostra una serie di chiamate API per IP in un arco temporale selezionato. In questo frame vengono visualizzati l&#39;indirizzo IP e l&#39;URL API a cui ha avuto accesso quell&#39;indirizzo IP.

![Chiamate API per IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

Il **[!UICONTROL Forgot Password]** frame di accesso mostra il numero di tentativi di password dimenticata in un arco temporale selezionato. Un’elevata attività contro un indirizzo IP può essere un attacco al sito.

![Password dimenticata](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

Il **[!UICONTROL Create Account access]** mostra il numero di nuove attività dell’account in un arco temporale selezionato. Un’elevata attività da un singolo indirizzo IP può indicare un attacco.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

Il **[!UICONTROL POST activities]** il frame mostra il `POST` attività per il sito, con facet su `client_ip` dal [!DNL Fastly] log. Mostra anche l’URL a cui accede l’indirizzo IP.

![POST-attività](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

Il **[!UICONTROL POST activities summary table]** frame mostra il riepilogo `POST` attività per il sito, con facet su `client_ip` dal [!DNL Fastly] log. Mostra anche il conteggio dell’URL a cui accede l’indirizzo IP. Il conteggio si riferisce all’intervallo temporale selezionato.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

Il **[!UICONTROL POST activities details table]** il frame mostra il `POST` attività per il sito da [!DNL Fastly] log. Vengono inoltre visualizzati tutti i dettagli dell&#39; [!DNL Fastly] per queste richieste. È limitato alle ultime 2000 richieste.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

Il **[!UICONTROL Guest Carts activities]** mostra il numero di attività del carrello degli ospiti in un arco temporale selezionato, suddivise per indirizzo IP e URL a cui si accede. I carrelli ospiti possono essere utilizzati in un attacco carding. Questo fotogramma mostra il numero totale di richieste in cui si accede agli URL dei carrelli ospiti.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

Il **[!UICONTROL API – forgot password, create account by Countries]** mostra il numero di account creati e le richieste di reimpostazione di una password dimenticata in un arco temporale selezionato. Mostra anche il paese di origine della richiesta. Il quadro si concentra sul paese di origine della richiesta.

![api-forgot-countries](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

Il **[!UICONTROL API - forgot password, create account by Countries and IP address]** mostra il numero di account creati e le richieste di reimpostazione di una password dimenticata in un arco temporale selezionato. Mostra inoltre l’indirizzo IP, l’URL a cui si accede e il paese di origine della richiesta. Questo fotogramma si concentra sul numero di IP.

![api-forgot-countries-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

Il **[!UICONTROL Guest cart activities by IP]** mostra le attività del carrello guest in base all’IP in un arco temporale selezionato.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

Il **[!UICONTROL Guest cart activities by Countries]** mostra le attività del carrello degli ospiti per paese in un arco temporale selezionato.

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
