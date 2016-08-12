---
title: "Utvärderingsguiden för | Microsoft Intune"
description: "Introduktion och förutsättningar för att komma igång med en kostnadsfri 30-dagars utvärderingsversion av Intune"
keywords: 
author: lindavr
manager: angrobe
ms.date: 08/09/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 619a1d11-3d22-4635-8f70-770eba3e1712
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 51fba2b01d8978bc062c50c4388714609be0fdf0
ms.openlocfilehash: cbf863619a385d596630ee4ff0b216a4cbbe6cb7


---

# Utvärderingsguiden för Intune
Det går snabbt och enkelt att ställa in en kostnadsfri 30-dagars utvärderingsversion av Intune för att hantera dina mobila enheter och datorer. Du kan lägga till upp till 100 användare och enheter med några enkla steg i utvärderingsversionen, ställa in grupper, konfigurera efterlevnadspolicyer och registrera och hantera mobila enheter och datorer.

I det här avsnittet lär du dig grunderna för att få igång en utvärderingsversion av Intune och få en översikt över tjänsten så att du kan utvärdera Intunes funktioner och möjligheter.

Titta på den här fem minuter långa demonstrationsvideon och se hur lätt det är att komma igång med den kostnadsfria utvärderingsversionen av Microsoft Intune och hantera dina enheter. I den första delen av videon beskrivs en portal som har ”pensionerats”, men stegen är i stort sett desamma även om du använder en annan portal. Du kan läsa mer om portalen [här](https://docs.microsoft.com/intune/deploy-use/account-portal-merged-with-Office-365).

<iframe width="675" height="480" src="https://www.youtube.com/embed/ltcZvm4VOFU" frameborder="0" allowfullscreen></iframe>

## Innan du börjar
Innan du börjar med Intune behöver du följande:

-   En enhet med en Silverlight-aktiverad webbläsare som du kan använda för att få åtkomst till de webbplatser där du skapar Intune-användarkonton (**Office 365-administrationscentret**) och där du hanterar enheter, grupper och principer (**Intune-administratörskonsolen**).

-   En andra enhet med en webbläsare som du använder för att testa hur Intune-användare registrerar och hanterar sina enheter med hjälp av företagsportalen. Du kan också testa hur användare söker efter och installerar appar och ber om hjälp från administratörer. Om du inte har en andra enhet kan du använda sekretesslägesinställningen i samma webbläsare som du använder för Intune-administration (i Internet Explorer kan du till exempel klicka på **Verktyg** &gt; **InPrivate-surfning**).

-   Om du har ett befintligt Microsoft Online Services-konto behöver du ha tillgång till autentiseringsuppgifterna för kontots administratör. Om du inte har något sådant konto, eller om du vill använda denna Intune-innehavare enbart i utvärderingssyfte, behöver du inte dessa autentiseringsuppgifter för administratören.

-   Om du ska hantera iOS- eller Windows Phone-enheter med Intune-utvärderingsversionen behöver du certifikat (eller nycklar) och konton för att hämta dessa certifikat (se följande tabell). Android-enheter behöver inte några ytterligare certifikat.

    |Plattform|Certifikatkrav|Mer information|
    |------------|----------------------------|--------------------|
    |Windows Phone 8.1 och Windows Phone 8 |Inga certifikat krävs för Windows Phone 8.1-användare som installerar företagsportalappen från Store. Ett Symantec-certifikat krävs för Windows Phone 8.0 eller för att använda Intune för att distribuera företagets portalapp till Windows Phone 8.1-enheter.|Dessa riktlinjer förutsätter att användarna hämtar företagsportalappen från Store på en Windows Phone 8.1 eller senare enhet. Information om Windows Phone 8.0-stöd finns i [Konfigurera hantering av Windows Phone med Microsoft Intune](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune).|
    |Windows 10-, Windows RT 8.1-, Windows RT- eller Windows 8.1-enheter|Det finns inga certifikatkrav vid registrering av Windows RT- eller Windows-enheter.|[Installera Windows PC-klienten med Microsoft Intune](/Intune/Deploy-Use/install-the-windows-pc-client-with-microsoft-intune).|
    |iOS 7.1 och senare|Hämta ett certifikat för Apple Push-aviseringstjänsten.|Begär ett certifikat för Apple Push Notification Service från Apple genom att följa anvisningarna i [Konfigurera iOS-hantering med Microsoft Intune](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune).|

## Steg för att slutföra en 30-dagars utvärderingsversion av Intune
- [Steg 1: Logga in eller registrera dig för en 30-dagars utvärderingsversion](get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md). Innan du registrerar dig eller loggar in på Intune bör du bestämma dig för om du vill logga in med ett befintligt konto eller skapa ett tillfälligt konto som ska användas endast för 30-dagars utvärderingsversionen av Microsoft Intune.
- [Steg 2: Lägg till användare](get-started-with-a-30-day-trial-of-microsoft-intune-step-2.md). Nu när du har lagt upp ditt konto, ska du antingen lägga till enskilda användarkonton till Intune eller lägga till användare i grupp (se anvisningarna i det här avsnittet). Det är viktigt att du förstår hur Intune hanterar administratörskonton innan du börjar.
- [Steg 3: Skapa grupper för att organisera användare och enheter](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md). Grupper i Intune ger stor flexibilitet för att hantera dina enheter och användare. Du kan konfigurera grupper efter organisationens behov (till exempel genom geografisk plats, avdelning eller maskinvaruegenskaper) och använda dem för att utföra olika administrativa uppgifter i skala, från att ange principer för en uppsättning användare till att distribuera program till en uppsättning enheter.
- [Steg 4: Skapa principer och publicera en app](get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md). Intune-principerna förser dig med inställningar som hjälper dig att kontrollera säkerhetsinställningarna på mobila enheter, underhålla Windows-brandväggen och Endpoint Protection-inställningarna för datorer, samt distribuera program.
- [Steg 5: Registrera mobila enheter och installera en app](get-started-with-a-30-day-trial-of-microsoft-intune-step-5.md). Om du ska konfigurera hantering av mobila enheter med Intune måste du ange utfärdaren för hantering av mobila enheter, aktivera hantering för specifika enhetsplattformar och sedan registrera enheterna i företagsportalappen. Därefter kan du hämta det Microsoft Skype-program som du har publicerat.
- [Steg 6: Övriga alternativ och tillägg](get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md). Välj hur du använder andra aviseringar, rapporter och andra Intune-funktioner som uppfyller dina affärsbehov.
- [Steg 7: Nästa steg](get-started-with-a-30-day-trial-of-microsoft-intune-step-7.md). Förbered för att flytta till en betald prenumeration och dra nytta av Intune "FastTrack Center Benefit.


### Nästa steg
Det är dags att komma igång med din prenumeration på 30-dagars utvärderingsversionen!

>[!div class="step-by-step"]
[**Registrera dig för Intune** &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)

### Se även
[Snabbstartsguide för Intune](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune)



<!--HONumber=Aug16_HO2-->


