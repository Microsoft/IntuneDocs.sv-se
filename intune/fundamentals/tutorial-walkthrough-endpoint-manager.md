---
title: Självstudie – Genomgång av Intune i Microsoft Endpoint Manager
titleSuffix: Microsoft Intune
description: I den här självstudien får du en genomgång av Microsoft Intune i Microsoft Endpoint Managers administrationscenter så att du får mer kunskaper om hur du utför uppgifter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune from the Microsoft Endpoint Manager admin center.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d8950e57c2427c522d337807d315ed5c399c0d5
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514089"
---
# <a name="tutorial-walkthrough-intune-in-microsoft-endpoint-manager"></a>Självstudie: Genomgång av Intune i Microsoft Endpoint Manager

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) innehåller över 100 tjänster som hjälper dig med olika scenarier och möjligheter i molnet. Microsoft Intune är en av flera tjänster som finns i Azure. Med Intune kan du se till att företagets enheter, appar och data uppfyller företagets säkerhetskrav. Du har kontrollen och kan ange vilka krav som måste kontrolleras och vad som händer när de kraven inte uppfylls. I [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) hittar du Microsoft Intune-tjänsten, samt andra inställningar för enhetshantering. Att förstå funktionerna som finns i Intune hjälper dig att utföra uppgifter för hantering av mobilenheter (MDM) och hantering av mobilprogram (MAM).

> [!NOTE]
> Microsoft Endpoint Manager är en enkel, integrerad plattform för slutpunktshantering som hanterar alla dina slutpunkter. I det här administrationscentret för Microsoft Endpoint Manager integreras ConfigMgr och Microsoft Intune.

I de här självstudierna får du:
> [!div class="checklist"]
> * Rundtur i administrationscentret för Microsoft Endpoint Manager
> * Anpassa visningen av administrationscentret för Microsoft Endpoint Manager

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
Innan du konfigurerar Microsoft Intune, bör du granska följande krav:

- [Operativsystem och webbläsare som stöds](../supported-devices-browsers.md) 
- [Krav för nätverkskonfiguration och bandbredd](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune

Du kan prova Intune utan kostnad i 30 dagar. Om du redan har ett arbets- eller skolkonto **loggar du in** med det kontot och lägger till Intune i din prenumeration. Annars kan du [registrera dig](free-trial-sign-up.md) för ett kostnadsfritt utvärderingskonto så att du kan använda Intune i din organisation.

> [!IMPORTANT]
> Du kan inte kombinera ett befintligt arbets- eller skolkonto efter att du har registrerat dig för ett nytt konto.

## <a name="tour-microsoft-intune-in-the-microsoft-endpoint-manager-admin-center"></a>Rundtur i Microsoft Intune i administrationscentret för Microsoft Endpoint Manager

Följ stegen nedan för att bättre förstå Intune i administrationscentret för Microsoft Endpoint Manager. När du har slutfört genomgången har du bättre kunskaper om några av huvudområdena i Intune.

1. Öppna en webbläsare och logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Använd din kostnadsfria utvärderingsprenumeration om Intune är nytt för dig.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Startsida](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-01.png)

    När du öppnar Microsoft Endpoint Manager eller någon annan tjänst i Azure visas tjänsten i ett fönster. Några av de första arbetsbelastningarna som du kanske använder i Intune är **Enheter**, **Appar**, **Användare** och **Grupper**. En arbetsbelastning är helt enkelt ett delområde av en tjänst. När du markerar en arbetsbelastning öppnas fönstret på hela sidan. Andra fönster skjuts ut från höger i fönstret när de öppnas och stängs och visar det föregående fönstret. 

    När du öppnar Microsoft Endpoint Manager visas som standard fönstret **Startsida**. I det här fönstret får du en snabb överblick över klientorganisations- och efterlevnadsstatus, samt andra användbara länkar.

2. I navigeringsfönstret väljer du **Instrumentpanel** för att se allmän information om enheterna och klientapparna i din Intune-klientorganisation. Om du börjar med en ny Intune-klient har du inga registrerade enheter än. 

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Instrumentpanel](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-02.png)
    
    Med Intune kan du hantera personalens enheter och appar, till exempel hur de kommer åt företagsdata. Enheterna måste först registreras i Intune innan du kan använda MDM-tjänsten. När en enhet registreras utfärdas ett MDM-certifikat till den. Certifikatet används för att kommunicera med Intune-tjänsten. 

    Det finns flera olika metoder för att registrera personalens enheter i Intune. Varje metod påverkas av ägarskapet för enheten (personlig eller företagsägd), enhetstypen (iOS/iPadOS, Windows, Android) och hanteringskraven (återställning, tillhörighet, låsning). Men innan du kan aktivera enhetsregistrering måste du konfigurera Intune-infrastrukturen. I synnerhet kräver registrering av enheter att du [anger en MDM-utfärdare](mdm-authority-set.md). Mer information om hur du förbereder Intune-miljön (klienten) finns i [Konfigurera Intune](setup-steps.md). När Intune-klienten är klar kan du registrera enheter. Mer information om enhetsregistrering finns i [Vad är enhetsregistrering?](../enrollment/device-enrollment.md)

3. I navigeringsfönstret väljer du **Enheter** för att se information om de registrerade enheterna i din Intune-klientorganisation. 

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Enheter**.

    I fönstret **Enheter – Översikt** finns flera flikar där du kan se en sammanfattning av följande status och aviseringar:
    - **Registreringsstatus** – Granska information om Intune-registrerade enheter per plattforms- och registreringsfel.
    - **Registreringsaviseringar** – Hitta mer information om ej tilldelade enheter per plattform. 
    - **Efterlevnadsstatus** – Granska efterlevnadsstatusen baserat på enhet, princip, inställning, hot och skydd. Dessutom innehåller fönstret en lista med enheter som saknar en efterlevnadsprincip.
    - **Konfigurationsstatus** – Granska konfigurationsstatusen för enhetsprofiler, samt profildistribution och 
    - **Uppdateringsstatus för programvara** – Se en bild över distributionsstatusen för alla enheter och alla användare.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Enheter](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-03.png)

4. I fönstret **Enheter – Översikt** väljer du **Efterlevnadsprinciper** för att se informationen om efterlevnad för enheter som hanteras av Intune. Information visas som ser ut ungefär som i följande bild.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Efterlevnadsprinciper](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-04.png)
    
    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Enhetsefterlevnad**.

    Ett efterlevnadskrav är i princip samma sak som en regel, t. ex. att kräva en PIN-kod för en enhet eller att kräva enhetskryptering. Efterlevnadsprinciper definierar de regler och inställningar som en enhet måste följa för att anses vara kompatibel. Om du vill använda enhetsefterlevnad måste du ha:
    - en prenumeration på Intune och Azure Active Directory (Azure AD) Premium
    - enheter med en plattform som stöds
    - enheter som har registrerats i Intune
    - enheter som har registrerats på en användare eller ingen primär användare.
    
    Mer information finns i [Komma igång med efterlevnadsprinciper för enheter i Intune](../protect/device-compliance-get-started.md).

5. I fönstret **Enheter – Översikt** väljer du **Villkorsstyrd åtkomst** för att se informationen om åtkomstprinciper.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Villkorsstyrd åtkomst](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-05.png)

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Villkorsstyrd åtkomst**.

    Villkorlig åtkomst syftar på de olika sätt på vilka du kan styra de enheter och appar som tillåts ansluta till dina e-post- och företagsresurser. Mer information om enhetsbaserad och appbaserad villkorlig åtkomst och vanliga scenerier för användning av villkorlig åtkomst med Intune finns i [Vad är villkorlig åtkomst?](../protect/conditional-access.md)

6. I navigeringsfönstret väljer du **Enheter** > **Konfigurationsprofiler** för att se informationen om enhetsprofiler i Intune.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Konfigurationsprofiler](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-06.png)
    
    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Enhetskonfiguration**.

    Intune innehåller inställningar och funktioner som du kan aktivera eller inaktivera på olika enheter i din organisation. Dessa inställningar och funktioner läggs till i ”konfigurationsprofiler”. Du kan skapa profiler för olika enheter och plattformar, bland annat iOS/iPadOS, Android, macOS och Windows. Du kan sedan använda Intune för att tillämpa profilen i din organisation.   

    Mer information om enhetskonfiguration finns i [Tillämpa inställningar för funktioner på dina enheter med enhetsprofiler i Microsoft Intune](../configuration/device-profiles.md).

7. I navigeringsfönstret väljer du **Enheter** > **Alla enheter** för att se informationen om de registrerade enheterna i din Intune-klientorganisation. Om du börjar med en ny Intune-registrering har du inga registrerade enheter än.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Alla enheter](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-07.png)

    I den här listan med enheter finns viktig information om kompatibilitet, OS-version och senaste incheckningsdatum.

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Enheter** > **Alla enheter**.
 
8. I navigeringsfönstret väljer du **Appar** för att se en översikt över appens status. Det här fönstret innehåller installationsstatus för appen baserat på följande flikar:

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Klientappar**.

    I fönstret **Appar – Översikt** finns två flikar där du kan se en sammanfattning av följande statusar:
    - **Installationsstatus** – Visar de vanligaste installationsfelen per enhet, samt appar med installationsfel.  
    - **Status för appskyddsprincip** – Hitta information om tilldelade användare i appskyddsprinciperna, samt flaggade användare.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Appar](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-08.png)

    Som IT-administratör kan du använda Microsoft Intune för att hantera klientappar som ditt företags personal använder. Den här funktionen är ett tillägg till hanteringen av enheter och att skydda data. En av en administratörs prioriteringar är att säkerställa att användarna har åtkomst till appar som de behöver för att utföra sitt arbete. Dessutom kanske du vill tilldela och hantera appar på enheter som inte har registrerats med Intune. Intune erbjuder en mängd funktioner som hjälper dig att få de appar som du behöver, på de enheter som du önskar. 

    > [!NOTE]
    > I fönstret **Appar – Översikt** finns också klientorganisationsstatus och kontoinformation.

    Mer information om hur du lägger till och tilldelar appar finns i [Lägga till appar i Microsoft Intune](../apps/apps-add.md) och [Tilldela appar till grupper med Microsoft Intune](../apps/apps-deploy.md).

9. I fönstret **Appar – Översikt** väljer du **Alla appar** för att se en lista med appar som har lagts till i Intune.

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Klientappar** > **Appar**.

    Du kan lägga till flera olika typer av appar baserat på plattform i Intune. När du har lagt till en app kan du tilldela den till grupper av användare. 

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Alla appar](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-09.png)

    Du hittar mer information i [Lägg till appar i Microsoft Intune](~/apps/apps-add.md). 

10. I navigeringsfönstret väljer du **Användare** för att visa information om de användare du har inkluderat i Intune. Dessa användare är företagets personal.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Användare](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-10.png)

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Användare**.

    Du kan lägga till användare direkt i Intune eller synkronisera användare från din lokala Active Directory. När de har lagts till, kan användare registrera enheter och få åtkomst till företagsresurser. Du kan även ge användare ytterligare behörigheter för åtkomst till Intune. Mer information finns i [Lägga till användare och ge administrativ behörighet till Intune](users-add.md).

11. I navigeringsfönstret väljer du **Grupper** för att se informationen om grupper i Azure Active Directory (Azure AD) som har inkluderats i Intune. Som Intune-administratör använder du grupper för att hantera enheter och användare.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Grupper](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-11.png)

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Grupper**.

    Du kan skapa grupper som passar organisationens behov. Skapa grupper för att ordna användare eller enheter efter geografisk plats, avdelning eller maskinvaruegenskaper. Använd grupper för att hantera skalanpassade aktiviteter. Du kan t.ex. ange principer för många användare eller distribuera appar till en uppsättning enheter. Mer information om grupper finns i [Lägga till grupper för att organisera användare och enheter](../groups-add.md).

12. I navigeringsfönstret väljer du **Administration av klientorganisation** för att se informationen om din Intune-klient.

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Status för klientorganisation**.

    Fönstret **Klientorganisationsadministratör – Status för klientorganisation** innehåller flikar för **Information om klientorganisation**, **Status för anslutningsprogrammet** och **Service Health-instrumentpanel**. Om det har uppstått problem med klientorganisationen eller med själva Intune, hittar du information i det här fönstret. 

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Status för klientorganisation](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-12.png)

    Mer information finns i [Status för Intune-klient](../tenant-status.md).

13. I navigeringsfönstret väljer du **Felsökning + support** > **Felsök** för att kontrollera statusinformationen för en speciell användare. 

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Felsök**.

    I listrutan **Tilldelningar** kan du välja att visa de riktade tilldelningarna för klientappar, principer, uppdateringsringar och registreringsbegränsningar. Dessutom innehåller det här fönstret enhetsinformation, appskyddsstatus och registreringsfel för en speciell användare.

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Felsöka](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-13.png)

    Mer information om felsökning i Intune finns i [Använd felsökningsportalen för att hjälpa företagets användare](../help-desk-operators.md).

14. I navigeringsfönstret väljer du **Felsökning + support** > **Hjälp och support** för att begära hjälp. 

    > [!TIP]
    > Om du tidigare använde Intune i Azure-portalen hittade du informationen ovan i portalen genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välja **Hjälp och support**.

    Som IT-administratör kan du använda alternativet **Hjälp och support** för att söka efter och visa lösningar samt registrera ett supportärende online för Intune. 

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Hjälp och support](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-14.png)

    Om du vill skapa en supportbegäran måste ditt konto ha tilldelats en administratörsroll i Azure Active Directory. Administratörsroller är **Intune-administratör**, **Global administratör** och **Tjänstadministratör**. 

    Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](../get-support.md).

15. I navigeringsfönstret väljer du **Felsökning + support** > **Guidade scenarier** för att visa tillgängliga Intune-scenarier. 

    Ett guidat scenario är en anpassad serie med steg som handlar om ett visst användningsfall från slutpunkt till slutpunkt. Vanliga scenarier baseras på den roll som en administratör, användare eller enhet har i din organisation. Dessa regler kräver vanligtvis en samling noggrant samordnade profiler, inställningar, program och säkerhetskontroller för att ge bästa möjliga användarupplevelse och säkerhet.

    Om du inte är bekant med alla steg och resurser som behövs för att implementera ett visst Intune-scenario kan du använda guidade scenarier som utgångspunkt. 

    ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Guidade scenarier](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-15.png)

    Mer information om guidade scenarier finns i [Översikt över guidade scenarier](~/fundamentals/guided-scenarios-overview.md).

## <a name="configure-the-microsoft-endpoint-manager-admin-center"></a>Konfigurera administrationscentret för Microsoft Endpoint Manager

Med Azure kan du anpassa och konfigurera portalens vy.

### <a name="change-the-dashboard"></a>Ändra instrumentpanelen

I **Instrumentpanel** visas allmän information om enheterna och klientapparna i din Intune-klientorganisation. Med instrumentpaneler kan du skapa en fokuserad och organiserad vy i administrationscentret för Microsoft Endpoint Manager. Använd instrumentpanelerna som en arbetsyta där du snabbt kan starta uppgifter för dagliga åtgärder och övervaka resurser. Du kan exempelvis skapa anpassade instrumentpaneler som baseras på projekt, uppgifter eller användarroller. I administrationscentret för Microsoft Endpoint Manager finns en standardinstrumentpanel som utgångspunkt. Du kan redigera standardinstrumentpanelen, skapa och anpassa fler instrumentpaneler, samt publicera och dela instrumentpaneler så att de blir tillgängliga för andra användare. 

   ![Skärmbild av administrationscentret för Microsoft Endpoint Manager – Instrumentpanel](./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-16.png)

Om du vill ändra din nuvarande instrumentpanel väljer du **Redigera**. Om du inte vill ändra standardinstrumentpanelen kan du skapa en **Ny instrumentpanel**. Genom att skapa en ny instrumentpanel får du en tom, privat instrumentpanel med **Panelgalleriet** där du kan lägga till eller omarrangera paneler. Du kan hitta paneler efter kategori eller resurstyp. Du kan också söka efter vissa paneler. Välj **Min instrumentpanel** för att välja någon av dina befintliga anpassade instrumentpaneler.

### <a name="change-the-portal-settings"></a>Ändra portalinställningarna

Du kan anpassa administrationscentret för Microsoft Endpoint Manager genom att välja standardvy, tema, tidsgräns för autentiseringsuppgifter, samt inställningar för språk och region.

   <img alt="Screenshot of the Microsoft Endpoint Manager admin center - Portal settings" src="./media/tutorial-walkthrough-endpoint-manager/tutorial-walkthrough-mem-17.png" width="250">

## <a name="next-steps"></a>Nästa steg

För att komma igång snabbt med Microsoft Intune går du igenom Intune-snabbstarterna genom att först skapa ett kostnadsfritt Intune-konto.

> [!div class="nextstepaction"]
> [Snabbstart: Prova Microsoft Intune utan kostnad](free-trial-sign-up.md)
