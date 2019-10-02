---
title: Använda Windows Holographic-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Med Microsoft Intune kan du hantera och slutföra olika aktiviteter på enheter som kör Windows Holographic for Business och HoloLens, inklusive att konfigurera företagsportalen, skapa en policy för efterlevnad, anpassa OMA-URI-inställningar, distribuera appar, kategorisera enheter i grupper, skapa profiler, begränsa enheter, aktivera programuppdateringar, definiera användningsvillkor, konfigurera inställningar för VPN och trådlöst nätverk, och använda Hello för företag.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9e50784529bb3128b08aa36859ca003f7c6f7691
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727798"
---
# <a name="manage-and-use-different-device-management-features-on-windows-holographic-and-hololens-devices-with-intune"></a>Hantera och använda olika enhetshanteringsfunktioner på Windows Holographic- och HoloLens-enheter med Intune

Microsoft Intune innehåller många funktioner för att hantera enheter som kör Windows Holographic for Business, såsom [Microsoft HoloLens](https://docs.microsoft.com/hololens/). Du kan använda Intune för att bekräfta att enheterna är kompatibla med regler för din organisation och du kan anpassa enheten genom att lägga till en VPN- eller Wi-Fi-profil. En annan viktig funktion är att använda enheten som en Kiosk och köra en viss app eller en specifik uppsättning av appar.

Aktiviteterna i den här artikeln hjälper dig att hantera, anpassa och skydda dina enheter som kör Windows Holographic for Business, inklusive programuppdateringar och använda Windows Hello för företag.

Om du vill använda Windows Holographic-enheter med Intune måste du skapa en profil för versionsuppgradering. Uppgraderingsprofilen uppgraderar enheter från Windows Holographic till Windows Holographic for Business. Du kan köpa Commercial Suite för att få licensen som krävs för uppgraderingen för Microsoft HoloLens. Mer information finns i [Uppgradera enheter som kör Windows Holographic till Windows Holographic for Business](../configuration/holographic-upgrade.md).

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) är en utmärkt resurs för att hantera och kontrollera dina enheter som kör Windows Holographic for Business. Med Intune och Azure AD kan du göra följande: 

- **[Anslut enheter till Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)** : I Azure Active Directory (AD) kan du lägga till organisationens Windows 10-enheter, inklusive enheter som kör Windows Holographic for Business. Den här funktionen gör att Azure AD kan styra enheten. Det hjälper till att bekräfta att användarna kommer åt företagets resurser från enheter som uppfyller dina säkerhets- och efterlevnadskrav.

  I [Enhetshantering i Azure AD](https://docs.microsoft.com/azure/active-directory/devices/overview) finns mer information.

- **[Massregistrering för Windows-enheter](../enrollment/windows-bulk-enroll.md)** : Du kan ansluta ett stort antal nya Windows-enheter till Azure Active Directory (AD) och Intune. Den här funktionen kallas massregistrering och använder konfigurationspaket. Med dessa paket ansluts enheter som kör Windows Holographic for Business till Azure AD-klienten och registrerar dem i Intune.

## <a name="company-portal"></a>Företagsportal
**[Konfigurera företagsportalappen](../apps/company-portal-app.md)**

Intune tillhandahåller företagsportalappen för användarna så att de kan få åtkomst till företagets data, registrera enheter, installera appar, kontakta IT-avdelningen m.m. Du kan anpassa företagsportalappen för dina enheter som kör Windows Holographic for Business.

Med företagsportalappen kan du också köra följande åtgärder:

- [Ta bort en enhet från Intune](/intune-user-help/unenroll-your-device-from-intune-windows) med inställningsappen eller företagsportalappen
- [Byta namn på en enhet](/intune-user-help/rename-your-device-cpapp)
- [Installera appar](/intune-user-help/install-apps-cpapp-windows) på en enhet
- [Synkronisera enheter manuellt](/intune-user-help/sync-your-device-manually-windows) från inställningsappen eller företagsportalappen

## <a name="compliance-policy"></a>Policy för efterlevnad
**[Skapa en policy för efterlevnad för enheter](../protect/compliance-policy-create-windows.md)**

Efterlevnadsprinciper är regler och inställningar som enheter måste uppfylla för att vara kompatibla. Använd dessa principer med villkorlig åtkomst för att blockera åtkomst till företagsresurser för enheter som är inte kompatibla. I Intune skapar du efterlevnadsprinciper för att tillåta eller blockera åtkomst för enheter som kör Windows Holographic for Business. Du kan till exempel skapa en princip som kräver att BitLocker är aktiverat.

Se också **[Komma igång med efterlevnadsprinciper](../protect/device-compliance-get-started.md)** .

## <a name="deploy-and-manage-apps"></a>Distribuera och hantera appar
**[Lägga till appar i Intune](../apps/apps-add.md)**

Du kan lägga till appar på enheter som kör Windows Holographic for Business med hjälp av Intune. Det finns många sätt att distribuera appar på, bland annat:

- [Lägga till Microsoft Store-appar](../apps/store-apps-windows.md)
- [Lägga till appar som du skapar](../apps/lob-apps-windows.md)
- [Tilldela appar till grupper](../apps/apps-deploy.md)

Microsoft Intune kan distribuera universella Windows-appar till Microsoft HoloLens-enheter som kör Windows Holographic för företag. Du kan ladda upp app-paketen direkt i Intune Azure Portal eller distribuera dem från Microsoft Store för företag. Se följande artiklar för mer information om relaterade områden:
- För att distribuera branschspecifika appar med Intune Azure Portal, se [Lägga till branschspecifika appar för Windows till Microsoft Intune](../apps/lob-apps-windows.md).

    > [!NOTE]
    > Intune tillåter en högsta paketstorleken på 8 GB. Den här paketstorleken är endast tillgänglig för LOB-appar som har överförts till Intune.

- För att distribuera appar med Microsoft Store för företag, se [Hantera appar som du har köpt från Microsoft Store för företag med Microsoft Intune](../apps/windows-store-for-business.md). 
- Mer information om app-hantering med Microsoft Intune finns i [Vad är app-hantering i Microsoft Intune](../apps/app-management.md).
- Mer information om hur du utvecklar appar Microsoft HoloLens finns i [Mixed reality-appar för Microsoft HoloLens](https://www.microsoft.com/hololens/apps). 

> [!NOTE]
> HoloLens-enheter som kör Windows 10 Holographic för företag 1607 stöder inte online-licensierade appar från Microsoft Store för företag. Läs mer i [Installera appar på HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps).

## <a name="device-actions"></a>Enhetsåtgärder
Intune har vissa inbyggda åtgärder som gör att IT-administratörer kan utföra olika uppgifter, lokalt på enheten eller via fjärranslutning med Intune i Azure-portalen. Användare kan dessutom utfärda ett fjärrkommando från Intune-företagsportalen till privatägda enheter som har registrerats i Intune.

Följande inställningar kan användas för enheter som kör Windows Holographic for Business: 

- **[Rensning](../remote-actions/devices-wipe.md#wipe)** : Åtgärden **Rensa** tar bort enheten från Intune och återställer enheten till fabriksinställningarna. Använd den här åtgärden innan du ger enheten till en ny användare eller om enheten tappas bort eller blir stulen.

- **[Dra tillbaka](../remote-actions/devices-wipe.md#retire)** : Åtgärden **Dra tillbaka** tar bort enheten från Intune. Den tar även bort hanterade appdata, inställningar och e-postprofiler som har tilldelats av Intune. Användarens personliga data finns kvar på enheten.

- **[Synkronisera enheter för att få de senaste principerna och åtgärderna](../remote-actions/device-sync.md)** : Åtgärden **Synkronisera** tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den. Den här funktionen hjälper dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

**[Vad är enhetshantering i Microsoft Intune?](../remote-actions/device-management.md)** är en bra resurs för att lära dig hantera enheter med hjälp av Azure-portalen. 

## <a name="device-categories-and-groups"></a>Enhetskategorier och grupper
**[Kategorisera enheter i grupper](../enrollment/device-group-mapping.md)**

Med Intune kan du skapa enhetskategorier som automatiskt lägger till enheter i grupper baserat på kategorier som du skapar, till exempel försäljning, redovisning, personal och så vidare. Tanken är att göra det enklare att hantera enheter som kör Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Enhetens konfigurationsprofiler 
**[Kom igång med konfigurationsprofiler](../configuration/device-profiles.md) och [skapa din egen profil](../configuration/device-profile-create.md)**

Intune innehåller inställningar och funktioner som du kan aktivera eller inaktivera på olika enheter i din organisation. Dessa inställningar och funktioner hanteras med hjälp av profiler. Du kan till exempel skapa en profil som aktiverar Cortana eller använder Windows Defender SmartScreen på enheter som kör Windows Holographic for Business.

Du kan använda OMA-URI i dina profiler för att anpassa vissa inställningar, skapa enhetsbegränsningar och konfigurera ett virtuellt privat nätverk (VPN) och ett trådlöst nätverk.

### <a name="custom-device-settingsconfigurationcustom-settings-windows-holographicmd"></a>[Anpassa enhetsinställningar](../configuration/custom-settings-windows-holographic.md)

Om du vill konfigurera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) kan du skapa en anpassad profil i Intune. Du kan använda OMA-URI-inställningar för att styra olika funktioner på dina Windows Holographic for Business-enheter, till exempel aktivera VPN eller söka efter uppdateringar på Microsoft Update.

### <a name="configure-kiosk-modeconfigurationkiosk-settings-holographicmd"></a>[Konfigurera kioskläge](../configuration/kiosk-settings-holographic.md)

Med hjälp av delnings- eller gästdatorfunktionerna i Intune kan du konfigurera Windows Holographic for Business-enheter så att de körs som kiosk. Dessa enheter kan köra en app (kioskläge med en app) eller flera appar (kioskläge med flera appar).

### <a name="device-restrictionsconfigurationdevice-restrictions-windows-holographicmd"></a>[Enhetsbegränsningar](../configuration/device-restrictions-windows-holographic.md)

Med enhetsbegränsningar kan du styra olika inställningar och funktioner på dina enheter, inklusive att kräva ett lösenord, installera appar från [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), aktivera Bluetooth och mycket mer. Dessa begränsningar skapas i en Intune-profil. Profilen kan tillämpas på flera enheter som kör Windows Holographic for Business.

### <a name="configure-vpnconfigurationvpn-settings-configuremd"></a>[Konfigurera VPN](../configuration/vpn-settings-configure.md)

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. I Intune kan du skapa en VPN-profil med inställningar för enheter som kör Windows Holographic for Business. Du kan till exempel skapa en VPN-profil så att alla Windows Holographic för Business-enheter kan använda Citrix VPN som anslutningstyp.

### <a name="configure-wi-ficonfigurationwi-fi-settings-configuremd"></a>[Konfigurera ett trådlöst nätverk](../configuration/wi-fi-settings-configure.md)

Du kan också skapa en profil för trådlöst nätverk i Intune för att tilldela trådlösa nätverksinställningar till dina Windows Holographic for Business-enheter. När du tilldelar en profil för trådlöst nätverk får dina slutanvändare åtkomst till företagets nätverk, utan att någon nätverkskonfiguration behövs. Du kan exempelvis skapa ett trådlöst nätverk som endast är dedikerat till dina Windows Holographic for Business-enheter.

## <a name="shared-multi-user-devices"></a>Delade enheter för flera användare
[Delade enheter](../configuration/shared-user-device-settings-windows-holographic.md)

Enheter som kör Windows Holographic for Business, till exempel Microsoft HoloLens, kan ha flera användare. Intune innehåller inställningar för att styra olika funktioner på de här delade enheterna, till exempel energisparfunktioner, användning av lokal lagring och kontohantering. Konfigurationsprofilerna kan också tillämpas på enheter med olika operativsystem. Enheter som kör RS2 och RS3 kan exempelvis ingå i samma grupp.

## <a name="software-updates"></a>Programuppdateringar
**[Hantera programuppdateringar](../protect/windows-update-for-business-configure.md)**

Intune innehåller en funktion som kallas uppdateringsringar för Windows 10-enheter. I dessa uppdateringsringar finns en grupp med inställningar som avgör hur uppdateringar ska installeras. Du kan till exempel skapa en underhållsperiod för installation av uppdateringar, eller välja att datorn startas om när uppdateringarna har installerats. En uppdateringsring kan tillämpas på flera enheter som kör Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Villkor
**[Hantera företagets villkor för användaråtkomst](../enrollment/terms-and-conditions-create.md)**

Du kan kräva att användarna ska acceptera företagets villkor innan de registrerar enheter och får åtkomst till företagets appar, inklusive sin e-post. I Intune definierar du hur villkoren ska visas i företagsportalen och tilldelar dessutom dessa villkor till enheter som kör Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello för företag
**[Använda Windows Hello för företag](../protect/windows-hello.md)**

Hello för företag är en alternativ inloggningsmetod som använder ett Azure Active Directory-konto för att ersätta lösenord, smartkort eller virtuella smartkort. Med Hello för företag kan Windows Holographic for Business-enheter logga in med en PIN-kod som har en minimilängd som du har angett.
