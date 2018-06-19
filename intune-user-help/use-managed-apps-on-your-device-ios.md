---
title: Använda hanterade appar på iOS-enheten | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 506b2e50333be9f284b7709fc2a57693330ff7a4
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31031659"
---
# <a name="use-managed-apps-on-your-ios-device"></a>Använda hanterade appar på iOS-enheten

Hanterade appar är appar som företagets support kan konfigurera för att skydda företagsdata som du kan komma åt i appen. När du använder företagets data i en hanterad app på en iOS-enhet kanske du märker att appen inte fungerar riktigt som du förväntat dig. Du kanske inte kan kopiera och klistra in skyddade företagsdata, eller så kanske du inte kan spara data på vissa platser.

Det kan också finnas flera hanterade appar som samverkar med varandra i enheten. Det gör att du kan utföra dina vardagsuppgifter samtidigt som företagets data skyddas. Om du till exempel öppnar en företagsfil i en hanterad app, och en annan hanterad app krävs för att visa filen, öppnas automatiskt den hanterade appen som gör att du kan visa filen. Om en nödvändig app inte är tillgänglig kanske du inte kan komma åt alla åtgärder. Du kanske inte kan öppna ett dokument eller använda en webblänk i ett hanterat dokument.

När du använder företagsdata i en hanterad app visas ett meddelande (se nedan) så att du vet att appen du öppnar är en hanterad app.

![managed-apps-message-ios](./media/managed-apps-message.png)

### <a name="how-do-i-get-managed-apps"></a>Hur skaffar jag hanterade appar?
Du kan hämta hanterade appar på ett par olika sätt:

-   När enheten har registrerats i Microsoft Intune installerar du appen från företagsportalappen eller företagsportalwebbplatsen. Alternativt kan företagets support installera den på enheten. Läs mer om hur du registrerar i [Registrera din iOS-enhet i Intune](enroll-your-device-in-intune-ios.md) eller [Registrera en macOS-enhet i Intune](enroll-your-device-in-intune-macos.md).

-   Du installerar en app från App Store och loggar sedan in med ditt företagskonto som hanteras av Intune.

Företagets support kan ibland köpa flera licenser för en app som du installerar. Om du ser ett meddelande som ber dig godkänna Apples Volymköpsprogram är det normalt och du kan godkänna det. Om du inte godkänner det kan du inte installera appen.

### <a name="what-can-my-company-support-manage-in-an-app"></a>Vad kan företagets support hantera i en app?
Följande är några exempel på vad företagets support kan hantera i en app och hur det kan påverka din användning av företagsdata på enheten:

-   Åtkomst till vissa webbplatser

-   Överföring av data mellan appar

-   Spara filer

-   Kopiera och klistra in

-   Krav på åtkomst via PIN-kod

-   Din inloggning, med företagets autentiseringsuppgifter

-   Möjligheten att säkerhetskopiera till molnet

-   Möjligheten att ta skärmdumpar

-   Krav på datakryptering

Kontakta företagets support om du vill ha mer information om hanterade appar på enheten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
