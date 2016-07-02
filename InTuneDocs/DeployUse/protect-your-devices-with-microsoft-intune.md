---
title: Skydda enheter | Microsoft Intune
description: 
keywords: 
author: Robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71e0cbf3-2bfb-412e-8a12-8503df08b4cf
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c52448ab454a764be922319fb930a85a86c3996e
ms.openlocfilehash: c8f833593e6a4606b0dd56373d4dc016c7ea0924


---

# Skydda enheter med Microsoft Intune
När dina enheter hanteras av Intune vill du antagligen se till att de skyddas mot obehörig åtkomst och andra hot. Här är exempel på några av funktionerna i Intune som hjälper dig att göra det.

> [!TIP]
> I det här avsnittet beskrivs inte alla metoder i Intune som du kan använda för att skydda dina enheter. Du kan till exempel använda Intune-principer för att konfigurera många säkerhetsinställningar för dina enheter, exempelvis konfigurera lösenord, ställa in kryptering och använda maskinvarufunktioner som Bluetooth och enhetens kamera. Mer information om dessa inställningar finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

## Återställa lösenord när användare har låsts ute från sina enheter
Det första steget för att skydda företagets data på mobila enheter är att kräva ett lösenord för att använda enheten. Det betyder att du ibland kan behöva [återställa ett lösenord](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) eller hjälpa en anställd att göra det, antingen genom att ta bort lösenordet eller genom att ställa in ett tillfälligt lösenord på distans. Du kan också [fjärrlåsa en enhet](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) om den blir stulen eller borttappad.

## Lägga till ett extra skyddslager för Windows-enheter
[Multifaktorautentisering (MFA)](protect-windows-devices-with-multi-factor-authentication.md) är ett säkrare sätt att autentisera användare av Windows- och Windows Phone-enheter i nätverket.  Med MFA behöver användare att bekräfta sin identitet utöver användarnamn och lösenord, via ett telefonsamtal eller ett textmeddelande.

## Kontrollera Microsoft Passport-inställningar på Windows-enheter
Med Intune kan du integrera [Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), som är en alternativ inloggningsmetod för Windows 10 och senare som använder Active Directory eller ett Azure Active Directory-konto i stället för ett lösenord, smartkort eller virtuellt smartkort.

## Förbikoppla aktiveringslåset på iOS-enheter
Aktiveringslåset är en funktion som skyddar användarnas enheter genom att kräva att deras Apple-ID och lösenord anges innan någon kan radera eller återaktivera enheten. Detta kan dock leda till problem, till exempel om användaren lämnar företaget utan att ta bort låset. [Kringgå aktiveringslås för iOS](help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune.md) kan hjälpa genom att ta bort låset från de övervakade iOS-enheterna så att du kan allokera eller radera dem.

## Skydda Windows-datorer som hanteras med Intune-klienten
Intune stöder fortfarande säkerhetsprinciper för Windows-datorer som du inte registrerar utan hanterar med Intune-klientprogrammet. Information om hur du kan skydda dina Windows-datorer med dessa principer finns i [Använd principer för att skydda Windows-datorer som kör Intune-klientprogramvaran](policies-to-protect-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Jun16_HO4-->


