---
title: Självstudier – Använda programmet för enhetsregistrering för registrering av iOS-enheter i Intune
titleSuffix: Microsoft Intune
description: I den här självstudiekursen får du konfigurera Apples DEP att registrera iOS-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9cd0eec492f5131e4015aa64eccb4c081c663ee
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61515677"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>Självstudie: Använda programmet för enhetsregistrering för registrering av iOS-enheter i Intune
Apples program för enhetsregistrering (DEP) förenklar registreringen av enheter. Med Microsoft Intune och DEP registreras enheter automatiskt första gången som användaren slår på enheten. Du kan därför leverera enheter till många användare utan att behöva konfigurera varje enhet individuellt. 

I den här självstudien får du lära dig att:
> [!div class="checklist"]
> * Hämta en Apple DEP-token
> * Skapa en Autopilot-enhetsgrupp
> * Skapa en Autopilot-distributionsprofil
> * Tilldela Autopilot-distributionsprofilen till enhetsgruppen
> * Distribuera Windows-enheter till användare

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
- Enheter som köpts i [Apples enhetsregistreringsprogram](http://deploy.apple.com)
- Ange [utfärdare för hantering av mobila enheter](mdm-authority-set.md)
- Hämta ett [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Hämta en Apple DEP-token
Innan du registrerar iOS-enheter med DEP behöver du en Apple DEP-tokenfil (.pem). Med denna token kan Intune synkronisera information om DEP-enheter som ditt företag äger. Intune kan även överföra registreringsprofiler till Apple och tilldela enheter till dessa profiler.

Du kan använda Apples DEP-portal för att skapa en DEP-token. Du kan också använda DEP-portalen för att tilldela enheter till Intune för hantering.

1. I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > **Lägg till**.

2. Välj **Jag godkänner** för att ge Microsoft behörighet att skicka information om användare och enhet till Apple.

   ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

4. Välj **Skapa en token för Apples enhetsregistreringsprogram** för att öppna Apples portal för distributionsprogram och logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.

5.  Gå till Apples [portal för driftsättningsprogram](https://deploy.apple.com) och välj **Kom igång** för **Enhetsregistreringsprogram**.

4. På sidan **Hantera servrar** väljer du **Lägg till MDM-server**.

5. Som **MDM-servernamn** anger du *TestMDMServer* och väljer sedan **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

6. Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas med meddelandet **Upload Your Public Key** (Överför din offentliga nyckel). Markera **Välj fil...** för att överföra PEM-filen och välj sedan **Nästa**.

6. Gå till **Distributionsprogram** > **Enhetsregistreringsprogram** > **Hantera enheter**.
7. Under **Choose Devices By** (Välj enheter efter) väljer du **Serial Number** (Serienummer). <!--ask Tiffany about this-->

8. Välj **Assign to Server** (Tilldela till server) för **Välj åtgärd** och välj **servernamnet** som angetts för Microsoft Intune och sedan &lt;OK&gt;. Apples portal tilldelar de angivna enheterna till Intune-servern för hantering och visar sedan meddelandet **Assignment Complete** (Tilldelningen är klar).

   Gå till Apple-portalen och **Driftsättningsprogram** &gt; **Enhetsregistreringsprogram** &gt; **View Assignment History (Visa historik för tilldelning)** för att se en lista över enheter och deras MDM-servertilldelning.

9. I Intune, i Azure Portal anger du för framtida referens det Apple-ID som användes till att skapa denna token.

    ![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/device-enrollment-program-enroll-ios/image03.png)

10. I rutan **Apple-token**, bläddrar du till certifikatfilen (.pem), väljer **Öppna** och väljer sedan **Skapa**. 

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil
Nu när du har installerat din token kan skapa du en registreringsprofil för DEP-enheter. En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.

2. Välj den token du precis har installerat och välj **Profiler** > **Skapa profil**.

3. Under **Skapa profil** anger du *TestDEPProfile* i fältet **Namn** och *Testing DEP for iOS devices* (Testar DEP för iOS-enheter) i fältet **Beskrivning**. Användarna kan inte se den här informationen.

4. I **Användartillhörighet** väljer du **Registrera med användartillhörighet**. Det här alternativet är för enheter som tillhör användare som vill använda Företagsportal för tjänster som installation av appar.

5. Välj **Nej** under **Autentisera med företagsportalen istället för Apple-installationsassistenten**.

6. Välj **Inställningar för enhetshantering** och välj **Nej** under **Kontrollerad**. Kontrollerade enheter ger dig fler hanteringsalternativ men du använder det inte för i här självstudiekursen.

7. Välj **OK**.

8. Välj **Anpassa inställningsassistenten** och ange *Tutorial department* (Självstudieavdelning) i **Avdelningsnamn**. Den här strängen är det som användarna ser när de trycker på **Om konfigurationen** under enhetsaktiveringen.

9. Ange ett telefonnummer under **Avdelningens telefonnummer**. Det här numret visas när användarna trycker på knappen **Behöver hjälp** vid aktiveringen.

10. Du kan **visa** eller **dölja** olika sidor vid enhetsaktiveringen. För den här självstudiekursen ställer du in **Lösenord** på **Visa** och alla andra på **Dölj**.

11. Välj **OK** > **Skapa**.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter

Nu kan du se vilka enheter som har tilldelats till denna token.

1. I Intune i Microsoft Azure Portal väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj en token i listan > **Enheter** > **Synkronisera**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Tilldela iOS-enheterna en registreringsprofil

Du måste tilldela en registreringsprogramprofil till enheterna innan de kan registreras.

1. I Intune i Microsoft Azure-portalen, väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramtokens** > välj din token i listan.
2. Välj **Enheter** > välj enheter i listan > **Tilldela profil**.
3. Välj en profil för enheterna under **Tilldela profil** och välj sedan **Tilldela**.

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Du har konfigurerat hantering och synkronisering mellan Apple och Intune, och har tilldelat en profil så att DEP-enheterna kan registreras. Du kan nu distribuera enheter till användare. Enheter med användartillhörighet kräver att varje användare tilldelas en Intune-licens.

## <a name="clean-up-resources"></a>Rensa resurser

Om du inte vill använda Autopilot-enheter mer kan du ta bort dem.

- Om enheterna har registrerats i Intune måste du först [ta bort dem från Azure Active Directory-portalen](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>Nästa steg

Det finns mer information om andra alternativ som är tillgängliga för registrering av iOS-enheter.

> [!div class="nextstepaction"]
> [Fördjupande artikel om iOS DEP-registrering](device-enrollment-program-enroll-ios.md)
