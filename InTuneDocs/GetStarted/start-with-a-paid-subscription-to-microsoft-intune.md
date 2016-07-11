---
title: "Snabbstartsguide för Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: ca0ca74357b59d9cc6fbf4ec7eb237dff972c411


---


# Snabbstartsguide för Intune
Den här snabbstartsguiden leder dig genom stegen för att konfigurera en betald prenumeration på Microsoft Intune så att du snabbt och enkelt kan börja hantera mobila enheter och Windows-datorer som används av din organisation. Du kan följa stegen i ordning eller bara hoppa framåt om ett steg inte gäller för din miljö eller dina affärsbehov.

>[!NOTE]
>Den här artikeln handlar om hur du konfigurerar Intune som en fristående tjänst. Alternativt, om du använder Microsoft System Center Configuration Manager för att hantera datorer och servrar, kan du [utöka Configuration Manager för att hantera mobila enheter](https://technet.microsoft.com/library/jj884158.aspx) genom att ansluta Intune med Configuration Manager i en MDM-hybriddistribution för att även hantera mobila enheter.

Många av stegen i den här snabbstartsguiden är samma som de i [utvärderingsguiden för Intune](/intune/understand-explore/get-started-with-a-30-day-trial-of-microsoft-intune). Efter utvärderingen, när du är redo att börja hantera dina mobila enheter, måste du dock åtgärda ett antal ytterligare krav. Dessa varierar beroende på din aktuella nätverksinfrastruktur och dina affärskrav, t.ex.:

-   Synkronisera lokala Active Directory-konton med Intune och Azure Active Directory

-   Uppdatera posterna för DNS-tjänsten och den offentliga domänen hos din domänregistrator

-   Anpassa Intune-funktioner för produktionsanvändning

>[!TIP]
>Om du köper minst 150 licenser för Microsoft Intune i ett tillgängligt abonnemang kan du använda FastTrack Center Benefit, en tjänst där Microsoft-specialister samarbetar med dig för att förbereda din miljö för Intune. Se [Beskrivning av Microsoft Intune Serviceförmån](https://technet.microsoft.com/library/mt228265.aspx).


## Innan du börjar
Använd den här guiden när du börjar med en betald prenumeration och är redo att distribuera Intune och göra ändringar i din befintliga nätverksinfrastruktur. Det kan röra sig om att enbart lägga till eller uppdatera interna och externa DNS-poster, eller att synkronisera befintliga Active Directory-användarkonton till Azure Active Directory. Oavsett vilka olika Intune-funktioner för mobila enheter som du väljer, måste du planera noggrant hur Intune ska interagera med dina befintliga nätverkskomponenter och tjänster. Särskilt bör du granska:

-   **Hantera användaridentitet**: För de flesta medelstora och stora organisationer är en anslutning av befintliga katalogtjänster till Intune via Azure Active Directory det bästa och enklaste sättet att hantera användaridentiteter med Intune. Detta gäller särskilt om du redan använder andra Microsoft-molntjänster, till exempel Office 365 eller Exchange Online. Att synkronisera befintliga användarkonton med [Microsofts Azure Active Directory Connect](https://www.microsoft.com/download/details.aspx?id=47594) är ett snabbt och enkelt sätt att ansluta din lokala Active Directory till Azure Active Directory och konfigurera enkel inloggning för användarnas autentisering.

-   **Hur DNS påverkas**: Om du vill använda ett eget domännamn i stället för standarddomänen onmicrosoft.com när du först registrerar dig för Intune krävs vissa offentliga DNS-postuppdateringar. Uppdateringar av DNS-poster krävs så att mobila enheter kan hitta Intune-tjänsten och kontrollera att hanteringstjänsten för din prenumeration fungerar som den ska så att alla enheter som används i din organisation hanteras korrekt.

## Ha följande till hands
Redo att sätta igång? Du behöver följande när du börjar använda din betalprenumeration på Intune:

### En enhet med en Silverlight-aktiverad webbläsare
Du behöver detta för att få åtkomst till Intune-administrationskonsolen där du hanterar enheter, appar och principer. Du behöver också en webbläsare för att få åtkomst till den webbaserade företagsportalen när du inte kommer åt företagsportalappen från en mobil enhet. För att göra det lättare kan du använda inställningen för sekretessläge i samma webbläsare som du använder för Intune-administration (i Internet Explorer klickar du till exempel på **Verktyg** &gt; **InPrivate-surfning**).

>[!TIP]
>Microsoft Edge-webbläsaren stöds inte för åtkomst till Intune-administrationskonsolen på grund av det här kravet.


### Certifikat för mobila enheter
Om du ska hantera iOS- eller Windows Phone-enheter med Intune behöver du certifikat och konton för att hämta dessa certifikat. Du behöver inte några ytterligare certifikat för att hantera Android-enheter.

- Inget certifikat krävs för **Windows Phone 8.1**-användare som installerar företagsportalappen från Store. Dock behöver du ett [kodsigneringscertifikat från Symantec](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do) för **Windows Phone 8.0** eller om du ska använda Intune för att distribuera företagsportalappen till Windows Phone 8.1-enheter.

>[!NOTE]
>Den här snabbstartsguiden förutsätter att användarna hämtar företagsportalappen från Store på en Windows Phone 8.1-enhet eller senare. Information om Windows Phone 8.0-stöd finns i [Konfigurera hantering av Windows Phone 8.0 med Microsoft Intune](/Intune/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune).

- Det finns inga certifikatkrav för **Windows-datorer** eller **Windows RT-enheter** när Windows-datorer registreras som enheter eller när [Windows-datorklienten installeras för Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).

- För **iOS**- eller **Mac OS X**-enheter måste du begära ett certifikat för Apple Push Notification Service från Apple. Mer information finns i steg 3 i [Konfigurera iOS- och Mac-hantering med Microsoft Intune](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).

### Nästa steg
Det är dags att komma igång med Intunes snabbstartsguide!

>[!div class="step-by-step"]
[**Logga in i Intune** &rarr;](start-with-a-paid-subscription-to-microsoft-intune-step-1.md)



<!--HONumber=Jun16_HO4-->


