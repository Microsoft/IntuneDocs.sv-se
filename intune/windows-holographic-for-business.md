---
title: Hantera Windows Holographic-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Med Microsoft Intune kan du slutföra olika aktiviteter på enheter som kör Windows Holographic for Business, inklusive att konfigurera företagsportalen, skapa en policy för efterlevnad, anpassa OMA-URI-inställningar, distribuera appar, kategorisera enheter i grupper, skapa profiler, begränsa enheter, aktivera programuppdateringar, definiera användningsvillkor, konfigurera inställningar för VPN och trådlöst nätverk, och använda Hello för företag.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18f86580fc4c80fade7aeaa9678e9d8edac9a53e
ms.sourcegitcommit: b57be56524ddb5026fab94f7638dc516ed118325
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/03/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>Anpassa enheter som kör Windows Holographic med Intune

Microsoft Intune har stöd för enheter som kör Windows Holographic for Business, som till exempel [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/).

För att kunna hantera enheter som kör Windows Holographic med Microsoft Intune, måste du skapa en profil för uppgradering av utgåvan. Uppgraderingsprofilen uppgraderar enheter från Windows Holographic till Windows Holographic for Business. Du kan köpa Commercial Suite för att få licensen som krävs för uppgraderingen för Microsoft-HoloLens. Mer information finns i [Uppgradera enheter som kör Windows Holographic till Windows Holographic for Business](holographic-upgrade.md).

Du kan använda uppgifterna i den här artikeln till att hantera och anpassa dina enheter som kör Windows Holographic for Business. Du kan till exempel hantera programuppdateringar, konfigurera VPN-inställningar och mycket mer.

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) är en utmärkt resurs för att hantera och kontrollera dina enheter som kör Windows Holographic for Business. Med Intune och Azure AD kan du göra följande: 

- **[Konfigurera enheter som är anslutna till Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup)**: I Azure Active Directory (AD) kan du lägga till organisationens Windows 10 -enheter, inklusive enheter som kör Windows Holographic for Business. Den här funktionen gör att Azure AD kan styra enheten. Det säkerställer att dina användare kommer åt företagets resurser från enheter som uppfyller dina krav för säkerhet och efterlevnad.

  I artikeln med [introduktion till enhetshantering i Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction) finns mer information.

- **[Massregistrering för Windows-enheter](windows-bulk-enroll.md)**: Som administratör kan du ansluta ett stort antal nya Windows-enheter till Azure Active Directory (AD) och Intune. Den här funktionen kallas massregistrering och använder konfigurationspaket. Med dessa paket ansluts enheter som kör Windows Holographic for Business till Azure AD-klienten och registrerar dem i Intune.

## <a name="company-portal"></a>Företagsportal
**[Konfigurera företagsportalappen](company-portal-app.md)**

Intune innehåller en företagsportal där användarna får åtkomst till företagets data, registrerar enheter, installerar appar, kontaktar IT-avdelningen m.m. Du kan anpassa företagsportalappen för dina enheter som kör Windows Holographic for Business.

## <a name="compliance-policy"></a>Policy för efterlevnad
**[Skapa en policy för efterlevnad för enheter](compliance-policy-create-windows.md)**

Efterlevnadsprinciper är regler och inställningar som enheter måste uppfylla för att vara kompatibla. Du kan använda dessa principer med villkorlig åtkomst om du vill blockera åtkomst till företagsresurser för enheter som är inte kompatibla. I Intune kan du skapa efterlevnadsprinciper till att tillåta eller blockera åtkomst för enheter som kör Windows Holographic for Business. Du kan till exempel skapa en princip som kräver att BitLocker är aktiverat.

Se också **[Komma igång med efterlevnadsprinciper](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Distribuera och hantera appar
**[Lägga till appar i Intune](apps-add.md)**

Du kan lägga till appar på enheter som kör Windows Holographic for Business med hjälp av Intune. Det finns många sätt att distribuera appar på, bland annat:

- [Lägga till Microsoft Store-appar](store-apps-windows.md)
- [Lägga till appar som du skapar](lob-apps-windows.md)
- [Tilldela appar till grupper](apps-deploy.md)

Microsoft Intune kan distribuera universella Windows-appar till Microsoft HoloLens-enheter som kör Windows Holographic för företag. Du kan ladda upp app-paketen direkt i Intune Azure Portal eller distribuera dem från Microsoft-Store för företag. Se följande för mer information om relaterade områden:
- För att distribuera branschspecifika appar med Intune Azure Portal, se [Lägga till branschspecifika appar för Windows till Microsoft Intune](lob-apps-windows.md).
- För att distribuera appar med Microsoft Store för företag, se [Hantera appar som du har köpt från Microsoft Store för företag med Microsoft Intune](windows-store-for-business.md). 
- Mer information om app-hantering med Microsoft Intune finns i [Vad är app-hantering i Microsoft Intune](app-management.md).
- Mer information om hur du utvecklar appar Microsoft HoloLens finns i [Mixed reality-appar för Microsoft HoloLens](https://www.microsoft.com/hololens/apps). 

> [!NOTE]
> HoloLens-enheter som kör Windows 10 Holographic för företag 1607 stöder inte online-licensierade appar från Microsoft Store för företag. Läs mer i [Installera appar på HoloLens](https://docs.microsoft.com/en-us/hololens/hololens-install-apps).

## <a name="device-actions"></a>Enhetsåtgärder
Intune har vissa inbyggda åtgärder som gör att IT-administratörer kan utföra olika uppgifter, lokalt på enheten eller via fjärranslutning med Intune i Azure-portalen. Användare kan dessutom utfärda ett fjärrkommando från Intune-företagsportalen till privatägda enheter som har registrerats i Intune.

Följande inställningar kan användas för enheter som kör Windows Holographic for Business: 

- **[Fabriksåterställning](devices-wipe.md#factory-reset)**: Åtgärden **Fabriksåterställning** tar bort enheten från Intune och återställer enheten till fabriksinställningarna. Använd den här åtgärden innan du ger enheten till en ny användare eller om enheten tappas bort eller blir stulen.

- **[Ta bort företagsdata](devices-wipe.md#remove-company-data)**: Åtgärden **Ta bort företagsdata** tar bort enheten från Intune och tar bort data för hanterade appar, inställningar och e-postprofiler som tilldelats via Intune. Användarens personliga data finns kvar på enheten.

- **[Synkronisera enheter för att hämta de senaste principerna och åtgärderna](device-sync.md)**: **Synkroniseringsåtgärden** tvingar enheten att checka in i Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den. Den här funktionen hjälper dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

**[Vad är enhetshantering i Microsoft Intune?](device-management.md)** är en bra resurs för att lära dig hantera enheter med hjälp av Azure-portalen. 

## <a name="device-categories-and-groups"></a>Enhetskategorier och grupper
**[Kategorisera enheter i grupper](device-group-mapping.md)**

Med Intune kan du skapa enhetskategorier som automatiskt lägger till enheter i grupper baserat på kategorier som du skapar, till exempel försäljning, redovisning, personal och så vidare. Tanken är att göra det enklare att hantera enheter som kör Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Enhetens konfigurationsprofiler 
**[Kom igång med konfigurationsprofiler](device-profiles.md) och [skapa din egen profil](device-profile-create.md)**

Intune innehåller inställningar och funktioner som du kan aktivera eller inaktivera på olika enheter i din organisation. Dessa inställningar och funktioner hanteras med hjälp av profiler. Du kan till exempel skapa en profil som aktiverar Cortana eller använder Windows Defender SmartScreen på enheter som kör Windows Holographic for Business.

Du kan använda OMA-URI i dina profiler för att anpassa vissa inställningar, skapa enhetsbegränsningar och konfigurera ett virtuellt privat nätverk (VPN) och ett trådlöst nätverk.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Anpassa enhetsinställningar](custom-settings-windows-holographic.md)

Om du vill konfigurera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) kan du skapa en anpassad profil i Intune. Du kan använda OMA-URI-inställningar för att styra olika funktioner på dina Windows Holographic for Business-enheter, till exempel aktivera VPN eller söka efter uppdateringar på Microsoft Update.

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Enhetsbegränsningar](device-restrictions-windows-holographic.md)

Med enhetsbegränsningar kan du styra olika inställningar och funktioner på dina enheter, inklusive att kräva ett lösenord, installera appar från [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), aktivera Bluetooth och mycket mer. Dessa begränsningar skapas i en Intune-profil. Profilen kan tillämpas på flera enheter som kör Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Konfigurera VPN](vpn-settings-configure.md)

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. I Intune kan du skapa en VPN-profil med inställningar för enheter som kör Windows Holographic for Business. Du kan till exempel skapa en VPN-profil så att alla Windows Holographic för Business-enheter kan använda Citrix VPN som anslutningstyp.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Konfigurera ett trådlöst nätverk](wi-fi-settings-configure.md)

Du kan också skapa en profil för trådlöst nätverk i Intune för att tilldela trådlösa nätverksinställningar till dina Windows Holographic for Business-enheter. När du tilldelar en profil för trådlöst nätverk får dina slutanvändare åtkomst till företagets nätverk, utan att någon nätverkskonfiguration behövs. Du kan exempelvis skapa ett trådlöst nätverk som endast är dedikerat till dina Windows Holographic for Business-enheter.

## <a name="software-updates"></a>Programuppdateringar
**[Hantera programuppdateringar](windows-update-for-business-configure.md)**

Intune innehåller en funktion som kallas uppdateringsringar för Windows 10-enheter. I dessa uppdateringsringar finns en grupp med inställningar som avgör hur uppdateringar ska installeras. Du kan till exempel skapa en underhållsperiod för installation av uppdateringar, eller välja att datorn startas om när uppdateringarna har installerats. En uppdateringsring kan tillämpas på flera enheter som kör Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Villkor
**[Hantera företagets villkor för användaråtkomst](terms-and-conditions-create.md)**

Du kan kräva att användarna ska acceptera företagets villkor innan de kan registrera enheter och få åtkomst till företagets appar, inklusive sin e-post. I Intune kan du definiera hur villkoren ska visas i företagsportalen och dessutom tilldela dessa villkor till enheter som kör Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello för företag
**[Använda Windows Hello för företag](windows-hello.md)**

Hello för företag är en alternativ inloggningsmetod som använder ett Azure Active Directory-konto för att ersätta lösenord, smartkort eller virtuella smartkort. Med Hello för företag kan Windows Holographic for Business-enheter logga in med en PIN-kod som har en minimilängd som du har angett.
