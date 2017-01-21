---
title: "Använda hanterade appar på Android-enheten | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: maxles
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ca37b4bf393d03e61bed93fa8e7d83efe3922412


---


# <a name="use-managed-apps-on-your-android-device"></a>Använda hanterade appar på Android-enheten

Hanterade appar är appar som IT-administratören kan konfigurera för att skydda företagsdata som du kan komma åt i appen. När du använder företagets data i en hanterad app på en Android-enhet kanske du märker att appen inte fungerar riktigt som du förväntat dig. Du kanske inte kan kopiera och klistra in skyddade företagsdata, eller så kanske du inte kan spara data på vissa platser.

Det kan också finnas flera hanterade appar som samverkar med varandra i enheten. Det gör att du kan utföra dina vardagsuppgifter samtidigt som företagets data skyddas. Om du till exempel öppnar en företagsfil i en hanterad app, och en annan hanterad app krävs för att visa filen, öppnas automatiskt den hanterade appen som gör att du kan visa filen. Om en nödvändig app inte är tillgänglig kanske du inte kan komma åt alla åtgärder. Du kanske inte kan öppna ett dokument eller använda en webblänk i ett hanterat dokument.

När du använder företagsdata i en hanterad app visas ett meddelande (se nedan) så att du vet att appen du öppnar är en hanterad app.

![open-managed-apps-message](./media/managed-apps-message.png)

## <a name="how-do-i-get-managed-apps"></a>Hur skaffar jag hanterade appar?
Du kan hämta hanterade appar på ett par olika sätt:

-   När enheten har registrerats i Microsoft Intune installerar du appen från företagsportalappen eller företagsportalwebbplatsen. Alternativt kan IT-administratören installera den på enheten. Mer information om registrering finns i [Registrera din enhet i Intune](enroll-your-device-in-Intune-android.md).

-   Du installerar en app från Play Store och loggar sedan in med ditt företagskonto som hanteras av Intune.

## <a name="what-can-my-it-admin-manage-in-an-app"></a>Vad kan IT-administratören hantera i en app?
Här är några exempel på vad IT-administratören kan hantera i en app och hur det kan påverka din användning av företagsdata på din enhet:

-   Åtkomst till vissa webbplatser

-   Överföring av data mellan appar

-   Spara filer

-   Kopiera och klistra in

-   Krav på åtkomst via PIN-kod

-   Din inloggning, med företagets autentiseringsuppgifter

-   Möjligheten att säkerhetskopiera till molnet

-   Möjligheten att ta skärmdumpar

-   Krav på datakryptering

Några vanliga appar som IT-avdelningen kan hantera:

-   Intune Managed Browser

-   Intune Image Viewer

-   Intune PDF Viewer

-   Intune AV Player

-   Microsoft Word, Excel och PowerPoint

Kontakta IT-administratören om du vill ha mer information om hanterade appar på enheten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).



<!--HONumber=Dec16_HO2-->


