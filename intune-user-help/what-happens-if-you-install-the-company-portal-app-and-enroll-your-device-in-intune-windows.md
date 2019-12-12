---
title: Installera företagsportalappen för Windows | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16b51322cbbdf585d44d7b6c54af11f01531a9a6
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506029"
---
# <a name="what-happens-if-you-install-the-company-portal-app-and-enroll-your-windows-device-in-intune"></a>Vad händer om du installerar företagsportalappen och registrerar din Windows-enhet i Intune?

När du installerar företagsportalappen och sedan använder den för att registrera en Windows- eller Windows Phone-enhet låter du företagets support hantera din enhet för att skydda företags- eller skoldata. Det här avsnittet beskriver vad som händer med enheter som är äldre än Windows 10. För Windows 10-enheter läser du [motsvarande avsnitt](about-cp-app-for-windows-10.md).  

## <a name="what-happens-to-all-windows-devices-after-enrollment"></a>Vad händer med alla Windows-enheter efter registreringen?
Om du registrerar en Windows- eller Windows Phone-enhet i Intune kan du:

- Komma åt företagets nätverk, samt dina e-post- och arbetsfiler.

- Hämta företagsappar från webbplatsen för företagsportalen. (__Obs!__ För Windows 7 och Windows Vista kan du bara hämta företagsappar från webbplatsen för företagsportalen.)

- Konfigurera ditt företags eller din skolas e-postkonto automatiskt.

- Återställa din telefon till fabriksinställningarna om den tappas bort eller blir stulen.

När du registrerar en enhet ger du företagets support tillstånd att till exempel:

- Återställa enheten till tillverkarens standardinställningar. Det är bra om enheten tappas bort eller blir stulen.

- Ta bara bort företagsrelaterade filer och företagsappar. *Dina personliga data och inställningar tas inte bort.*

- Företagets support kan se vilka program som är installerade på enheten, inklusive programvara som du har installerat själv.

- Ange krav för enheten, till exempel för att kräva ett lösenord eller en PIN-kod för enheten för att skydda företagsdata. Företagets support kan också begränsa hur många gånger du kan ange ett felaktigt lösenord, och kan låsa dig ute från enheten om du försöker för många gånger.

- Kräva att du krypterar data på din enhet för att skydda företagsdata, om enheten förloras eller blir stulen.

- Kräva att du accepterar villkoren.

- Förhindra dig att ta bilder av företagsrelaterade data.

## <a name="what-happens-to-all-windows-pcs-after-enrollment"></a>Vad händer med alla Windows-datorer efter registreringen?

- Programvara installeras på datorn så att företagets support kan hantera datorn och så att du kan komma åt företagsresurser som appar och supportinformation. Företagets support kan uppdatera den här programvaran automatiskt.

- Intune Endpoint Protection kanske är installerat på datorn. Det här programmet söker efter virus och skadlig kod.

- Företagets support kan samla in eller radera data från datorns hårddisk.

- Företagets support kan installera appar och uppdateringar på datorn.

## <a name="what-happens-every-eight-hours-after-device-enrollment"></a>Vad händer var åttonde timme efter enhetsregistreringen?

Ungefär var åttonde timme kommer registrerade enheter att:

- Hämta eventuella uppdateringar av principer eller appar som företagets support har gjort tillgängliga.

- Skicka eventuella uppdateringar av hårdvaruförteckningen.

- Skicka eventuella uppdateringar av förteckningar över företagsappar.

Kontakta företagets support om du har frågor. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
