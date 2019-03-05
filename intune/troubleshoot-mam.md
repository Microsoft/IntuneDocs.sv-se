---
title: Felsök hantering av mobilprogram
titlesuffix: Microsoft Intune
description: I det här avsnittet beskrivs några felsökningstips för villkorlig åtkomst till distributioner.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c94fc26543123f0b3cf6a0f08f8089c48d78778b
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232207"
---
# <a name="troubleshoot-mobile-application-management"></a>Felsök hantering av mobilprogram

I det här avsnittet finns lösningar på vanliga problem som kan inträffa när du använder Intunes hantering av mobilprogram.

Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](get-support.md), som beskriver hur du kan få hjälp på fler sätt.

## <a name="common-it-administrator-issues"></a>Vanliga problem för IT-administratörer

Detta är vanliga problem som IT-administratörer kan uppleva när Intune-principerna för appskydd används.

| Problem | Beskrivning | Lösning |
| -- | -- | -- |
| Principen tillämpas inte på Skype för Business | Appskyddsprincip utan enhetsregistrering som är utförd i Azure Portal tillämpas inte i Skype för företag-appen på iOS- och Android-enheter. | Skype för företag måste konfigureras för modern autentisering.  Följ instruktionerna i [Enable your tenant for modern authentication](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Aktivera din klient för modern autentisering) för att konfigurera modern autentisering för Skype. |
| Principen för Office-appen tillämpas inte | Appskyddsprinciper tillämpas inte på någon [Office-app som stöds](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) för någon användare. | Kontrollera att användaren är licensierad för Intune och de Office-appar som är avsedda för en distribuerad appskyddsprincip. Det kan ta upp till 8 timmar innan en skyddsprincip för nyligen distribuerade appar tillämpas. |
| Administratören kan inte konfigurera en appskyddsprincip i Azure Portal | IT-administratören kan inte konfigurera appskyddsprinciper i Azure Portal. | Följande användarroller har åtkomst till Azure Portal: <ul><li>Global administratör, som du kan ställa in i [Office-portalen](https://portal.office.com/)</li><li>Ägare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).</li><li>Deltagare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).</li></ul> Se [Rollbaserad administrationskontroll (RBAC) med Microsoft Intune](role-based-access-control.md) för hjälp med att konfigurera dessa roller.|
|Användarkonton som saknas i principrapporter om appskydd | Administratörens konsolrapporter visar inte användarkonton som en appskyddsprincip nyligen har distribuerats till. | Om en appskyddsprincip nyligen riktats till en användare, kan det ta upp till 24 timmar innan användaren visas i rapporter som en sådan användare. |
| Principändringar fungerar inte | Ändringar och uppdateringar till appskyddsprinciper kan ta upp till åtta timmar innan de börjar gälla. | I vissa fall kan slutanvändaren logga ut från appen och logga in igen för att tvinga fram synkronisering med tjänsten. |
| Appskyddsprincip fungerar inte med DEP | Appskyddsprincipen tillämpas inte på Apple DEP-enheter. | Kontrollera att du använder Användartillhörighet med Apples program för enhetsregistrering (DEP). Användartillhörighet krävs för alla appar som kräver användarautentisering under DEP. <br><br>Se [Registrera iOS-enheter automatiskt med Apples program för enhetsregistrering](device-enrollment-program-enroll-ios.md) för mer information om iOS DEP-registrering.|
| Dataöverföringsprincip fungerar inte med iOS | Principerna **Tillåt att appen överför data till andra appar** och **Tillåt att appen tar emot data från andra appar** kan inte hantera dataöverföring i iOS. | Se [Hantera dataöverföring mellan iOS-appar i Microsoft Intune](data-transfer-between-apps-manage-ios.md). |

## <a name="common-end-user-issues"></a>Vanliga problem för slutanvändare

Vanliga problem för slutanvändare är uppdelade i följande kategorier:

* **Vanliga användningsscenarier**: En slutanvändare kan uppleva de här scenarierna i appar som innehåller en Intune-appskyddsprincip. De är inte faktiska problem, men kan uppfattas som buggar eller fel.

* **Normala dialogrutor vid användning**: Det här är dialogrutor som slutanvändarna kan se i appar som innehåller en Intune-appskyddsprincip. Dessa meddelanden och dialogrutor indikerar **inte** ett fel eller en bugg.

* **Felmeddelanden och dialogrutor**: Det här är felmeddelanden och dialogrutor som slutanvändarna kan se i appar som innehåller en Intune-appskyddsprincip. De indikerar ofta att en IT-administratör eller en bugg har orsakat ett fel med Intune-appskydd.

### <a name="normal-usage-scenarios"></a>Normala användningsscenarier

Plattform | Scenario | Förklaring |
---| --- | --- |
iOS | Slutanvändaren kan använda iOS resurstillägg för att öppna arbets- eller skoldata i ohanterade appar, även om dataöverföringsprincipen är inställd på **Endast hanterade appar** eller **Inga appar.** Kan inte detta läcka data? | Intunes appskyddsprincip kan inte styra iOS resurstillägg utan att hantera enheten. Därför **krypterar Intune "företagets" data innan den delas utanför appen**. Du kan verifiera detta genom att försöka öppna en "företags"-fil utanför den hanterade appen. Filen ska vara krypterad och inte kunna öppnas utanför den hanterade appen.
Android | Varför **måste slutanvändaren installera företagsportalappen** även om jag använder MAM-appskydd utan att registrera enheter?  | På Android är mycket av appskyddsfunktionaliteten inbyggd i företagsportalappen. **Enhetsregistrering krävs inte, även om företagsportalappen alltid krävs**. För appskydd utan registrering behöver slutanvändaren bara ha företagsportalappen installerad på enheten.

### <a name="normal-usage-dialogs"></a>Normala dialogrutor vid användning

Plattform | Meddelande eller dialogruta | Förklaring |
--- | --- | --- |
iOS, Android | **Logga in**: Din organisation måste hantera den här appen för att kunna skydda sina data. För att utföra den här åtgärden loggar du in med ditt arbets- eller skolkonto. | Slutanvändaren måste logga in med sitt arbets- eller skolkonto för att kunna använda appen som kräver en appskyddsprincip. Användaren måste autentisera sig mot Azure Active Directory för att principen ska kunna tillämpas.
iOS, Android |**Omstart krävs**: Din organisation skyddar nu sina data i den här appen. Du måste starta om appen för att kunna fortsätta. | Appen har nyss fått en Intune-appskyddsprincip och måste startas om för att principen ska kunna tillämpas.
iOS, Android |**Åtgärden tillåts inte**: Din organisation tillåter endast att du öppnar arbets- eller skoldata i den här appen. | IT-administratören har ställt in **Tillåt att appen tar emot data från andra appar** på **Endast hanterade appar**. Slutanvändarna kan därför bara överföra data till den här appen från andra appar som har en appskyddsprincip.
iOS, Android |**Åtgärden tillåts inte**: Din organisation tillåter endast att du överför data till andra hanterade appar. | IT-administratören har ställt in **Tillåt att appen överför data till andra appar** på **Endast hanterade appar**. Slutanvändarna kan därför bara överföra data från den här appen till andra appar som har en appskyddsprincip.
iOS, Android |**Varning om borttagning**: Din organisation har tagit bort de data som hör till den här appen. För att fortsätta måste du starta om appen. | IT-administratören har påbörjat en rensning av appar med Intune-appskydd.
Android | **Företagsportalen krävs**: För att använda ditt arbets- eller skolkonto med den här appen måste du installera Intunes företagsportalapp. Klicka på ”Gå till butik” för att fortsätta. | På Android är mycket av appskyddsfunktionaliteten inbyggd i företagsportalappen. **Enhetsregistrering krävs inte, även om företagsportalappen alltid krävs**. För appskydd utan registrering behöver slutanvändaren bara ha företagsportalappen installerad på enheten.

### <a name="error-messages-and-dialogs-on-ios"></a>Felmeddelanden och dialogrutor i iOS

Felmeddelande eller dialogruta | Orsak | Åtgärder |
-- | --- | --- |
**Appen har inte konfigurerats**: Den här appen har inte konfigurerats för att du ska kunna använda den. Kontakta IT-administratören om du behöver hjälp. | Det gick inte att identifiera en obligatorisk appskyddsprincip för appen. |Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Välkommen till Intune Managed Browser**: Den här appen fungerar bäst när den hanteras av Microsoft Intune. Du kan alltid använda appen för att söka på webben och om den hanteras av Microsoft Intune får du åtkomst till ytterligare dataskyddsfunktioner. | Det gick inte att identifiera en obligatorisk appskyddsprincip för Intune Managed Browser-appen. <br><br>Användaren kan fortfarande använda appen för att söka på webben, men appen hanteras inte av Intune. | Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot Intune Managed Browser-appen.
**Inloggningen misslyckades**: Vi kan inte logga in dig just nu. Försök igen senare. | Det gick inte att registrera användaren med MAM-tjänsten när användaren försökte logga in med sitt arbets- eller skolkonto. | Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Kontot har inte konfigurerats**: Din organisation har inte konfigurerat ditt konto så att du har åtkomst till arbets- eller skoldata. Kontakta IT-administratören om du behöver hjälp. | Användarkontot har inte någon licens för Intune A Direct. | Kontrollera att användarkontot har en licens för Intune som tilldelats i [Office-portalen](https://portal.office.com).
**Enheten är inte kompatibel**: Den här appen kan inte användas eftersom du använder en jailbrokad enhet. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt att användaren finns på en jailbrokad enhet. | Återställ enheten till fabriksinställningarna. Följ [anvisningarna](https://support.apple.com/HT201274) från Apples supportwebbplats.
**Internetanslutning krävs**: Du måste vara ansluten till Internet för att kunna verifiera att du får använda den här appen. | Enheten är inte ansluten till Internet. | Anslut enheten till ett WiFi- eller datanätverk.
**Okänt fel**: Försök att starta om appen. Om problemet kvarstår kontaktar du IT-administratören för hjälp. | Ett okänt fel uppstod. | Vänta en stund och försök igen. Om felet kvarstår bör du skapa en [supportbegäran](get-support.md#create-an-online-support-ticket) med Intune.
**Försöker få åtkomst till organisationens data**: Arbets- eller skolkontot som du angav har inte åtkomst till den här appen. Du kan behöva logga in med ett annat konto. Kontakta IT-administratören om du behöver hjälp. | Intune identifierar att användaren försökte logga in med ett arbets- eller skolkonto som skiljer sig från det registrerade MAM-kontot för enheten. Endast ett arbets- eller skolkonto kan hanteras av MAM samtidigt per enhet. | Låt användaren logga in med kontot vars användarnamn är ifyllt på inloggningsskärmen. <br> <br> Eller låt användaren logga in med nya arbets- eller skolkontot och ta bort det befintliga kontot som MAM registrerat.
**Problem med anslutning**: Ett oväntat anslutningsproblem inträffade. Kontrollera anslutningen och försök igen.  |  Ett oväntat fel. | Vänta en stund och försök igen. Om felet kvarstår bör du skapa en [supportbegäran](get-support.md#create-an-online-support-ticket) med Intune.
**Varning**: Den här appen kan inte längre användas. Kontakta IT-administratören för mer information. | Det gick inte att validera appens certifikat. | Kontrollera att appversionen är uppdaterad. <br><br> Installera om appen.
**Fel**: Appen har stött på ett problem och måste stängas. Kontakta IT-administratören om problemet kvarstår. | Det gick inte att läsa MAM-appens PIN-kod från Apple iOS-nyckelringen. | Starta om enheten. Kontrollera att appversionen är uppdaterad. <br><br> Installera om appen.

### <a name="error-messages-and-dialogs-on-android"></a>Felmeddelanden och dialogrutor på Android

Dialogruta/felmeddelande | Orsak | Åtgärder |
-- | --- | --- |
**Appen har inte konfigurerats**: Appen har inte konfigurerats för att du ska kunna använda den. Kontakta IT-administratören om du behöver hjälp. | Det gick inte att identifiera en obligatorisk appskyddsprincip för appen. |Kontrollera att en appskyddsprincip för Android har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Det gick inte att starta appen**: Det uppstod ett problem när din app skulle startas. Försök att uppdatera appen eller Intunes företagsportalapp. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt giltig appskyddsprincip för appen, men appen kraschar under MAM-initieringen. | Kontrollera att appversionen är uppdaterad. <br><br> Kontrollera att företagsportalappen är installerad och uppdaterad på enheten. <br><br> Om felet kvarstår kan du använda företagsportalappen och skicka loggar till Intune, eller skapa en [supportbegäran](get-support.md#create-an-online-support-ticket).
**Inga appar hittades**: Din organisation tillåter inte att det här innehållet öppnas av några appar på den här enheten. Kontakta IT-administratören om du behöver hjälp. | Användaren försökte öppna arbets- eller skoldata med en annan app, men Intune kan inte hitta några andra hanterade appar som ska kunna öppna data. | Kontrollera att en appskyddsprincip för Android har distribuerats till användarens säkerhet och att den riktar sig till minst en annan MAM-aktiverad app som kan öppna datan det gäller.
**Inloggningen misslyckades**: Försök att logga in igen. Om problemet kvarstår kontaktar du IT-administratören för hjälp. | Det gick inte att autentisera kontot som användaren försökte logga in på. | Kontrollera att användaren loggar in med arbets- eller skolkontot som redan har registrerats med Intune MAM-tjänsten (det första arbets- eller skolkonto som har loggat in i den här appen). <br><br> Rensa appens data. <br><br> Kontrollera att appversionen är uppdaterad. <br><br> Kontrollera att företagsportalens version är uppdaterad.
**Internetanslutning krävs**: Du måste vara ansluten till Internet för att kunna verifiera att du får använda den här appen. | Enheten är inte ansluten till Internet. | Anslut enheten till ett WiFi- eller datanätverk.
**Enheten är inte kompatibel**: Den här appen kan inte användas eftersom du använder en rotad enhet. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt att användaren finns på en rotad enhet. | Återställ enheten till fabriksinställningarna.
**Kontot har inte konfigurerats**: Appen måste hanteras av Microsoft Intune, men ditt konto har inte konfigurerats. Kontakta IT-administratören om du behöver hjälp. | Användarkontot har inte någon licens för Intune A Direct. | Kontrollera att användarkontot har en licens för Intune som tilldelats i [Office-portalen](https://portal.office.com).
**Det gick inte att registrera appen**: Appen måste hanteras av Microsoft Intune, men det gick inte att registrera den just nu. Kontakta IT-administratören om du behöver hjälp. | Det går inte att automatiskt registrera appen med MAM-tjänsten när appens skyddsprincip krävs. | Rensa appens data. <br><br> Skicka loggar till Intune via företagsportalappen, eller skicka en supportbegäran. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).

## <a name="next-steps"></a>Nästa steg

- [Verifiera din konfiguration för hantering av mobilprogram](app-protection-policies-validate.md)
- Ytterligare information om felsökning av Intune information finns i [Använd felsökningsportalen för att hjälpa företagets användare](help-desk-operators.md). 
- Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kända problem i Microsoft Intune](known-issues.md).
- Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).
