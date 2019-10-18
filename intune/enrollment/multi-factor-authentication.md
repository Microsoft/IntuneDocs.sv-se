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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b761672ceace57ae7c0939959d25b8d6e45be32
ms.sourcegitcommit: 60ed93682a21860e9d99ba1592ede120477f2b4d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72379822"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Kräv multifaktorautentisering för enhetsregistreringar i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune kan använda Azure Active Directory (AD) multifaktorautentisering (MFA) för enhetsregistrering så att du enklare kan skydda dina företagsresurser.

MFA fungerar genom att kräva två eller flera av följande verifieringsmetoder:

- Något du känner till (vanligtvis ett lösenord eller PIN-kod).
- Något du har (betrodda enheter som inte enkelt dupliceras, t.ex. en telefon).
- Något du är (biometrik, till exempel ett fingeravtryck).

MFA stöds för iOS, Android, Windows 8.1 eller senare, eller Windows Phone 8.1 eller Windows 10 Mobile eller senare enheter.

När du aktiverar MFA måste slutanvändarna ange två typer av autentiseringsuppgifter för att registrera en enhet.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Konfigurera Intune så att multifaktorautentisering krävs vid enhetsregistrering

Om du vill kräva MFA när en enhet registreras följer du dessa steg:

>[!Important]
>Du måste ha tilldelat Azure Active Directory Premium P1 eller senare till dina användare för att implementera den här principen.

>[!Important]
>Konfigurera inte **Enhetsbaserade åtkomstregler** för Microsoft Intune-registrering.

1. Logga in med dina autentiseringsuppgifter på [Microsoft Azure Portal](https://portal.azure.com).
2. I portalen går du till **Intune** och väljer **Villkorlig åtkomst**. Den nod för villkorsstyrd åtkomst som nås från *Intune* är samma nod som den som nås från *Azure AD*.
4. Välj **Ny princip**.
5. I **Ny** princip anger du ett beskrivande namn för principen.
6. Välj **Tilldelningar** i avsnittet **Användare och grupper**. 
7. I **Användare och grupper** väljer du **Välj användare eller grupper** och markerar **Användare och grupper**. Välj sedan de användare och/eller grupper som ska få den här principen. Välj sedan **Klart**.
8. I avsnittet **Tilldelningar** väljer du **Molnappar**.
9. På fliken **Ta med** i **Molnappar** väljer du **Välj appar** och välj sedan **Välj** > **Microsoft Intune-registrering** och väljer sedan **Klart**. När du väljer **Microsoft Intune-registrering** tillämpas MFA för villkorsstyrd åtkomst endast vid registreringen av enheten (engångsfråga för MFA).
10. I avsnittet **Tilldelningar** behöver du för **Villkor** inte ange några inställningar för MFA.
11. I avsnittet **Åtkomstkontroller** väljer du **Bevilja**.
12. I **Bevilja** väljer du **Bevilja åtkomst** och väljer sedan **Kräv multifaktorautentisering** . Markera inte **Kräv att enheten är markerad som kompatibel** eftersom det inte går att utvärdera regelefterlevnad för en enhet förrän den har registrerats. Välj sedan **Välj**.
13. I **Ny princip**, väljer du **Aktivera princip** > **På** och väljer sedan **Skapa**.



## <a name="next-steps"></a>Nästa steg

När slutanvändarna registrerar sina enheter måste de nu autentisera med en andra identifieringsmetod, till exempel PIN-kod, telefon eller biometrik.
