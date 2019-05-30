---
title: Återställa lösenord på Windows-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Om du ska återställa lösenordet på Windows-enheter, installerar du Microsofts tjänst för PIN-återställning och Microsofts klient för PIN-återställning, skapar en enhetsprincip med ditt katalog-ID för Azure Active Directory och återställer sedan lösenordet i Azure-portalen med Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9e9fde8969de0690919b52c2f4d662470eb15ca
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048147"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Återställa lösenord på Windows-enheter med Intune

Du kan återställa lösenordet för Windows-enheter. Funktionen för lösenordsåterställning använder Microsofts tjänst för PIN-återställning till att generera ett nytt lösenord för enheter som kör Windows 10 Mobile. 

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows 10 Mobile med Creators Update eller senare (ansluten till Azure AD).

Följande plattformar stöds **inte**:
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>Auktorisera tjänster för PIN-återställning

Om du vill återställa lösenordet på Windows-enheter, publicerar du tjänsten för PIN-återställning på Intune-klienten.

1. Gå till [Microsofts tjänst för PIN-återställning](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) och logga in med klientorganisationens administratörskonto.
2. **Godkänn** medgivande för att PIN-återställningstjänsten får åtkomst till ditt konto: ![Godkänn PIN-återställningsserverns begäran om behörigheter](./media/pin-reset-service-home-screen.png)
3. Gå till [Microsofts klient för PIN-återställning](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) och logga in med klientorganisationens administratörskonto. **Godkänn** att klienten för PIN-återställning får åtkomst till ditt konto.
4. I [Azure-portalen](https://portal.azure.com) kontrollerar du att tjänsten för PIN-återställning finns med i listan över Enterprise-program (Alla program): ![Sidan för att återställa PIN-koden för tjänstbehörigheter](./media/pin-reset-service-application.png)

> [!NOTE]
> När du har godkänt begäranden om PIN-återställning får du antingen meddelandet `Page not found`, eller så verkar det som om ingenting händer. Detta är normalt. Kontrollera att de två programmen för PIN-återställning finns med i listan för din klientorganisation.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Konfigurera vilka Windows-enheter som ska få använda PIN-återställning

Om du vill konfigurera PIN-återställning för de Windows-enheter som du hanterar, kan du använda en [anpassad enhetsprincip för Intune i Windows 10](custom-settings-windows-10.md). Konfigurera principen med hjälp av följande CSP-leverantörer (Configuration Service Provider):

**Använda enhetsprincipen** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Ersätt ditt *klientorganisations-ID* med det Azure AD Directory-ID som finns i listan **Egenskaper** för Azure Active Directory i [Azure-portalen](https://portal.azure.com).

Ange värdet för denna CSP till **Sant**.

> [!TIP]
> När du har skapat principen kan du tilldela (eller distribuera) den till en grupp. Principen kan tilldelas till användar- eller enhetsgrupper. Om du tilldelar den till en användargrupp kan gruppen innehålla användare som har andra enheter, till exempel iOS. Tekniskt sett tillämpas principen inte, men dessa enheter ingår ändå i statusinformationen.

## <a name="reset-the-passcode"></a>Återställa lösenordet

1. Logga in på [Azure Portal](https://portal.azure.com). 
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** och sedan **Alla enheter**.
4. Välj den enhet som du vill återställa lösenordet för. I egenskaperna för enheten väljer du **Nytt lösenord**.
5. Välj **Ja** för att bekräfta. Lösenordet genereras och visas i portalen under de nästföljande sju dagarna.

## <a name="next-step"></a>Nästa steg

Om återställningen av lösenordet misslyckas, finns det en länk i portalen med mer information.
