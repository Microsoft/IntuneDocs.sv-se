---
title: "Återställa lösenord på Windows-enheter med Intune"
titlesuffix: Azure portal
description: "Läs mer om hur du kan använda Intune för att återställa lösenordet på Windows-enheter som kopplade till Microsofts tjänst för PIN-återställning.”"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: faf3e9b81f76755135f73f8753305d96d227ec14
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>Återställa lösenordet på Windows-enheter som är kopplade till Microsofts tjänst för PIN-återställning med hjälp av Intune

Funktionen för återställning av lösenord på Windows-enheter som är kopplade till Microsofts tjänst för PIN-återställning ger dig möjlighet att generera ett nytt lösenord för enheter som kör Windows 10 Mobile. Enheterna måste köra Windows 10 Creators Update eller senare.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds på Windows 10 Creators Update och senare (ansluten till Azure AD)
- Windows Phone – stöds inte
- iOS – stöds inte
- macOS – stöds inte
- Android – stöds inte


## <a name="before-you-start"></a>Innan du börjar

Innan du kan fjärråterställa lösenord på Windows-enheter som du hanterar måste du ansluta tjänsten för PIN-återställning till Intune-klienten och konfigurera alla enheter som du ska hantera. Följ anvisningarna nedan för att konfigurera:

### <a name="connect-intune-with-the-pin-reset-service"></a>Ansluta Intune till tjänsten för PIN-återställning

1. Besök [webbplatsen för integrering av Microsofts tjänst för PIN-återställning](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) och logga in med det klientadministratörskonto som du använder för att hantera Intune-klienten.
2. När du loggar in ska du klicka på **Acceptera** och ge tjänsten för PIN-återställning tillgång till ditt konto.<br>
![Behörighetssida för tjänsten för PIN-återställning](./media/pin-reset-service-application.png)
3. I Azure-portalen kan du kontrollera att Intune och tjänsten för PIN-återställning har integrerats från Enterprise-programmen. Bladet med alla program visas i nedanstående skärmbild:<br>
![Tjänsten för PIN-återställning i Azure](./media/pin-reset-service-home-screen.png)
4. Logga in på [webbplatsen](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) med autentiseringsuppgifterna för ditt Intune-klientadministratörskonto. Välj **Acceptera** igen för att ge tjänsten tillgång till ditt konto.

### <a name="configure-windows-devices-to-use-pin-reset"></a>Konfigurera vilka Windows-enheter som ska få använda PIN-återställning

Om du vill konfigurera PIN-återställning för de Windows-enheter som du hanterar kan du aktivera funktionen med hjälp av en [anpassad princip för Intune i Windows 10](custom-settings-windows-10.md). Konfigurera principen med hjälp av följande CSP-leverantörer (Configuration Service Provider):


- **För enheter** - **./Device/Vendor/MSFT/PassportForWork/*klient-ID*/Policies/EnablePinRecovery**

*klient-ID* hänvisar till ditt Azure Active Directory katalog-ID, som du kan hämta på sidan **Egenskaper** i Azure Active Directory.

Ange värdet för denna CSP till **Sant**.

## <a name="steps-to-reset-the-passcode"></a>Steg för att återställa lösenordet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter** väljer du **Hantera** > **Alla enheter**.
5. Välj den enhet som du vill återställa lösenordet för, gå till egenskapsbladet för enheten och välj **Nytt lösenord**.
6. En bekräftelse visas. Välj **Ja**. Lösenordet genereras och visas i portalen under de nästföljande sju dagarna.

## <a name="next-steps"></a>Nästa steg

Om återställningen av lösenordet misslyckas finns det en länk i portalen som du kan använda för att hitta mer information.


