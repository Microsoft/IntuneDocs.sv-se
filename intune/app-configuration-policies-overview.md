---
title: Appkonfigurationsprinciper för Microsoft Intune
titlesuffix: ''
description: Läs om hur du använder appkonfigurationsprinciper på en iOS- eller Android-enhet i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/03/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1100be1b4df5bdd6c794cf6527a9ff9ad42fecd5
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849031"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Appkonfigurationsprinciper för Microsoft Intune

Använd appkonfigurationsprinciper i Microsoft Intune för att ge konfigurationsinställningar för en iOS- eller Android-app. Med de här konfigurationsinställningarna kan en app anpassas. Du tilldelar inte de konfigurationsprinciperna direkt till användare och enheter. I stället associerar du konfigurationsprincipen med en app och tilldelar sedan appen. Inställningarna för konfigurationsprincipen används när appen söker efter dem, oftast första gången den körs.

Du kan tilldela en appkonfigurationsprincip till en grupp användare och enheter genom att använda en kombination av tilldelningar som inkluderar och exkluderar. När du lägger till en appkonfigurationsprincip kan du ange tilldelningar för den. När du anger tilldelningar för principen kan du välja att inkludera och exkludera grupper av användare som principen ska gälla för. När du väljer att inkludera en eller flera grupper kan du välja att utse specifika grupper att inkludera eller välja inbyggda grupper. Inbyggda grupper innefattar **Alla användare**, **Alla enheter** samt **Alla användare + alla enheter**.

Till exempel kan en app kräva att du anger några av de följande uppgifterna:

- Ett anpassat portnummer
- Språkinställningar
- Säkerhetsinställningar
- Anpassade inställningar, t.ex. en företagslogotyp

Om användarna inte anger dessa inställningar på korrekt sätt kan det öka supportens arbetsbörda och ta längre tid att börja använda nya appar.

Med appkonfigurationsprinciper slipper du den här typen av problem eftersom du kan tilldela dessa inställningar till användarna i en princip innan de kör appen. Inställningarna distribueras sedan automatiskt utan att användarna behöver göra något.

Konfigurationsinställningarna används när appen söker efter dem. Normalt söker en app efter konfigurationsinställningar första gången appen körs av användaren.

Du har två alternativ för hur du använder appkonfigurationer med Intune:
 - **Hanterade enheter** – enheten hanteras av Intune som MDM-leverantör (hantering av mobila enheter).
 - **Hanterade appar** – en app hanteras utan enhetsregistrering.

> [!NOTE]
> Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. De stödjande programmen bearbetar appkonfigurationen och tar bort och blockerar icke-godkända konton.

## <a name="apps-that-support-app-configuration"></a>Appar som stöder appkonfiguration

Du kan använda principer för appkonfiguration för appar som stöder det. Appar måste ha skrivits för att stödja användning av appkonfigurationer för att ha stöd för appkonfiguration i Intune. Kontakta appleverantören om du vill ha mer information.

Du kan förbereda dina verksamhetsspecifika appar genom att antingen integrera Intune App SDK i appen eller genom att omsluta appen när den har utvecklats. Intune App SDK, som finns för både iOS och Android, gör det möjligt för din app att använda Intunes appkonfigurationsprinciper. Den arbetar för att minimera mängden kodändringar i programmet som utvecklare behöver göra. Mer information finns i [Översikt över Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Graph API har stöd för appkonfiguration

Du kan även använda Graph API för att utföra de här uppgifterna för appkonfiguration. Mer information finns i [Graph API-referens för MAM-riktad konfiguration](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Nästa steg

### <a name="managed-devices"></a>Hanterade enheter

 - Lär dig hur du använder appkonfiguration med iOS-enheter.  Se [Lägg till konfigurationsprinciper för hanterade iOS-mobilappar](app-configuration-policies-use-ios.md).
 - Lär dig hur du använder appkonfiguration med Android-enheter.  Se [Lägg till konfigurationsprinciper för hanterade Android-enheter](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>Hanterade appar

 - Lär dig hur du använder appkonfiguration med hanterade appar. Se [Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering](app-configuration-policies-managed-app.md).
