---
title: Skydda enheter med Microsoft Intune
description: "Läs olika exempel på hur Intune kan hjälpa dig att skydda dina enheter mot obehörig åtkomst och andra hot."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c866f2a8eebdb2f6c07314b745f65c06e3469e4e
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="protect-devices-with-microsoft-intune"></a>Skydda enheter med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I Microsoft Intune finns en fullständig uppsättning funktioner som hjälper dig att skydda de enheter som du hanterar och de data som lagras på dessa enheter. I det här avsnittet får du lära dig grunderna om funktionerna och veta hur du lär dig mer.

## <a name="general-ways-to-protect-all-devices"></a>Generella metoder för att skydda alla enheter

### <a name="device-configuration"></a>Enhetskonfiguration
Med Intune [konfigurationsprinciper](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) kan du skydda och konfigurera enheter med hjälp av flera inställningar och funktioner. Exempel:
- Du kan begränsa användningen av maskinvarufunktioner på enheten, till exempel kameran eller Bluetooth.
- Du kan konfigurera kompatibla och icke-kompatibla appar. Du får en varning om en icke-kompatibel app installeras (och på vissa plattformar kan installationen blockeras).

### <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Återställa lösenord när användare har låsts ute från sina enheter
Det första steget för att skydda företagets data på mobila enheter är att kräva ett lösenord för att använda enheten. Det betyder att du ibland kan behöva [återställa ett lösenord](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) eller hjälpa en anställd att göra det, antingen genom att ta bort lösenordet eller genom att ställa in ett tillfälligt lösenord på distans. Du kan också [fjärrlåsa en enhet](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) om den blir stulen eller borttappad.

### <a name="retire-devices-and-remove-data"></a>Dra tillbaka enheter och ta bort data
När en enhet behöver [tas bort från Intune-hanteringen](retire-devices-from-microsoft-intune-management.md) (till exempel om en användare lämnar företaget eller om enheten blir stulen) vill du förmodligen ta bort data från enheten. I Intune finns flera metoder för att skydda företagets data.

### <a name="require-devices-to-be-compliant"></a>Kräv att enheter är kompatibla
I Intune finns [efterlevnadsprinciper för enheter](introduction-to-device-compliance-policies-in-microsoft-intune.md) som gör att du kan utvärdera (och i vissa fall reparera) enheter som inte uppfyller de regler som du anger. Du kan till exempel rapportera om iOS-enheter som är jailbrokade, om enheter är krypterade eller inte eller om Windows 10-enheter rapporteras som felfria eller inte av hälsoattesteringstjänsten.

### <a name="protect-apps-and-the-data-they-use"></a>Skydda appar och de data som de använder
I Intune finns flera funktioner som hjälper dig att skydda appar och deras data. Med principer för hantering av mobilprogram (MAM) kan du till exempel förhindra att data säkerhetskopieras från en skyddad app, begränsa kopiering och inklistring till andra appar och kräva en PIN-kod att få åtkomst till en app. Mer information om hur du skyddar appar finns i [Skydda data och appar med Microsoft Intune](protect-apps-and-data-with-microsoft-intune.md)

### <a name="add-an-additional-layer-of-protection-to-devices"></a>Lägga till ett extra skyddslager för enheter
[Multi-Factor Authentication (MFA)](multi-factor-authentication-azure-active-directory.md) är ett säkrare sätt att autentisera enhetsanvändare i nätverket.  Med MFA måste användarna bekräfta sin identitet utöver användarnamn och lösenord, via ett telefonsamtal eller SMS.

## <a name="further-capabilities-for-windows-devices"></a>Ytterligare funktioner för Windows-enheter

### <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Kontrollera Windows Hello för företag-inställningar på Windows-enheter
Med Intune kan du integrera [Windows Hello för företag](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (tidigare Microsoft Passport), som är en alternativ inloggningsmetod för Windows 10 och senare som använder Active Directory eller ett Azure Active Directory-konto i stället för ett lösenord, smartkort eller virtuellt smartkort.

## <a name="further-capabilities-for-ios-devices"></a>Ytterligare funktioner för iOS-enheter

### <a name="bypass-activation-lock-on-ios-devices"></a>Förbikoppla aktiveringslåset på iOS-enheter
Aktiveringslåset är en funktion som skyddar användarnas enheter genom att kräva att deras Apple-ID och lösenord anges innan någon kan radera eller återaktivera enheten. Detta kan dock leda till problem, till exempel om användaren lämnar företaget utan att ta bort låset. [Kringgå aktiveringslås för iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) kan hjälpa genom att ta bort låset från de övervakade iOS-enheterna så att du kan allokera eller radera dem.



## <a name="protect-windows-pcs-managed-with-the-intune-client"></a>Skydda Windows-datorer som hanteras med Intune-klienten
Intune stöder fortfarande säkerhetsprinciper för Windows-datorer som du inte registrerar utan hanterar med Intune-klientprogrammet. Information om hur du kan skydda dina Windows-datorer med dessa principer finns i [Använd principer för att skydda Windows-datorer som kör Intune-klientprogramvaran](policies-to-protect-windows-pcs-in-microsoft-intune.md).
