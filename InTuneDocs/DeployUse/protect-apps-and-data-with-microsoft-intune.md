---
# required metadata

title: Skydda data och appar | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Skydda data och appar med Microsoft Intune


Intune skyddar företagets data via flera tekniklager.  I identitetslagret skyddas åtkomsten till tjänster med villkorlig åtkomst som endast tillåter åtkomst från hanterade och godkända enheter.  I klientprogramlagret skyddar MAM (Mobile App Management) mot dataförlust genom att förhindra att data flyttas till appar eller lagringsplatser som inte är skyddade och genom att rensa data om en enhet blir borttappad eller stulen.  Dessa två skyddslager bör användas tillsammans för att skydda data utan att den mobila arbetsstyrkans produktivitet påverkas.

Ett viktigt första steg för att skydda företagets data är att implementera villkorlig åtkomst som säkerställer att alla enheter som används för att komma åt dessa data är rätt skyddade, t.ex. med starka lösenord och kryptering, samt att de inte är jailbrokade. I Microsoft Intune kan du ange villkor som enheterna måste uppfylla innan de får tillgång till företagets e-post och data.

[Villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) baseras på två typer av principer som du kan definiera i Intune:
- [Efterlevnadsprinciper](introduction-to-device-compliance-policies-in-microsoft-intune.md) bestämmer en enhets efterlevnad. De utvärderar inställningar och villkor som:
  - PIN-koder och lösenord: Du kan skapa regler som kräver ett lösenord innan en enhet kan låsas upp, komplexitetskrav för lösenord och andra lösenordsinställningar.
  - Kryptering: IT-administratören kan begränsa åtkomsten till enheter som är krypterade.
  - Enheten är inte jailbrokad eller rotad: Intune kan känna av om en registrerad enhet är jailbrokad och du kan definiera principen så att åtkomsten till sådana enheter blockeras.
- [Principer för villkorlig åtkomst](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) konfigureras för en bestämd tjänst, t.ex. Exchange Online eller SharePoint Online. För varje tjänst kan du definiera vilka grupper av användare som dessa principer ska gälla för. Du kan till exempel bestämma att anställda på personalavdelningen bara ska kunna komma åt företagets e-post från registrerade enheter som uppfyller efterlevnadskraven.

Att skydda åtkomsten till företagets resurser är bara det första steget i att skydda företagets data. Du måste fortfarande kunna skydda informationen när användaren har kommit åt den på enheten. Nu kan informationen kopieras, flyttas och sparas till en annan plats eller delas. I Intune kan du komma runt det här problemet genom att begränsa eller förhindra dataflyttning med en uppsättning regler som:
- Förhindrar kopiering och inklistring eller dataöverföring utanför arbetskontexten.
- Förhindrar säkerhetskopiering till personlig molnlagring eller funktionen Spara som.
- Skyddar åtkomsten till appar genom att kräva PIN-kod/lösenord eller autentiseringsuppgifter för företaget.
- Tvingar alla länkar att öppnas i Intune Managed Browser.

Den här uppsättningen regler kallas för [hanteringsprinciper för mobila appar (MAM)](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).  MAM-principer kan tillämpas på appar som körs på enheter som kan, men som inte nödvändigtvis, hanteras av dig.  Du kan skydda företagets data genom att använda MAM-principer för enheter som är registrerade i Intune, enheter som är registrerade och som hanteras i en tredje parts MDM-lösning eller enheter som inte hanteras av dig, t.ex. personalägda enheter.

Om du vill associera en app med en MAM-princip måste Microsoft Intune App Software Development Kit (SDK) ingå i appen eller så använder du appomslutningsverktyget.

App SDK är till exempel inbyggt i appar som Microsoft Office-apparna. En fullständig lista över appar som stöds finns i [Microsoft Intunes galleri för mobilprogram](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) på sidan för Microsoft Intunes programpartner. Välj appen om du vill se vilka scenarier och plattformar som stöds och huruvida appen stöder flera identiteter.

Du kan också [aktivera dina egna anpassade affärsappar](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md) för användning med MAM-principer.

Förutom att förhindra eller begränsa dataflyttning om en enhet blir stulen eller borttappad eller om användaren inte längre arbetar på ditt företag, kan du [rensa företagsdata selektivt](wipe-managed-company-app-data-with-microsoft-intune.md), så att bara personliga data finns kvar.


<!--HONumber=Jun16_HO2-->


