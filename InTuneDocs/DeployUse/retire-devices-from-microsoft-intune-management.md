---
# required metadata

title: Dra tillbaka enheter | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Dra tillbaka enheter från Intune-hanteringen

Oavsett om enheter är företagsägda eller privata kommer det en tidpunkt då en hanterad enhet behöver tas bort från Intune-hanteringen. Processen är relativt enkel. Du utför antingen en selektiv eller en fullständig rensning.
## Rensa data och appar från enheter
Både en selektiv rensning och en fullständig rensning tar bort enheten från Intune-hanteringen genom att ta bort enhetens princip och företagsportalen, vilket innebär att enheten inte längre har de autentiseringsuppgifter som krävs för att logga in till företagsresurser, till exempel Microsoft SharePoint, e-post eller Office 365.

[Selektiv rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) är det bästa alternativet för medarbetare som registrerat sin egen enhet i Intune eftersom det inte påverkar personlig information på enheten. Endast företagsdata tas bort.

För företagsägda enheter kan du också använda en [fullständig rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe), som återställer enheten till fabriksinställningarna.

## Återkalla åtkomst till företagets nätverk
Om du drar tillbaka en enhet på grund av att en medarbetare har slutat på företaget och glömt att lämna tillbaka företagsägd maskinvara, kan du även [fjärrlåsa](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) enheten. Därmed skyddas både företagsdata och du förhindrar att enheten missbrukas, även om du kanske får skriva av den som en förlust.

Du bör också återkalla licensen för medarbetarens Intunekonto.. Detta frigör licensen som du kan tilldela till ett nytta användarkonto.

## Göra sig av med maskinvara
Ibland är det själva enheten som blivit för gammal. I sådana fall tar en [återställning till fabriksinställningarna](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) med en fullständig rensning bort alla data och tar bort enheten från Intune. Sen kan du göra dig av med maskinvaran i enlighet med företagets policy.

### Se även
[Skydda dina data med en fullständig eller selektiv rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)


<!--HONumber=May16_HO2-->


