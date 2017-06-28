---
title: "Felsök hantering av mobilprogram"
description: "I det här avsnittet beskrivs några felsökningstips för villkorlig åtkomst till distributioner."
keywords: 
author: oydang
ms.author: oydang
manager: angerobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: dd4b216f04c909321bbf57f4dec5998e48cb490c
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="troubleshoot-mobile-application-management"></a>Felsök hantering av mobilprogram

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Börja här om du har problem med hantering av mobilprogram i Intune. Det här avsnittet innehåller några vanliga problem och frågor som du kan ha och ger lösningar och svar.

Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md), som beskriver hur du kan få hjälp på fler sätt.


## <a name="common-it-administrator-issues"></a>Vanliga problem för IT-administratörer

Dessa är vanliga problem som en IT-administratör kan uppleva med Intune-principen för appskydd.

| Problem | Beskrivning | Lösning |
| -- | -- | -- |
| Principen tillämpas inte på Skype för Business | Appskyddsprincip utan enhetsregistrering som är utförd i Azure Portal tillämpas inte i Skype för företag-appen på iOS- och Android-enheter. | Skype för företag måste konfigureras för modern autentisering.  Följ instruktionerna i [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Aktivera din klient för modern autentisering) för att konfigurera modern autentisering för Skype. |
| Principen för Office-appen tillämpas inte | Appskyddsprinciper tillämpas inte på någon [Office-app som stöds](https://www.microsoft.com/cloud-platform/microsoft-intune-partners) för någon användare. | Kontrollera att användaren är licensierad för Intune och de Office-appar som är avsedda för en distribuerad appskyddsprincip. Det kan ta upp till 8 timmar innan en skyddsprincip för nyligen distribuerade appar tillämpas. |
| Administratören kan inte konfigurera en appskyddsprincip i Azure Portal | IT-administratören kan inte konfigurera appskyddsprinciper i Azure Portal. | Följande användarroller har åtkomst till Azure Portal: <ul><li>Global administratör, som du kan ställa in i [Office-portalen](http://portal.office.com/)</li><li>Ägare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).</li><li>Deltagare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).</li></ul>  Referera till [Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) för hjälp med att ställa in dessa roller.|
|Användarkonton som saknas i principrapporter om appskydd | Administratörens konsolrapporter visar inte användarkonton som en appskyddsprincip nyligen har distribuerats till. | Om en appskyddsprincip nyligen riktats till en användare, kan det ta upp till 24 timmar innan användaren visas i rapporter som en sådan användare. |
| Principändringar fungerar inte | Ändringar och uppdateringar till appskyddsprinciper kan ta upp till åtta timmar innan de börjar gälla. | I vissa fall kan slutanvändaren logga ut från appen och logga in igen för att tvinga fram synkronisering med tjänsten. |
| Appskyddsprincip fungerar inte med DEP | Appskyddsprincipen tillämpas inte på Apple DEP-enheter. | Kontrollera att du använder Användartillhörighet med Apples program för enhetsregistrering (DEP). Användartillhörighet krävs för alla appar som kräver användarautentisering under DEP. <br><br>Referera till [Registrera företagsägda iOS-enheter i Enhetsregistreringsprogrammet](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md) för mer information om DEP-registrering.|
| Dataöverföringsprincip fungerar inte med iOS | Principerna **Tillåt att appen överför data till andra appar** och **Tillåt att appen tar emot data från andra appar** kan inte hantera dataöverföring i iOS. | Se [Hantera dataöverföring mellan iOS-appar med Microsoft Intune](/deploy-use/manage-data-transfer-between-ios-apps-with-microsoft-intune.md). |






## <a name="common-end-user-issues"></a>Vanliga problem för slutanvändare

Vanliga problem för slutanvändare är uppdelade i följande kategorier:

* **Vanliga användningsscenarier**: En slutanvändare kan uppleva de här scenarierna på appar som har en Intune-appskyddsprincip. De är inte faktiska problem, men kan uppfattas som buggar eller fel.

* **Normala dialogrutor vid användning**: Det här är dialogrutor som slutanvändare kan se i appar som har en Intune-appskyddsprincip. Dessa meddelanden och dialogrutor indikerar **inte** ett fel eller en bugg.

* **Felmeddelanden och dialogrutor**: Det här är felmeddelanden och dialogrutor som slutanvändare kan se i appar som har en Intune-appskyddsprincip. De indikerar ofta att en IT-administratör eller en bugg har orsakat ett fel med Intune-appskydd.



### <a name="normal-usage-scenarios"></a>Normala användningsscenarier

Plattform | Scenario | Förklaring |
---| --- | --- |
iOS | Slutanvändaren kan använda iOS resurstillägg för att öppna arbets- eller skoldata i ohanterade appar, även om dataöverföringsprincipen är inställd på **Endast hanterade appar** eller **Inga appar.** Kan inte detta läcka data? | Intunes appskyddsprincip kan inte styra iOS resurstillägg utan att hantera enheten. Därför **krypterar Intune "företagets" data innan den delas utanför appen**. Du kan verifiera detta genom att försöka öppna en "företags"-fil utanför den hanterade appen. Filen ska vara krypterad och inte kunna öppnas utanför den hanterade appen.
Android | Varför **måste slutanvändaren installera företagsportalappen** även om jag använder MAM-appskydd utan att registrera enheter?  | På Android är mycket av appskyddsfunktionaliteten inbyggd i företagsportalappen. **Enhetsregistrering krävs inte, även om företagsportalappen alltid krävs**. För appskydd utan registrering behöver slutanvändaren bara ha företagsportalappen installerad på enheten.

### <a name="normal-usage-dialogs"></a>Normala dialogrutor vid användning

Plattform | Meddelande eller dialogruta | Förklaring |
--- | --- | --- |
iOS, Android | **Logga in**: För att skydda data måste din organisation hantera den här appen. För att utföra den här åtgärden loggar du in med ditt arbets- eller skolkonto. | Slutanvändaren måste logga in med sitt arbets- eller skolkonto för att kunna använda den här appen, som kräver en appskyddsprincip. Användaren måste autentisera sig mot Azure Active Directory för att principen ska tillämpas.
iOS, Android |**Omstart krävs**: Din organisation skyddar nu data i den här appen. Du måste starta om appen för att kunna fortsätta. | Appen har precis fått en Intune-appskyddsprincip och måste startas om för att principen ska tillämpas.
iOS, Android |**Åtgärden tillåts inte**: Din organisation tillåter endast att du öppnar arbets- eller skoldata i den här appen. | IT-administratören har ställt in **Tillåt att appen tar emot data från andra appar** på **Endast hanterade appar**. Slutanvändare kan därför bara överföra data till den här appen från andra appar som har en appskyddsprincip.
iOS, Android |**Åtgärden tillåts inte**: Din organisation tillåter endast att du överför data till andra hanterade appar. | IT-administratören har ställt in **Tillåt att appen överför data till andra appar** på **Endast hanterade appar**. Slutanvändare kan därför bara överföra data från den här appen till andra appar som har en appskyddsprincip.
iOS, Android |**Varning om borttagning**: Din organisation har tagit bort data som hör till den här appen. För att fortsätta måste du starta om appen. | IT-administratören har påbörjat en rensning av appar med Intune-appskydd.
Android | **Företagsportalen krävs**: För att använda ditt arbets- eller skolkonto med den här appen måste du installera Intunes företagsportalapp. Tryck på ”Gå till butik” för att fortsätta. | På Android är mycket av appskyddsfunktionaliteten inbyggd i företagsportalappen. **Enhetsregistrering krävs inte, även om företagsportalappen alltid krävs**. För appskydd utan registrering behöver slutanvändaren bara ha företagsportalappen installerad på enheten.


### <a name="error-messages-and-dialogs-on-ios"></a>Felmeddelanden och dialogrutor i iOS


Felmeddelande eller dialogruta | Orsak | Åtgärder |
-- | --- | --- |
**Appen konfigureras inte**: Den här appen har inte ställts in för att du ska använda den. Kontakta IT-administratören om du behöver hjälp. | Det gick inte att identifiera en obligatorisk appskyddsprincip för appen. |Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Välkommen till Intune Managed Browser**: Den här appen fungerar bäst när den hanteras av Microsoft Intune. Du kan alltid använda appen för att söka på webben och om den hanteras av Microsoft Intune får du åtkomst till ytterligare dataskyddsfunktioner. | Det gick inte att identifiera en obligatorisk appskyddsprincip för Intune Managed Browser-appen. <br><br>Användaren kan fortfarande använda appen för att söka på webben, men appen hanteras inte av Intune. | Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot Intune Managed Browser-appen.
**Inloggningen misslyckades**: Vi kan inte logga in dig just nu. Försök igen senare. | Det gick inte att registrera användaren med MAM-tjänsten när användaren försökte logga in med sitt arbets- eller skolkonto. | Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Kontot är inte konfigurerat**: Din organisation har inte konfigurerat ditt konto så att du har åtkomst till arbets- eller skoldata. Kontakta IT-administratören om du behöver hjälp. | Användarkontot har inte någon licens för Intune A Direct. | Kontrollera att användarkontot har en licens för Intune som tilldelats i [Office-portalen](http://portal.office.com).
**Enheten är inte kompatibel**: Den här appen kan inte användas eftersom du använder en jailbrokad enhet. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt att användaren finns på en jailbrokad enhet. | Återställ enheten till fabriksinställningarna. Följ [anvisningarna](https://support.apple.com/HT201274) från Apples supportwebbplats.
**Internetanslutning krävs**: Du måste vara ansluten till Internet för att kunna verifiera att du får använda den här appen. | Enheten är inte ansluten till Internet. | Anslut enheten till ett WiFi- eller datanätverk.
**Okänt fel**: Försök att starta om den här appen. Om problemet kvarstår kontaktar du IT-administratören för hjälp. | Ett okänt fel uppstod. | Vänta en stund och försök igen. Om felet kvarstår bör du skapa ett supportärende med Intune [här](how-to-get-support-for-microsoft-intune.md).
**Åtkomst till din organisations data**: Arbets- eller skolkontot som du angav har inte åtkomst till den här appen. Du kan behöva logga in med ett annat konto. Kontakta IT-administratören om du behöver hjälp. | Intune identifierar att användaren försökte logga in med ett arbets- eller skolkonto som skiljer sig från det registrerade MAM-kontot för enheten. Endast ett arbets- eller skolkonto kan hanteras av MAM samtidigt per enhet. | Låt användaren logga in med kontot vars användarnamn är ifyllt på inloggningsskärmen. <br> <br> Eller låt användaren logga in med nya arbets- eller skolkontot och ta bort det befintliga kontot som MAM registrerat.
**Anslutningsfel**: Ett oväntat anslutningsproblem inträffade. Kontrollera anslutningen och försök igen.  |  Ett oväntat fel. | Vänta en stund och försök igen. Om felet kvarstår bör du skapa ett supportärende med Intune [här](how-to-get-support-for-microsoft-intune.md).
**Varning**: Den här appen kan inte längre användas. Kontakta IT-administratören för mer information. | Det gick inte att validera appens certifikat. | Kontrollera att appversionen är uppdaterad. <br><br> Installera om appen.
**Fel**: Den här appen har stött på ett problem och måste stängas. Kontakta IT-administratören om problemet kvarstår. | Det gick inte att läsa MAM-appens PIN-kod från Apple iOS-nyckelringen. | Starta om enheten. Kontrollera att appversionen är uppdaterad. <br><br> Installera om appen.


### <a name="error-messages-and-dialogs-on-android"></a>Felmeddelanden och dialogrutor på Android

Dialogruta/felmeddelande | Orsak | Åtgärder |
-- | --- | --- |
**Appen konfigureras inte**: Den här appen har inte ställts in för att du ska använda den. Kontakta IT-administratören om du behöver hjälp. | Det gick inte att identifiera en obligatorisk appskyddsprincip för appen. |Kontrollera att en appskyddsprincip för Android har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Det gick inte att starta appen**: Det uppstod ett problem när din app skulle startas. Försök att uppdatera appen eller Intunes företagsportalapp. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt giltig appskyddsprincip för appen, men appen kraschar under MAM-initieringen. | Kontrollera att appversionen är uppdaterad. <br><br> Kontrollera att företagsportalappen är installerad och uppdaterad på enheten. <br><br> Om felet kvarstår kan du använda företagsportalappen till att skicka loggar till Intune eller skapa ett supportärende [här](how-to-get-support-for-microsoft-intune.md).
**Inga appar hittades**: Din organisation tillåter inte att det här innehållet öppnas av några appar på den här enheten. Kontakta IT-administratören om du behöver hjälp. | Användaren försökte öppna arbets- eller skoldata med en annan app, men Intune kan inte hitta några andra hanterade appar som ska kunna öppna data. | Kontrollera att en appskyddsprincip för Android har distribuerats till användarens säkerhet och att den riktar sig till minst en annan MAM-aktiverad app som kan öppna datan det gäller.
**Inloggningen misslyckades**: Försök att logga in igen. Om problemet kvarstår kontaktar du IT-administratören för hjälp. | Det gick inte att autentisera kontot som användaren försökte logga in på. | Kontrollera att användaren loggar in med arbets- eller skolkontot som redan har registrerats med Intune MAM-tjänsten (det första arbets- eller skolkonto som har loggat in i den här appen). <br><br> Rensa appens data. <br><br> Kontrollera att appversionen är uppdaterad. <br><br> Kontrollera att företagsportalens version är uppdaterad.
**Internetanslutning krävs**: Du måste vara ansluten till Internet för att kunna verifiera att du får använda den här appen. | Enheten är inte ansluten till Internet. | Anslut enheten till ett WiFi- eller datanätverk.
**Enheten är inte kompatibel**: Den här appen kan inte användas eftersom du använder en rotad enhet. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt att användaren finns på en rotad enhet. | Återställ enheten till fabriksinställningarna.
**Kontot är inte konfigurerat**: Appen måste hanteras av Microsoft Intune, men ditt konto har inte konfigurerats. Kontakta IT-administratören om du behöver hjälp. | Användarkontot har inte någon licens för Intune A Direct. | Kontrollera att användarkontot har en licens för Intune som tilldelats i [Office-portalen](http://portal.office.com).
**Det gick inte att registrera appen**: Appen måste hanteras av Microsoft Intune, men det gick inte att registrera den just nu. Kontakta IT-administratören om du behöver hjälp. | Det går inte att automatiskt registrera appen med MAM-tjänsten när appens skyddsprincip krävs. | Rensa appens data. <br><br> Skicka loggar till Intune via företagsportalappen, eller skicka ett supportärende [här](how-to-get-support-for-microsoft-intune.md).




### <a name="see-also"></a>Se även
- [Verifiera din konfiguration för hantering av mobilprogram](../deploy-use/validate-mobile-application-management.md)
- [Förbered dig på att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Så kan du få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md)

