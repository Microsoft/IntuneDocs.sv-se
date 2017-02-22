---
title: "Multifaktorautentisering för enhetsregistreringar i Intune | Microsoft Docs"
description: "Så här kräver du multifaktorautentisering i Azure AD vid enhetsregistrering."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
translationtype: Human Translation
ms.sourcegitcommit: 30ed470200a830caa3c31be284f27e4b2347a71a
ms.openlocfilehash: fa14ab5d4297a31d80b48611708e8a78d7513b8d


---

# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Multifaktorautentisering för enhetsregistreringar i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune integrerar Azure multifaktorautentisering (MFA) för enhetsregistrering så att du enklare kan skydda dina företagsresurser.

MFA fungerar genom att kräva två eller flera av följande verifieringsmetoder: 

- Något du känner till (vanligtvis ett lösenord eller PIN-kod).
- Något du har (betrodda enheter som inte enkelt dupliceras, t.ex. en telefon).
- Något du är (biometrik).

MFA stöds för iOS, Android, Windows 8.1 eller senare, eller Windows Phone 8.1 eller senare enheter.

> [!NOTE]
> I tidigare versioner av Configuration Manager (äldre än version 1610) ser du fortfarande MFA-inställningarna i administrationskonsolen i Configuration Manager. Försök inte att konfigurera MFA i administrationskonsolen för Configuration Manager. Det fungerar nämligen inte. Konfigurera MFA så som beskrivs i det här avsnittet.

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Konfigurera Intune så att multifaktorautentisering krävs vid enhetsregistrering
Om du vill kräva MFA när en enhet registreras följer du dessa steg:

1. Logga in med dina administratörsautentiseringsuppgifter på [Microsoft Azure-portalen](https://manage.windowsazure.com).
2. Välj klient.
2. Välj fliken **Program**. En lista visas över tjänster för vilka du kan konfigurera Azure AD-säkerhetsfunktioner.
3. Välj **Microsoft Intune-registrering**.
4. Välj **Konfigurera**. 
5. Under **multifaktorautentisering och åtkomstregler för plats-baserade** kan du:
    
    -  Aktivera åtkomstregler
    -  Välj att tillämpa reglerna för alla användare eller för specifika Azure AD-säkerhetsgrupper.
    -  Kräv multifaktorautentisering för registrering av alla enheter.
    -  Kräv multifaktorautentisering för registrering när enheten inte är i bruk.
    -  Välj **Blockera åtkomst till företagsresurser** om du vill förhindra registrering av en enhet när den inte är ansluten till företagsnätverket. 
4. Du kan också klicka på länken till **definiera/redigera din nätverksplats** om du vill konfigurera anslutningskrav för enhetsregistrering.

> [!IMPORTANT]
> 
> Konfigurera inte **Enhetsbaserade åtkomstregler** för Microsoft Intune-registrering.



<!--HONumber=Feb17_HO1-->


