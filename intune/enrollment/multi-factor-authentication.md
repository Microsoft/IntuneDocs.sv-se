---
title: Kräv multifaktorautentisering för enhetsregistrering i Intune
titleSuffix: Microsoft Intune
description: Så här kräver du multifaktorautentisering i Azure AD vid enhetsregistrering i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14347d12888ff5ef61d4543409a08fbdeb371c89
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415208"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Kräv multifaktorautentisering för enhetsregistreringar i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune kan använda Azure Active Directory (AD) multifaktorautentisering (MFA) för enhetsregistrering så att du enklare kan skydda dina företagsresurser.

MFA fungerar genom att kräva två eller flera av följande verifieringsmetoder:

- Något du känner till (vanligtvis ett lösenord eller PIN-kod).
- Något du har (betrodda enheter som inte enkelt dupliceras, t.ex. en telefon).
- Något du är (biometrik, till exempel ett fingeravtryck).

MFA stöds för iOS/iPadOS, Android, Windows 8.1 eller senare, eller Windows Phone 8.1 eller Windows 10 Mobile eller senare enheter.

När du aktiverar MFA måste slutanvändarna ange två typer av autentiseringsuppgifter för att registrera en enhet.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Konfigurera Intune så att multifaktorautentisering krävs vid enhetsregistrering

Om du vill kräva MFA när en enhet registreras följer du dessa steg:

>[!Important]
>Du måste ha tilldelat Azure Active Directory Premium P1 eller senare till dina användare för att implementera den här principen.

>[!Important]
>Konfigurera inte **Enhetsbaserade åtkomstregler** för Microsoft Intune-registrering.

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Enheter** > **Villkorsstyrd åtkomst**. Den nod för villkorsstyrd åtkomst som nås från *Intune* är samma nod som den som nås från *Azure AD*.
2. Välj **Ny princip**.
3. I **Ny** princip anger du ett beskrivande namn för principen.
4. Välj **Tilldelningar** i avsnittet **Användare och grupper**. 
5. I **Användare och grupper** väljer du **Välj användare eller grupper** och markerar **Användare och grupper**. Välj sedan de användare och/eller grupper som ska få den här principen. Välj sedan **Klart**.
6. I avsnittet **Tilldelningar** väljer du **Molnappar**.
7. På fliken **Ta med** i **Molnappar** väljer du **Välj appar** och välj sedan **Välj** > **Microsoft Intune-registrering** och väljer sedan **Klart**. När du väljer **Microsoft Intune-registrering** tillämpas MFA för villkorsstyrd åtkomst endast vid registreringen av enheten (engångsfråga för MFA).
8. I avsnittet **Tilldelningar** behöver du för **Villkor** inte ange några inställningar för MFA.
9. I avsnittet **Åtkomstkontroller** väljer du **Bevilja**.
10. I **Bevilja** väljer du **Bevilja åtkomst** och väljer sedan **Kräv multifaktorautentisering**. Markera inte **Kräv att enheten är markerad som kompatibel** eftersom det inte går att utvärdera regelefterlevnad för en enhet förrän den har registrerats. Välj sedan **Välj**.
11. I **Ny princip**, väljer du **Aktivera princip** > **På** och väljer sedan **Skapa**.



## <a name="next-steps"></a>Nästa steg

När slutanvändarna registrerar sina enheter måste de nu autentisera med en andra identifieringsmetod, till exempel PIN-kod, telefon eller biometrik.
