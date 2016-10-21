---
title: Skydda enheter | Microsoft Intune
description: "Läs olika exempel på hur Intune kan hjälpa dig att skydda dina enheter mot obehörig åtkomst och andra hot."
keywords: 
author: Robstackmsft
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3e761ed60fe3df81061023aa31e0545aeeadd316
ms.openlocfilehash: be5051c46e1ef04ea140c9d440720f570edcbd1e


---

# Skydda enheter med Microsoft Intune

I Microsoft Intune finns en fullständig uppsättning funktioner som hjälper dig att skydda de enheter som du hanterar och de data som lagras på dessa enheter. I det här avsnittet får du lära dig grunderna om funktionerna och veta hur du lär dig mer.

## Generella metoder för att skydda alla enheter

### Enhetskonfiguration
Med Intune [konfigurationsprinciper](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) kan du skydda och konfigurera enheter med hjälp av flera inställningar och funktioner. Exempel:
- Du kan begränsa användningen av maskinvarufunktioner på enheten, till exempel kameran eller Bluetooth.
- Du kan konfigurera kompatibla och icke-kompatibla appar. Du får en varning om en icke-kompatibel app installeras (och på vissa plattformar kan installationen blockeras).

### Återställa lösenord när användare har låsts ute från sina enheter
Det första steget för att skydda företagets data på mobila enheter är att kräva ett lösenord för att använda enheten. Det betyder att du ibland kan behöva [återställa ett lösenord](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) eller hjälpa en anställd att göra det, antingen genom att ta bort lösenordet eller genom att ställa in ett tillfälligt lösenord på distans. Du kan också [fjärrlåsa en enhet](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) om den blir stulen eller borttappad.

### Dra tillbaka enheter och ta bort data
När en enhet behöver [tas bort från Intune-hanteringen](retire-devices-from-microsoft-intune-management) (till exempel om en användare lämnar företaget eller om enheten blir stulen) vill du förmodligen ta bort data från enheten. I Intune finns flera metoder för att skydda företagets data.

### Kräv att enheter är kompatibla
I Intune finns [efterlevnadsprinciper för enheter](introduction-to-device-compliance-policies-in-microsoft-intune) som gör att du kan utvärdera (och i vissa fall reparera) enheter som inte uppfyller de regler som du anger. Du kan till exempel rapportera om iOS-enheter som är jailbrokade, om enheter är krypterade eller inte eller om Windows 10-enheter rapporteras som felfria eller inte av hälsoattesteringstjänsten.

### Skydda appar och de data som de använder
I Intune finns flera funktioner som hjälper dig att skydda appar och deras data. Med principer för hantering av mobilprogram (MAM) kan du till exempel förhindra att data säkerhetskopieras från en skyddad app, begränsa kopiering och inklistring till andra appar och kräva en PIN-kod att få åtkomst till en app. Mer information om hur du skyddar appar finns i [Skydda data och appar med Microsoft Intune](protect-apps-and-data-with-microsoft-intune)

## Ytterligare funktioner för Windows-enheter

### Lägga till ett extra skyddslager för Windows-enheter
[Multifaktorautentisering (MFA)](protect-windows-devices-with-multi-factor-authentication.md) är ett säkrare sätt att autentisera användare av Windows- och Windows Phone-enheter i nätverket.  Med MFA måste användarna bekräfta sin identitet utöver användarnamn och lösenord, via ett telefonsamtal eller SMS.

### Kontrollera Windows Hello för företag-inställningar på Windows-enheter
Med Intune kan du integrera [Windows Hello för företag](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) (tidigare Microsoft Passport), som är en alternativ inloggningsmetod för Windows 10 och senare som använder Active Directory eller ett Azure Active Directory-konto i stället för ett lösenord, smartkort eller virtuellt smartkort.

## Ytterligare funktioner för iOS-enheter

### Förbikoppla aktiveringslåset på iOS-enheter
Aktiveringslåset är en funktion som skyddar användarnas enheter genom att kräva att deras Apple-ID och lösenord anges innan någon kan radera eller återaktivera enheten. Detta kan dock leda till problem, till exempel om användaren lämnar företaget utan att ta bort låset. [Kringgå aktiveringslås för iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) kan hjälpa genom att ta bort låset från de övervakade iOS-enheterna så att du kan allokera eller radera dem.



## Skydda Windows-datorer som hanteras med Intune-klienten
Intune stöder fortfarande säkerhetsprinciper för Windows-datorer som du inte registrerar utan hanterar med Intune-klientprogrammet. Information om hur du kan skydda dina Windows-datorer med dessa principer finns i [Använd principer för att skydda Windows-datorer som kör Intune-klientprogramvaran](policies-to-protect-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Sep16_HO1-->


