---
title: "Multifaktorautentisering som använder Azure AD | Microsoft Docs"
description: "Så här kräver du multifaktorautentisering i Azure AD vid enhetsregistrering."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 12/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
translationtype: Human Translation
ms.sourcegitcommit: 85462d6cb5e3dc6ce8e94fe8fd1bc1c1c2b6e4f3
ms.openlocfilehash: 6e20eca60886781ae884107a224245639c5f107c


---

# <a name="multi-factor-authentication-for-microsoft-intune"></a>Multifaktorautentisering för Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune integrerar Azure multifaktorautentisering (MFA) för enhetsregistrering så att du enklare kan skydda dina företagsresurser. MFA kräver autentiseringsfaktorer, till exempel textautentisering, utöver användarnamn och lösenord. Detta stöds för iOS, Android, Windows 8.1 eller senare, eller Windows Phone 8.1 eller senare enheter.

> [!NOTE]
>
> Så här använder du nu MFA i Intune. Det tidigare sättet, som kunder nu migreras från, beskrivs i [Protect Windows devices with multi-factor authentication](protect-windows-devices-with-multi-factor-authentication.md) (Skydda Windows-enheter med multifaktorautentisering).
>
> I tidigare versioner av Configuration Manager (äldre än version 1610) ser du fortfarande MFA-inställningarna i administrationskonsolen i Configuration Manager. Försök inte att konfigurera MFA i administrationskonsolen för Configuration Manager. Det fungerar nämligen inte. Konfigurera MFA så som beskrivs i det här avsnittet.

### <a name="configuring-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Så här konfigurerar du Intune så att multifaktorautentisering krävs vid enhetsregistrering
Gör så här om du vill kräva MFA vid enhetsregistrering:

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



<!--HONumber=Dec16_HO3-->


