---
title: Felsöka villkorlig åtkomst
titleSuffix: Microsoft Intune
description: Vad du kan göra om dina användare inte lyckas komma åt resurser via Villkorsstyrd åtkomst i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e8ebc708f76ed1f55f512edda75206d3ed5890a0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530731"
---
# <a name="troubleshoot-conditional-access"></a>Felsöka villkorlig åtkomst

Du kan skydda åtkomsten till Office 365-tjänster som Exchange Online, SharePoint Online, Skype för Business Online och Exchange On-Premises och andra tjänster med hjälp av Intune och Villkorsstyrd åtkomst. Med den här funktionen kan du se till att åtkomsten till företagsresurser är begränsad till enheter som har registrerats med Intune och som är kompatibla med reglerna för Villkorsstyrd åtkomst som du anger i Intune-administratörskonsolen eller i Azure Active Directory. Den här artikeln beskriver vad du gör om dina användare inte kan komma åt resurser som skyddas med Villkorsstyd åtkomst, eller om användare kan komma åt skyddade resurser men ska blockeras.

## <a name="requirements-for-conditional-access"></a>Krav för Villkorsstyrd åtkomst

Följande krav måste uppfyllas för att Villkorsstyrd åtkomst ska fungera:

- Enheten måste vara registrerad i och hanteras av Intune.
- Både användaren och enheten måste vara kompatibla med de tilldelade efterlevnadsprinciperna för Intune.
- Användaren måste som standard tilldelas en enhetsefterlevnadsprincip. Detta kan bero på hur inställningen **Markera enheter som saknar efterlevnadsprincip som** har konfigurerats under **Enhetsefterlevnad** > **Kompatibilitetsprincipinställningar** på Intune-administrationsportalen.
- Exchange ActiveSync måste vara aktiverat på enheten om användaren använder enhetens inbyggda e-postklient i stället för Outlook. Detta sker automatiskt för iOS-, Windows Phone- och Android-enheter.
- Intune Exchange Connector måste vara korrekt konfigurerad. Mer information finns i [Felsöka Exchange Connector i Microsoft Intune](troubleshoot-exchange-connector.md).

Du kan se dessa villkor för varje enhet i Azure-portalen och i inventeringsrapporten för enheten.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Enheterna ser ut att vara kompatibla men användarna blockeras ändå

- Android-enheter utan Knox beviljas inte åtkomst förrän användaren klickar på länken **Kom igång nu** i karantänmeddelandet som skickas till användarens e-postadress. Detta gäller även om användaren redan har registrerats i Intune. Om användaren inte får e-postmeddelandet med länken på sin telefon, kan han eller hon använda en dator för att komma åt sin e-post och vidarebefordra det till ett e-postkonto på enheten.
- Första gången en enhet registreras kan det ta lite tid innan kompatibilitetsinformationen registreras för en enhet. Vänta några minuter och försök igen.
- För iOS-enheter kan en befintlig e-postprofil blockera distributionen av en e-postprofil som skapats av en Intune-administratör och tilldelats användaren, vilket gör enheten inkompatibel. I det här scenariot meddelar företagsportalen användaren att enheten inte är kompatibel på grund av en manuellt konfigurerad e-postprofil, och användaren uppmanas att ta bort profilen. När användaren har tagit bort den befintliga e-postprofilen distribueras e-postprofilen för Intune korrekt. Du kan förhindra det här problemet genom att be användarna att ta bort alla befintliga e-postprofiler på deras enheter före registreringen.
- En enhet kan fastna i ett tillstånd där efterlevnaden kontrolleras, vilket hindrar användaren från att påbörja en ny incheckning. Om du har en enhet i det här tillståndet kan du prova följande:
  - Kontrollera att enheten använder den senaste versionen av företagsportalappen.
  - Starta om enheten.
  - Kontrollera om problemet är begränsat till särskilda nätverk (t.ex. mobilnät, Wi-Fi osv.).

  Om problemet kvarstår kontaktar du Microsoft Support genom att följa anvisningarna i [Få support för Microsoft Intune](get-support.md).
- Vissa Android-enheter kan se ut att vara krypterade, men företagsportalappen identifierar dessa enheter som okrypterade, och markerar dem därför som inkompatibla. I det här scenariot ser användarna ett meddelande i företagsportalappen som ber dem att ange ett startlösenord för enheten. När du har tryckt på meddelandet och bekräftat den befintliga PIN-koden eller det befintliga lösenordet väljer du alternativet **Kräv PIN-kod för att starta enheten** på skärmen **Säker start** och trycker sedan på knappen **Kontrollera efterlevnad** för enheten från företagsportalappen. Enheten bör nu identifieras som krypterad. 
  > [!NOTE]
  > Vissa enhetstillverkare krypterar sina enheter med en standard-PIN-kod i stället för en PIN-kod som användaren anger. Intune betraktar kryptering med standard-PIN-koden som osäker och markerar dessa enheter som inkompatibla tills användaren ställer in en annan PIN-kod.
- En Android-enhet som är registrerad och kompatibel kanske fortfarande blockeras och får ett karantänmeddelande första gången den försöker komma åt företagsresurser. Om detta inträffar kontrollerar du att företagsportalappen inte körs och klickar sedan på länken **Kom igång nu** i karantänmeddelandet för att starta en utvärdering. Detta är endast nödvändigt första gången Villkorsstyrd åtkomst aktiveras.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Enheter blockeras och inget karantänmeddelande tas emot via e-post

- Kontrollera att enheten visas som en Exchange ActiveSync-enhet i Intune-administratörskonsolen. Om inte är det troligt att enhetsidentifieringen misslyckas, förmodligen på grund av ett Exchange Connector-problem. Mer information finns i [Felsöka lokal Intune Exchange-anslutning](troubleshoot-exchange-connector.md).
- Innan Exchange Connector blockerar en enhet skickar tjänsten ett aktiveringsmeddelande (karantänmeddelande) via e-post. Om enheten är offline kanske den inte kan ta emot aktiveringsmeddelandet. 
- Kontrollera om e-postklienten på enheten har konfigurerats att hämta e-post med hjälp av **Push** i stället för **Avsökning**. I så fall kan det leda till att användaren missar e-postmeddelandet. Byt till **Avsökning** och se om enheten får e-postmeddelandet.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Enheter är inkompatibla men användarna blockeras inte

- För Windows-datorer blockerar Villkorsstyrd åtkomst endast den inbyggda e-postappen, Office 2013 med modern autentisering, eller Office 2016. För att blockera tidigare versioner av Outlook eller alla e-postappar på Windows-datorer krävs konfiguration av Enhetsregistrering i AAD och Active Directory Federation Services (AD FS), som beskrivs i [Konfigurera SharePoint Online och Exchange Online för Villkorsstyrd åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication). 
- Om enheten rensas selektivt eller dras tillbaka från Intune kan den fortfarande ha åtkomst flera timmar efter att den dragits tillbaka. Det beror på att Exchange cachelagrar åtkomsträttigheter i 6 timmar. Överväg andra sätt att skydda data på pensionerade enheter i det här scenariot.
- Surface Hub-enheter stöder Villkorsstyrd åtkomst. Dock måste du distribuera efterlevnadsprincipen till enhetsgrupper (inte användargrupper) för korrekt utvärdering.
- Kontrollera tilldelningarna för dina efterlevnadsprinciper och principer för Villkorsstyrd åtkomst. Om en användare inte finns i gruppen som tilldelats principerna, eller i en grupp som undantas, kommer användaren inte att blockeras. Kompatibiliteten kontrolleras endast för enheter som hör till användare i en tilldelad grupp.

## <a name="noncompliant-device-is-not-blocked"></a>Inkompatibel enhet blockeras inte

Om en enhet har åtkomst trots att den är inkompatibel vidtar du följande åtgärder.
- Granska dina mål- och undantagsgrupper. Om användare inte är i rätt målgrupp, eller är i en undantagsgrupp, blockeras de inte. Efterlevnad kontrolleras endast för enheter som har användare i en målgrupp.
- Kontrollera att enheten identifieras. Pekar Exchange Connector på en Exchange 2010-klientåtkomstserver när användaren har en Exchange 2013-servern? I så fall kan Intune inte känna till enhetens anslutning till Exchange om Exchange-standardregeln är Tillåt, även om användaren är i målgruppen.
- Kontrollera om enhetens finns/enhetens åtkomststatus i Exchange:
  - Använd denna PowerShell-cmdlet om du vill hämta en lista över alla mobila enheter för en postlåda: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Om enheten inte visas har den inte åtkomst till Exchange.
  - Om enheten visas använder du cmdleten Get-CASmailbox -identity:’upn’ | fl för att få detaljerad information om enhetens åtkomststatus och ange den informationen till Microsoft Support.

## <a name="next-steps"></a>Nästa steg
Om den här informationen inte är till hjälp kan du även [få support för Microsoft Intune](get-support.md).
