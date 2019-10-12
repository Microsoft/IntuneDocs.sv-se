---
title: Registrera din iOS-enhet som tillhandahålls av organisationen i hanteringen. | Microsoft Docs
description: Beskriver hur du registrerar en iOS-enhet i Intune som har köpts och tillhandahålls av din organisation
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0719aca1dbb84358b0c54fbfac57143d2a77c0de
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163461"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>Registrera din iOS-enhet som tillhandahålls av organisationen i hanteringen

Läs om hur du får en ny iOS-enhet hanterad i Intune.  

iOS-enheter som tillhandahålls till dig av arbete eller skola är ofta förkonfigurerade innan du tar emot dem. Din organisation skickar dessa förkonfigurerade inställningar till enheten när du startar den och loggar in för första gången. När installationen är färdig får du tillgång till arbetets eller skolans resurser.  

Du påbörjar konfigureringen genom att starta din enhet och logga in med dina inloggningsuppgifter för arbetet eller skolan. Resten av den här artikeln beskriver stegen och de skärmar du kommer att se i installationsassistenten.

## <a name="what-is-apple-dep"></a>Vad är Apple DEP?

Organisationen kanske har köpt sina enheter via något som kallas *Apples program för enhetsregistrering* (DEP). Apple DEP gör det möjligt för organisationer att köpa stora mängder iOS- eller macOS-enheter. Organisationer kan sedan konfigurera och hantera dessa enheter i önskad provider för hantering av mobila enheter, som Intune. Om du är administratör och vill ha mer information om Apple DEP kan du läsa [Automatisk registrering av iOS-enheter i Apples program för enhetsregistrering](/intune/enrollment/device-enrollment-program-enroll-ios).

## <a name="set-up-your-ios-device"></a>Konfigurera din iOS-enhet

Om du använder en egen iOS-enhet i stället för en enhet som tillhandahålls av organisationen följer du de här stegen för [egna enheter](enroll-your-device-in-intune-ios.md).  

1. Sätt igång din iOS-enhet.
2. När du har valt **språk** ansluter du enheten till Wi-Fi.
3. På skärmen för att **konfigurera iOS-enhet** väljer du om du vill:
   - **Set Up as New device** (Konfigurera som ny enhet)
   - **Restore from iCloud Backup** (Återställ från iCloud-säkerhetskopia)
   - **Restore from iTunes Backup** (Återställ från iTunes-säkerhetskopia)

4. När du har anslutit till Wi-Fi visas skärmen **Konfiguration**. Skärmen meddelar att **[ditt företag] kommer att konfigurera din enhet automatiskt**.

   **Med konfigurationen kan [Ditt företag] att hantera enheten trådlöst. En administratör kan hjälpa dig att konfigurera e-post och nätverkskonton, installera och konfigurera appar, samt fjärrhantera inställningar. En administratör kan inaktivera funktioner, installera och ta bort appar, övervaka och begränsa Internet-trafiken, samt fjärradera den här enheten.**

   **Konfigurationen tillhandahålls av: [Ditt företags] iOS-team [Adress]**

5. Logga in med ditt Apple-ID. När du har loggat in kan du installera företagsportalappen och hanteringsprofilen som ger dig åtkomst till företagets resurser, t.ex. e-post och appar.
6. Godkänn **villkoren** och välj om du vill skicka diagnostikinformation till Apple eller inte.
7. När du har slutfört registreringen kan du uppmanas att utföra fler åtgärder. I några av de här stegen kan du behöva ange lösenordet för e-poståtkomst eller konfigurera ett lösenord.

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
