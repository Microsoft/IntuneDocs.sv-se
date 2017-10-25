---
title: "Multifaktorautentisering för enhetsregistrering i Intune"
titlesuffix: Azure portal
description: "Så här kräver du multifaktorautentisering i Azure AD vid enhetsregistrering."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angerobe
ms.date: 08/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: 
ms.custom: intune-azure
ms.openlocfilehash: 0355c6ca11d7b1221ad7aa833874eba91eea0600
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Multifaktorautentisering för enhetsregistreringar i Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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
>Konfigurera inte **Enhetsbaserade åtkomstregler** för Microsoft Intune-registrering.

1. Logga in med dina autentiseringsuppgifter på [Microsoft Azure Portal](https://portal.azure.com).
2. Välj **Azure Active Directory** i portalen.
2. I **Azure Active Directory** väljer du **Hantera** > **Företagsprogram**.
3. I **Företagsprogram** väljer du **Hantera** > **Alla program**. En lista visas över alla Azure-appar som du hanterar.
3. Välj **Microsoft Intune-registrering** i listan.
4. I **Microsoft Intune-registrering** väljer du **Säkerhet** > **Villkorlig åtkomst**.
5. Välj **Ny princip**.
6. I **Ny** princip anger du ett beskrivande namn för principen.
7. Välj **Tilldelningar** i avsnittet **Användare och grupper**.
8. I **Användare och grupper** väljer du de användare eller grupper som principen ska tilldelas. Välj sedan **Klart**.
9. I avsnittet **Tilldelningar** väljer du **Molnappar**.
10. På fliken **Ta med** i **Molnappar** väljer du **Välj appar** och välj sedan **Välj** > **Microsoft Intune-registrering** och väljer sedan **Klart**.
11. I avsnittet **Tilldelningar** väljer du **Villkor**.
12. I **Villkor** behöver du inte ange några inställningar för MFA.
13. I avsnittet **Åtkomstkontroller** väljer du **Bevilja**.
14. I **Bevilja** väljer du **Bevilja åtkomst** och väljer sedan **Kräv multifaktorautentisering** .
    Markera inte **Kräv att enheten är markerad som kompatibel** eftersom det inte går att utvärdera regelefterlevnad för en enhet förrän den har registrerats.
15. Välj **Välj**.
16. I **Ny princip**, väljer du **Aktivera princip** > **På** och väljer sedan **Skapa**.



## <a name="next-steps"></a>Nästa steg

När slutanvändarna registrerar sina enheter måste de nu autentisera med en andra identifieringsmetod, till exempel PIN-kod, telefon eller biometrik.
