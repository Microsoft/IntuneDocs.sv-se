---
title: Självstudier – Använda Apple Business Manager eller programmet för enhetsregistrering för registrering av iOS-enheter i Intune
titleSuffix: Microsoft Intune
description: I de här självstudierna ska du ställa in registreringsfunktioner för Apples företagsenheter från ABM för att registrera iOS-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83a9467065bb5c1d1cde2035df936541bb804ddc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503076"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Självstudie: Använda Apples företagsenhetsregistrering i Apple Business Manager (ABM) för registrering av iOS-enheter i Intune
Funktionerna för registrering av enheter i Apple Business Manager underlättar registrering av enheter. Intune stöder också Apples äldre DEP-portal (Programmet för enhetsregistrering), men vi rekommenderar att du börjar om från början med Apple Business Manager. Med Microsoft Intune och Apples företagsenhetsregistrering registreras enheter automatiskt den första gången som användaren slår på enheten. Du kan därför leverera enheter till många användare utan att behöva konfigurera varje enhet individuellt. 

I den här självstudien får du lära dig att:
> [!div class="checklist"]
> * Hämta token för enhetsregistrering från Apple
> * Synkronisera hanterade enheter med Intune
> * Skapa en registreringsprofil
> * Tilldela enheter en registreringsprofil

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
- Enheter som köpts i [Apple Business Manager](https://business.apple.com) eller [Apples enhetsregistreringsprogram](http://deploy.apple.com)
- Ange [utfärdare för hantering av mobila enheter](../fundamentals/mdm-authority-set.md)
- Hämta ett [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Hämta token för enhetsregistrering från Apple
Innan du registrerar iOS-enheter med Apples företagsägda funktioner behöver du en enhetsregistreringstokenfil från Apple (.pem). Med denna token kan Intune synkronisera information om Apple-enheter som ditt företag äger. Intune kan även överföra registreringsprofiler till Apple och tilldela enheter till dessa profiler.

Du kan använda ABM- eller DEP-portalen för att skapa en token för enhetsregistrering. Du kan också använda portalerna för att tilldela enheter till Intune för hantering.

1. I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > **Lägg till**.

2. Välj **Jag godkänner** för att ge Microsoft behörighet att skicka information om användare och enhet till Apple.

   ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. .pem-filen används för att begära ett förtroendecertifikat från ABM- eller DEP-portalen.

4. Välj **Skapa en token för Apples enhetsregistreringsprogram** för att öppna Apples portal för distributionsprogram och logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.

5. Gå till Apples [portal för driftsättningsprogram](https://deploy.apple.com) och välj **Kom igång** för **Enhetsregistreringsprogram**. Processen kan vara lite annorlunda än följande steg i [Apple Business Manager](https://business.apple.com).

4. På sidan **Hantera servrar** väljer du **Lägg till MDM-server**.

5. Som **MDM-servernamn** anger du *TestMDMServer* och väljer sedan **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

6. Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas med meddelandet **Upload Your Public Key** (Överför din offentliga nyckel). Markera **Välj fil...** för att överföra PEM-filen och välj sedan **Nästa**.

6. Gå till **Distributionsprogram** > **Enhetsregistreringsprogram** > **Hantera enheter**.
7. Under **Choose Devices By** (Välj enheter efter) väljer du **Serial Number** (Serienummer). <!--ask Tiffany about this-->

8. Välj **Assign to Server** (Tilldela till server) för **Välj åtgärd** och välj **servernamnet** som angetts för Microsoft Intune och sedan &lt;OK&gt;. Apples portal tilldelar de angivna enheterna till Intune-servern för hantering och visar sedan meddelandet **Assignment Complete** (Tilldelningen är klar).

   Gå till Apple-portalen och **Driftsättningsprogram** &gt; **Enhetsregistreringsprogram** &gt; **View Assignment History (Visa historik för tilldelning)** för att se en lista över enheter och deras MDM-servertilldelning.

9. I Intune, i Azure Portal anger du för framtida referens det Apple-ID som användes till att skapa denna token.

    ![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. I rutan **Apple-token**, bläddrar du till certifikatfilen (.pem), väljer **Öppna** och väljer sedan **Skapa**. 

11. Om du vill tillämpa omfångstaggar för att begränsa vilka administratörer som har åtkomst till denna token väljer du omfång.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil
Nu när du har installerat din token kan skapa du en registreringsprofil för företagsägda iOS-enheter. En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.

2. Välj den token du precis har installerat och välj **Profiler** > **Skapa profil**.

3. Under **Skapa profil** anger du *TestDEPProfile* i fältet **Namn** och *Testing DEP for iOS devices* (Testar DEP för iOS-enheter) i fältet **Beskrivning**. Användarna kan inte se den här informationen.

4. Välj **iOS** under **Plattform**.

5. Bestäm om du vill att dina enheter som ska registreras med eller utan **användartillhörighet**. Användartillhörighet är utformat för enheter som ska användas av specifika användare. Om användarna vill använda företagsportalen för tjänster som att installera appar väljer du **Registrera med användartillhörighet**. Om användarna inte behöver företagsportalen, eller om du vill erbjuda många användare enheten väljer du **Registrera utan användartillhörighet**.

6. Om du väljer att registrera med användartillhörighet kan du avgöra om du vill autentisera med företagsportalen eller Apples installationsassistent. Om du vill använda Multi-Factor Authentication, låta användarna byta lösenord vid första inloggningen eller uppmana dem att återställa sina utgångna lösenord under registreringen väljer du **Ja** under **Autentisera med Företagsportalen istället för Apple-installationsassistenten**. Om du är nöjd med att använda Apples tillhandahållna grundläggande HTTP-autentisering via Apple-installationsassistenten väljer du **Nej**.

7. Om du väljer att registrera med användartillhörighet och autentisera med företagsportalen kan du avgöra om du vill installera företagsportalen med Apples volymköpsprogram (VPP). Om du installerar företagsportalen med en VPP-token behöver användaren inte ange något Apple-ID och lösenord för att ladda ned företagsportalen från App Store under registreringen. Välj **Använd token:** under **Installera företagsportalen med VPP** för att välja en VPP-token som har tillgängliga kostnadsfria licenser för företagsportalen. Om du inte vill använda VPP för att distribuera företagsportalen väljer du **Don't use VPP** (Använd inte DPP) under **Installera företagsportalen med VPP**. 

8. Om du väljer att registrera med användartillhörighet, autentisera med företagsportalen och installera företagsportalen med VPP kan du välja om du vill köra företagsportalen i enkelt appläge till autentiseringen. Med den här inställningen kan du se till att användaren inte har åtkomst till andra appar förrän företagets registrering är klar. Om du vill förhindra att användaren begränsas till det här flödet tills registreringen är klar väljer du **Ja** under **Kör företagsportalen i enkelt appläge tills autentisering**. 

9. Välj **Inställningar för enhetshantering** och välj **Ja** under **Kontrollerad**. Med övervakade enheter får du flest hanteringsalternativ för företagets iOS-enheter.

10. Välj **Ja** under **Låst registrering** för att se till att användarna inte kan ta bort hantering av företagets enheter. 

11. Välj ett alternativ under **Synkronisera med datorer** för att avgöra om iOS-enheter ska kunna synkroniseras med datorer.

12. Som standard namnger Apple enheten efter typ av enhet (t.ex. iPad). Om du vill ange en annan namnmall väljer du **Ja** under **Använd mall för enhetsnamn**. Ange namnet som du vill tillämpa på enheterna, där strängarna *{{SERIAL}}* och *{{DEVICETYPE}}* kommer att ersätta varje enhets serienummer och typ av enhet. Annars väljer du **Nej** under **Använd mall för enhetsnamn**.

13. Välj **OK**.

14. Välj **Anpassa inställningsassistenten** och ange *Tutorial department* (Självstudieavdelning) i **Avdelningsnamn**. Den här strängen är det som användarna ser när de trycker på **Om konfigurationen** under enhetsaktiveringen.

15. Ange ett telefonnummer under **Avdelningens telefonnummer**. Det här numret visas när användarna trycker på knappen **Behöver hjälp** vid aktiveringen.

16. Du kan **visa** eller **dölja** olika sidor vid enhetsaktiveringen. För att få en så smidig registrering som möjligt ska du ställa in alla skärmar på **Dölj**.

17. Välj **OK** > **Skapa**.

## <a name="sync-managed-devices-to-intune"></a>Synkronisera hanterade enheter med Intune

När du ställer in en registreringsprogramtoken med ABM-, ASM- eller DEP-portalen och tilldelar enheter där till MDM-servern kan du vänta på att enheterna ska synkroniseras till Intune-tjänsten eller push-överföra en synkronisering manuellt. Utan manuell synkronisering kan det ta upp till 24 timmar innan enheterna visas i Azure-portalen.

1. I Intune i Microsoft Azure Portal väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan > **Enheter** > **Synkronisera**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Tilldela iOS-enheterna en registreringsprofil

Du måste tilldela en registreringsprogramprofil till enheterna innan de kan registreras. Enheterna synkroniseras till Intune från Apple och måste tilldelas rätt MDM-servertoken i ABM-, ASM- eller DEP-portalen.

1. I Intune i Microsoft Azure-portalen, väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj din token i listan.
2. Välj **Enheter** > välj enheter i listan > **Tilldela profil**.
3. Välj en profil för enheterna under **Tilldela profil** och välj sedan **Tilldela**.

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Du har konfigurerat hantering och synkronisering mellan Apple och Intune, och har tilldelat en profil så att DEP-enheterna kan registreras. Du kan nu distribuera enheter till användare. Enheter med användartillhörighet kräver att varje användare tilldelas en Intune-licens.

## <a name="next-steps"></a>Nästa steg

Det finns mer information om andra alternativ som är tillgängliga för registrering av iOS-enheter.

> [!div class="nextstepaction"]
> [Fördjupande artikel om iOS DEP-registrering](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
