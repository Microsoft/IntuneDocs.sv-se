---
title: "Appkonfigurationsprinciper för Intune"
titlesuffix: Microsoft Intune
description: "Läs om hur du använder appkonfigurationsprinciper på en iOS- eller Android-enhet i Intune."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 52e0906b58680fa0b5628b2b5fc7445f8135658a
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="app-configuration-policies-for-intune"></a>Appkonfigurationsprinciper för Intune

Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar när användarna kör en iOS- eller Android-app. En app kan till exempel kräva att användarna anger:

- ett anpassat portnummer
- språkinställningar
- säkerhetsinställningar
- anpassade inställningar, t.ex. en företagslogotyp.

Om användarna inte anger dessa inställningar på korrekt sätt kan det öka supportens arbetsbörda och ta längre tid att börja använda nya appar.

Med appkonfigurationsprinciper slipper du den här typen av problem eftersom du kan tilldela dessa inställningar till användarna i en princip innan de kör appen. Inställningarna distribueras sedan automatiskt utan att användarna behöver göra något.

Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem (oftast första gången den körs).

Du har två alternativ för hur du använder appkonfigurationer med Intune:
 - **Hanterade enheter**  
   Enheten hanteras av Intune som MDM-leverantör (hantering av mobila enheter).
 - **Hanterade appar**  
   En app hanteras utan enhetsregistrering.

## <a name="apps-that-support-app-configuration"></a>Appar som stöder appkonfiguration

Du kan använda principer för appkonfiguration för appar som stöder det. Appar måste ha skrivits för att stödja användning av appkonfigurationer för att ha stöd för appkonfiguration i Intune. Kontakta appleverantören om du vill ha mer information.

Du kan förbereda dina verksamhetsspecifika appar genom att antingen integrera Intune App SDK i appen eller genom att omsluta appen när den har utvecklats. Intune App SDK, som finns för både iOS och Android, gör det möjligt för din app att använda Intunes appskyddsprinciper. Den arbetar för att minimera mängden kodändringar i programmet som utvecklare behöver göra. Mer information finns i [Översikt över Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Graph API har stöd för appkonfiguration

Du kan även använda Graph API för att utföra de här uppgifterna för appkonfiguration. Mer information finns i [Graph API-referens för MAM-riktad konfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Nästa steg

### <a name="managed-devices"></a>Hanterade enheter

 - Lär dig hur du använder appkonfiguration med iOS-enheter.  Se [Lägg till konfigurationsprinciper för hanterade iOS-mobilappar](app-configuration-policies-use-ios.md).
 - Lär dig hur du använder appkonfiguration med Android-enheter.  Se [Lägg till konfigurationsprinciper för hanterade Android-enheter](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Hanterade appar

 - Lär dig hur du använder appkonfiguration med hanterade appar. Se [Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering](app-configuration-policies-managed-app.md).