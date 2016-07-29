---
title: "Använda hanterade appar på Android-enheten | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: angrobe
ms.date: 05/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
ROBOTS: noindex,nofollow
ms.reviewer: maxles
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 9e6ef6d4daf8507ed00cb5fa4a1d88f44a05068c


---


# Använda hanterade appar på Android-enheten

Hanterade appar är appar som IT-administratören kan konfigurera för att skydda de företagsdata som du kan komma åt i appen. När du använder företagets data i en hanterad app på en Android-enhet kan du märka att appen inte fungerar riktigt som du förväntat dig. Du kanske inte kan kopiera och klistra in skyddade företagsdata, eller så kanske du inte kan spara data på vissa platser.

Det kan också finnas flera hanterade appar som samverkar med varandra i enheten. Det gör att du kan utföra dina vardagsuppgifter samtidigt som företagets data skyddas. Om du till exempel öppnar en företagsfil i en hanterad app, och en annan hanterad app krävs för att visa filen, öppnas automatiskt den hanterade appen som gör att du kan visa filen. Om en nödvändig app inte är tillgänglig kanske du inte kan komma åt alla åtgärder. Du kanske inte kan öppna ett dokument eller använda en webblänk i ett hanterat dokument.

När du använder företagsdata i en hanterad app visas ett meddelande (se nedan) så att du vet att appen du öppnar är en hanterad app.

![open-managed-apps-message](./media/managed-apps-message.png)

## Hur skaffar jag hanterade appar?
Du kan hämta hanterade appar på ett par olika sätt:

-   När enheten har registrerats i Microsoft Intune installerar du appen från företagsportalappen eller företagsportalwebbplatsen. Alternativt kan IT-administratören installera den på enheten. Mer information om registrering finns i [Registrera din enhet i Intune](enroll-your-device-in-Intune-android.md).

-   Du installerar en app från Play Store och sedan loggar du in med ditt företagskonto som hanteras av Intune.

## Vad kan IT-administratören hantera i en app?
Här är några exempel på vad IT-administratören kan hantera i en app och hur det kan påverka din användning av företagsdata i enheten:

-   Åtkomst till vissa webbplatser

-   Överföring av data mellan appar

-   Spara filer

-   Kopiera och klistra in

-   Krav på åtkomst via PIN-kod

-   Din inloggning med företagets autentiseringsuppgifter

-   Möjligheten att säkerhetskopiera till molnet

-   Möjligheten att ta skärmdumpar

-   Krav på datakryptering

Några vanliga appar som IT-avdelningen kan hantera:

-   Intune Managed Browser

-   Intune Image Viewer

-   Intune PDF Viewer

-   Intune AV Player

-   Microsoft Word, Excel och PowerPoint

Kontakta IT-administratören om du vill ha mer information om hanterade appar på enheten. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).


### Se även
[Med hjälp av en Android-enhet med Intune](using-your-android-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


