---
title: "Felsök hantering av mobilprogram | Microsoft Docs"
description: "I det här avsnittet beskrivs några felsökningstips för villkorlig åtkomst till distributioner."
keywords: 
author: NathBarn
ms.author: oldang
manager: angerobe
ms.date: 09/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd5a0a3b-0013-4be3-a233-ce6e9083149f
translationtype: Human Translation
ms.sourcegitcommit: d50a5751a5afd987196336e9443dc5a429a283fd
ms.openlocfilehash: b333c0f5097fec38bf0dd78726a028fd7aaccd2f


---

# <a name="troubleshoot-mobile-application-management"></a>Felsök hantering av mobilprogram

Börja här om du har problem med hantering av mobilprogram i Intune. Det här avsnittet innehåller några vanliga problem och frågor som du kan ha och ger lösningar och svar.

## <a name="common-it-administrator-issues"></a>Vanliga problem för IT-administratörer

1. **Problem:** Appens skyddsprincip utan enhetsregistrering som är utförd i Azure-portalen, tillämpas inte i Skype för företag-appen på iOS- och Android-enheter.

  **Lösning**: Skype för företag måste konfigureras för modern autentisering.  Följ instruktionerna i [Enable your tenant for modern authentication](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) (Aktivera din klient för modern autentisering) för att konfigurera modern autentisering för Skype.

2. **Problem:** Appens skyddsprinciper tillämpas inte på någon [Office App som stöds](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners) för någon användare.

  **Lösning**: Kontrollera att användaren är licensierad för Intune och de Office-appar som är avsedda för en distribuerad appskyddsprincip. Det kan ta upp till 8 timmar innan en skyddsprincip för nyligen distribuerade appar tillämpas.

3. **Problem:** IT-administratören kan inte konfigurera appskyddsprinciper i Azure Portal.

  **Lösning**:

  Följande användarroller har åtkomst till Azure Portal:

  - Global administratör, som du kan ställa in i [Office-portalen](http://portal.office.com/)
  - Ägare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).
  - Deltagare, som du kan ställa in i [Azure-portalen](https://portal.azure.com/).<br>

  Referera till [Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md) för hjälp med att ställa in dessa roller.

4. **Problem:** Administratörens konsolrapporter visar inte användarkonton som appens skyddsprincip nyligen har distribuerats till.

  **Lösning**: Om en appskyddsprincip nyligen riktats till en användare, kan det ta upp till 24 timmar innan användaren visas i rapporter som en sådan användare.

5. **Problem:** Principändringar/uppdateringar kan ta upp till 8 timmar innan de börjar gälla.  

  **Lösning**: Slutanvändaren kan logga ut från appen och logga in igen för att tvinga fram synkronisering med tjänsten.  

6. **Problem:** Appskyddsprincipen tillämpas inte på Apple DEP-enheter.

  **Lösning**: Kontrollera att du använder Användartillhörighet med Apples program för enhetsregistrering (DEP). Användartillhörighet krävs för alla appar som kräver användarautentisering under DEP.
Referera till [Registrera företagsägda iOS-enheter i Enhetsregistreringsprogrammet](../deploy-use/ios-device-enrollment-program-in-microsoft-intune.md) för mer information om DEP-registrering.

## <a name="common-end-user-issues"></a>Vanliga problem för slutanvändare

### <a name="issues-on-ios"></a>Problem med iOS

Dialogruta/felmeddelande | Orsak | Åtgärder |
-- | --- | --- |
**Appen konfigureras inte**: Den här appen har inte ställts in för att du ska använda den. Kontakta IT-administratören om du behöver hjälp. | Det gick inte att identifiera en obligatorisk appskyddsprincip för appen. |Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Välkommen till Intune Managed Browser**: Den här appen fungerar bäst när den hanteras av Microsoft Intune. Du kan alltid använda appen för att söka på webben och om den hanteras av Microsoft Intune får du åtkomst till ytterligare dataskyddsfunktioner. | Det gick inte att identifiera en obligatorisk appskyddsprincip för Intune Managed Browser-appen. <br><br>Användaren kan fortfarande använda appen för att söka på webben, men appen hanteras inte av Intune. | Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot Intune Managed Browser-appen.
**Inloggningen misslyckades**: Vi kan inte logga in dig just nu. Försök igen senare. | Det gick inte att registrera användaren med MAM-tjänsten när användaren försökte logga in med sitt arbets- eller skolkonto. | Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Kontot är inte konfigurerat**: Din organisation har inte konfigurerat ditt konto så att du har åtkomst till arbets- eller skoldata. Kontakta IT-administratören om du behöver hjälp. | Användarkontot har inte någon licens för Intune A Direct. | Kontrollera att användarkontot har en licens för Intune som tilldelats i [Office-portalen](http://portal.office.com).
**Enheten är inte kompatibel**: Den här appen kan inte användas eftersom du använder en jailbrokad enhet. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt att användaren finns på en jailbrokad enhet. | Återställ enheten till fabriksinställningarna. Följ [anvisningarna](https://support.apple.com/en-us/HT201274) från Apples supportwebbplats.
**Internetanslutning krävs**: Du måste vara ansluten till Internet för att kunna verifiera att du får använda den här appen. | Enheten är inte ansluten till Internet. | Anslut enheten till ett WiFi- eller datanätverk.
**Okänt fel**: Försök att starta om den här appen. Om problemet kvarstår kontaktar du IT-administratören för hjälp. | Ett okänt fel uppstod. | Vänta en stund och försök igen. Om felet kvarstår bör du skapa ett supportärende med Intune [här](/how-to-get-support-for-microsoft-intune.md).
**Åtkomst till din organisations data**: Arbets- eller skolkontot som du angav har inte åtkomst till den här appen. Du kan behöva logga in med ett annat konto. Kontakta IT-administratören om du behöver hjälp. | Intune identifierar att användaren försökte logga in med ett arbets- eller skolkonto som skiljer sig från det registrerade MAM-kontot för enheten. Endast ett arbets- eller skolkonto kan hanteras av MAM samtidigt per enhet. | Låt användaren logga in med kontot vars användarnamn är ifyllt på inloggningsskärmen. <br> <br> Eller låt användaren logga in med nya arbets- eller skolkontot och ta bort det befintliga kontot som MAM registrerat.
**Anslutningsfel**: Ett oväntat anslutningsproblem inträffade. Kontrollera anslutningen och försök igen.  |  Ett oväntat fel. | Vänta en stund och försök igen. Om felet kvarstår bör du skapa ett supportärende med Intune [här](/how-to-get-support-for-microsoft-intune.md).
**Varning**: Den här appen kan inte längre användas. Kontakta IT-administratören för mer information. | Det gick inte att validera appens certifikat. | Kontrollera att appversionen är uppdaterad. <br><br> Installera om appen.
**Fel**: Den här appen har stött på ett problem och måste stängas. Kontakta IT-administratören om problemet kvarstår. | Det gick inte att läsa MAM-appens PIN-kod från Apple iOS-nyckelringen. | Starta om enheten. Kontrollera att appversionen är uppdaterad. <br><br> Installera om appen.


### <a name="issues-on-android"></a>Problem med Android

Dialogruta/felmeddelande | Orsak | Åtgärder |
-- | --- | --- |
**Appen konfigureras inte**: Den här appen har inte ställts in för att du ska använda den. Kontakta IT-administratören om du behöver hjälp. | Det gick inte att identifiera en obligatorisk appskyddsprincip för appen. |Kontrollera att en appskyddsprincip för iOS har distribuerats till användarens säkerhetsgrupp och att den riktar sig mot den här appen.
**Det gick inte att starta appen**: Det uppstod ett problem när din app skulle startas. Försök att uppdatera appen eller Intunes företagsportalapp. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt giltig appskyddsprincip för appen, men appen kraschar under MAM-initieringen. | Kontrollera att appversionen är uppdaterad. <br><br> Kontrollera att företagsportalappen är installerad och uppdaterad på enheten. <br><br> Om felet kvarstår kan du använda företagsportalappen till att skicka loggar till Intune eller skapa ett supportärende [här](/how-to-get-support-for-microsoft-intune.md).
**Inga appar hittades**: Din organisation tillåter inte att det här innehållet öppnas av några appar på den här enheten. Kontakta IT-administratören om du behöver hjälp. | Användaren försökte öppna arbets- eller skoldata med en annan app, men Intune kan inte hitta några andra hanterade appar som ska kunna öppna data. | Kontrollera att en appskyddsprincip för Android har distribuerats till användarens säkerhet och att den riktar sig till minst en annan MAM-aktiverad app som kan öppna datan det gäller.
**Inloggningen misslyckades**: Försök att logga in igen. Om problemet kvarstår kontaktar du IT-administratören för hjälp. | Det gick inte att autentisera kontot som användaren försökte logga in på. | Kontrollera att användaren loggar in med arbets- eller skolkontot som redan har registrerats med Intune MAM-tjänsten (det första arbets- eller skolkonto som har loggat in i den här appen). <br><br> Rensa appens data. <br><br> Kontrollera att appversionen är uppdaterad. <br><br> Kontrollera att företagsportalens version är uppdaterad.
**Internetanslutning krävs**: Du måste vara ansluten till Internet för att kunna verifiera att du får använda den här appen. | Enheten är inte ansluten till Internet. | Anslut enheten till ett WiFi- eller datanätverk.
**Enheten är inte kompatibel**: Den här appen kan inte användas eftersom du använder en rotad enhet. Kontakta IT-administratören om du behöver hjälp. | Intune har upptäckt att användaren finns på en rotad enhet. | Återställ enheten till fabriksinställningarna.
**Kontot är inte konfigurerat**: Appen måste hanteras av Microsoft Intune, men ditt konto har inte konfigurerats. Kontakta IT-administratören om du behöver hjälp. | Användarkontot har inte någon licens för Intune A Direct. | Kontrollera att användarkontot har en licens för Intune som tilldelats i [Office-portalen](http://portal.office.com).
**Det gick inte att registrera appen**: Appen måste hanteras av Microsoft Intune, men det gick inte att registrera den just nu. Kontakta IT-administratören om du behöver hjälp. | Det går inte att automatiskt registrera appen med MAM-tjänsten när appens skyddsprincip krävs. | Rensa appens data. <br><br> Skicka loggar till Intune via företagsportalappen, eller skicka ett supportärende [här](/how-to-get-support-for-microsoft-intune.md).





### <a name="see-also"></a>Se även
- [Verifiera din konfiguration för hantering av mobilprogram](../deploy-use/validate-mobile-application-management.md)
- [Förbered dig på att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


