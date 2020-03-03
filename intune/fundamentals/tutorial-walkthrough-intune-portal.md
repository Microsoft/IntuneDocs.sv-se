---
title: Självstudier – Genomgång av Intune i Azure Portal
titleSuffix: Microsoft Intune
description: I den här självstudiekursen får du en genomgång av Microsoft Intune så att du får mer kunskaper om hur du utför uppgifter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/06/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e892d8a3-7f74-498c-98d5-e968a8fbb049
Customer intent: As an Intune admin, I want to learn where to find the different features in Intune.
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 203d243df3e8ae496e7ff78f20222fd361417c3d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514055"
---
# <a name="tutorial-walkthrough-of-microsoft-intune-in-the-azure-portal"></a>Självstudie: Genomgång av Microsoft Intune i Azure Portal

[Azure](https://docs.microsoft.com/learn/modules/welcome-to-azure) innehåller över 100 tjänster som hjälper dig med olika scenarier och möjligheter i molnet. Microsoft Intune är en av flera tjänster som finns i Azure. Med Intune kan du se till att företagets enheter, appar och data uppfyller företagets säkerhetskrav. Du har kontrollen och kan ange vilka krav som måste kontrolleras och vad som händer när de kraven inte uppfylls. Du hittar Microsoft Intune-tjänsten på [Azure Portal](https://portal.azure.com). Att förstå funktionerna som finns i Intune hjälper dig att utföra uppgifter för hantering av mobilenheter (MDM) och hantering av mobilprogram (MAM).

I de här självstudierna får du:
> [!div class="checklist"]
> * en genomgång av Microsoft Intune
> * Konfigurera Azure Portal

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
Innan du konfigurerar Microsoft Intune, bör du granska följande krav:

- [Operativsystem och webbläsare som stöds](../supported-devices-browsers.md) 
- [Krav för nätverkskonfiguration och bandbredd](../network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune

Du kan prova Intune utan kostnad i 30 dagar. Om du redan har ett arbets- eller skolkonto **loggar du in** med det kontot och lägger till Intune i din prenumeration. Annars kan du [registrera dig](free-trial-sign-up.md) för ett kostnadsfritt utvärderingskonto så att du kan använda Intune i din organisation.

> [!IMPORTANT]
> Du kan inte kombinera ett befintligt arbets- eller skolkonto efter att du har registrerat dig för ett nytt konto.

## <a name="tour-microsoft-intune"></a>Genomgång av Microsoft Intune

Följ stegen nedan så får du en bättre förståelse av Intune i Azure Portal. När du har slutfört genomgången har du bättre kunskaper om några av huvudområdena i Intune.

1. Öppna en webbläsare och logga in på [Intune-portalen](https://aka.ms/intuneportal). Använd din kostnadsfria utvärderingsprenumeration om Intune är nytt för dig.

    ![Skärmbild av Microsoft Intune-portalen](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-01.png)

    När du öppnar Intune eller någon annan tjänst i Azure visas tjänsten i ett fönster. Några av de första arbetsbelastningarna du kanske använder i Intune är **Enheter**, **Klientappar**, **Användare** och **Grupper**. En arbetsbelastning är helt enkelt ett delområde av en tjänst. När du markerar en arbetsbelastning öppnas fönstret på hela sidan. Andra fönster skjuts ut från höger i fönstret när de öppnas och stängs och visar det föregående fönstret. Fönster kallas även blad. 

    Som standard visas **översiktsfönstret** när du öppnar Intune. I det här fönstret får du en snabb ögonblicksbild av enhetstilldelning och efterlevnadsstatus samt status för appinstallationer.

2. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** för att visa information om de registrerade enheterna i din Intune-klient. Om du börjar med en ny Intune-klient har du inga registrerade enheter än. 

    ![Skärmbild av enhetsregistreringsfönstret](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-02.png)
    
    Med Intune kan du hantera personalens enheter och appar, till exempel hur de kommer åt företagsdata. Enheterna måste först registreras i Intune innan du kan använda MDM-tjänsten. När en enhet registreras utfärdas ett MDM-certifikat till den. Certifikatet används för att kommunicera med Intune-tjänsten. 

    Det finns flera olika metoder för att registrera personalens enheter i Intune. Varje metod påverkas av ägarskapet för enheten (personlig eller företagsägd), enhetstypen (iOS/iPadOS, Windows, Android) och hanteringskraven (återställning, tillhörighet, låsning). Men innan du kan aktivera enhetsregistrering måste du konfigurera Intune-infrastrukturen. I synnerhet kräver registrering av enheter att du [anger en MDM-utfärdare](mdm-authority-set.md). Mer information om hur du förbereder Intune-miljön (klienten) finns i [Konfigurera Intune](setup-steps.md). När Intune-klienten är klar kan du registrera enheter. Mer information om enhetsregistrering finns i [Vad är enhetsregistrering?](../enrollment/device-enrollment.md)

3. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsefterlevnad** för att visa information om efterlevnad för enheter som hanteras av Intune. Information visas som ser ut ungefär som i följande bild.

    ![Skärmbild av fönstret för enhetsefterlevnad](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-03.png)
    
    Ett efterlevnadskrav är i princip samma sak som en regel, t. ex. att kräva en PIN-kod för en enhet eller att kräva enhetskryptering. Efterlevnadsprinciper definierar de regler och inställningar som en enhet måste följa för att anses vara kompatibel. Om du vill använda enhetsefterlevnad måste du ha:
    - en prenumeration på Intune och Azure Active Directory (Azure AD) Premium
    - enheter med en plattform som stöds
    - enheter som har registrerats i Intune
    - enheter som har registrerats på en användare eller ingen primär användare.
    
    Mer information finns i [Komma igång med efterlevnadsprinciper för enheter i Intune](../protect/device-compliance-get-started.md).

4. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetskonfiguration** för att visa information om enhetsprofiler i Intune.

    ![Skärmbild av fönstret för enhetskonfiguration](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-04.png)
    
    Intune innehåller inställningar och funktioner som du kan aktivera eller inaktivera på olika enheter i din organisation. Dessa inställningar och funktioner läggs till i ”konfigurationsprofiler”. Du kan skapa profiler för olika enheter och plattformar, till exempel iOS/iPadOS, Android och Windows. Du kan sedan använda Intune för att tillämpa profilen i din organisation.   

    Mer information om enhetskonfiguration finns i [Tillämpa inställningar för funktioner på dina enheter med enhetsprofiler i Microsoft Intune](../configuration/device-profiles.md).

5. I [Intune](https://aka.ms/intuneportal) väljer du **Enheter** för att visa information om Intune-klientens registrerade enheter. Om du börjar med en ny Intune-registrering har du inga registrerade enheter än.

    ![Skärmbild av enhetsregistreringsfönstret](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-05.png)

    I fönstret **Enheter** finns information om klientens registrerade enheter. Du kan klicka på **Alla enheter** för att visa en lista över enheter för Intune-klienten.

6. I [Intune](https://aka.ms/intuneportal) väljer du **Klientappar** för att visa appinstallationsstatus.

    ![Skärmbild av fönstret för klientappar](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-06.png)

    Som IT-administratör kan du använda Microsoft Intune för att hantera klientappar som ditt företags personal använder. Den här funktionen är ett tillägg till hanteringen av enheter och att skydda data. En av en administratörs prioriteringar är att säkerställa att användarna har åtkomst till appar som de behöver för att utföra sitt arbete. Dessutom kanske du vill tilldela och hantera appar på enheter som inte har registrerats med Intune. Intune erbjuder en mängd funktioner som hjälper dig att få de appar som du behöver, på de enheter som du önskar. Mer information om hur du lägger till och tilldelar appar finns i [Lägga till appar i Microsoft Intune](../apps/apps-add.md) och [Tilldela appar till grupper med Microsoft Intune](../apps/apps-deploy.md).

7. I [Intune](https://aka.ms/intuneportal) väljer du **Villkorlig åtkomst** för att visa information om åtkomstprinciper.

    ![Skärmbild av fönstret för villkorlig åtkomst](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-07.png)

    Villkorlig åtkomst syftar på de olika sätt på vilka du kan styra de enheter och appar som tillåts ansluta till dina e-post- och företagsresurser. Mer information om enhetsbaserad och appbaserad villkorlig åtkomst och vanliga scenerier för användning av villkorlig åtkomst med Intune finns i [Vad är villkorlig åtkomst?](../protect/conditional-access.md)

8. I [Intune](https://aka.ms/intuneportal) väljer du **Användare** för att visa information om de användare du har inkluderat i Intune. Dessa användare är företagets personal.

    ![Skärmbild av fönstret Användare](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-08.png)

    Du kan lägga till användare direkt i Intune eller synkronisera användare från din lokala Active Directory. När de har lagts till, kan användare registrera enheter och få åtkomst till företagsresurser. Du kan även ge användare ytterligare behörigheter för åtkomst till Intune. Mer information finns i [Lägga till användare och ge administrativ behörighet till Intune](users-add.md).

9. I [Intune](https://aka.ms/intuneportal) väljer du **Grupper** för att visa information om grupper i Azure Active Directory (Azure AD) som inkluderats i Intune. Som Intune-administratör använder du grupper för att hantera enheter och användare.

    ![Skärmbild av fönstret Grupper](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-09.png)

    Du kan skapa grupper som passar organisationens behov. Skapa grupper för att ordna användare eller enheter efter geografisk plats, avdelning eller maskinvaruegenskaper. Använd grupper för att hantera skalanpassade aktiviteter. Du kan t.ex. ange principer för många användare eller distribuera appar till en uppsättning enheter. Mer information om grupper finns i [Lägga till grupper för att organisera användare och enheter](../groups-add.md).

10. I [Intune](https://aka.ms/intuneportal) väljer du **Hjälp och support** för att fråga om hjälp. Som IT-administratör kan du använda alternativet **Hjälp och support** för att söka efter och visa lösningar samt registrera ett supportärende online för Intune. 

    ![Skärmbild av fönstret Hjälp och support](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-10.png)

    Om du vill skapa en supportbegäran måste ditt konto ha tilldelats en administratörsroll i Azure Active Directory. Administratörsroller är **Intune-administratör**, **Global administratör** och **Tjänstadministratör**. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](../get-support.md).

11. I [Intune](https://aka.ms/intuneportal) väljer du **Klientstatus** för att visa information om Intune-klienten.

    ![Skärmbild av fönstret Klientstatus](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-11.png)

    Informationen i Klientstatus är bland annat status för anslutningsappar, Intune-tjänstens hälsotillstånd och Intune-nyheter. Om det finns problem med klienten eller med själva Intune hittar du information i fönstret **Klientstatus**. Mer information finns i [Status för Intune-klient](../tenant-status.md).

12. I [Intune](https://aka.ms/intuneportal) väljer du **Felsök** för att nå en genväg till felsökningstips, att begära support eller kontrollera status för Intune. Informationen är specifik för den Intune-användare du väljer.

    ![Skärmbild av fönstret Felsök](./media/tutorial-walkthrough-intune-portal/tutorial-walkthrough-intune-portal-12.png)

Mer information om felsökning i Intune finns i [Använd felsökningsportalen för att hjälpa företagets användare](../help-desk-operators.md).

## <a name="configure-the-azure-portal"></a>Konfigurera Azure Portal

Med Azure kan du anpassa och konfigurera portalens vy.

### <a name="change-the-sidebar"></a>Ändra sidopanelen

På **sidopanelen** till vänster på Azure Portal finns en lista över alla tillgängliga Azure-tjänster. Du kan ändra utseende på den här omfattande listan från standardvyn så att du alltid kan se de tjänster som är viktigast för dig. I informationen nedan används Intune som exempel på en tjänst som vi ska lägga till överst i listan.

![En användare söker efter Microsoft Intune i listan ”Fler tjänster”.](./media/tutorial-walkthrough-intune-portal/azure-add-intune1.png)

1. Välj **Alla tjänster** på sidopanelen till vänster på sidan.
2. Sök efter **Intune** i filterrutan.
3. Markera **stjärnan** för att lägga till Intune längst ned i listan över dina favorittjänster.
4. Håll markören över Intune-tjänsten. Markera och dra Intune med hjälp av de **tre lodräta punkterna** till höger om namnet på tjänsten.

### <a name="change-the-dashboard"></a>Ändra instrumentpanelen

Standardstartsidan är **instrumentpanelen**. På den här sidan anpassar du dina paneler så att de visar den information som är mest relevant för dig.

![En bild av den vanliga nya instrumentpanelen. Sidopanelen med alla tjänster visas till vänster och huvudinstrumentpanelen i mitten. Knapparna för instrumentpanelsändringar finns längst upp, med paneler som ger åtkomst till alla resurser, snabbstartsguider, tjänstens hälsotillstånd och Azure Marketplace.](./media/tutorial-walkthrough-intune-portal/azure-default-dashboard.png)

Om du vill ändra din nuvarande instrumentpanel väljer du **Redigera instrumentpanel**. Om du inte vill ändra standardinstrumentpanelen kan du skapa en **Ny instrumentpanel**. Genom att skapa en ny instrumentpanel får du en tom, privat instrumentpanel med **Panelgalleriet** där du kan lägga till eller omarrangera paneler. Du kan söka efter paneler via deras **allmänna** kategori, **typ**, via **Sök** och via en **resursgrupp** eller **tagg**.

Du kan också lägga till paneler direkt på instrumentpanelen från valfri knapp med **tre punkter** och välja **Fäst på instrumentpanel**.

![En närbild av Användare och grupper > Alla grupper i Intune, där alternativet Fäst på instrumentpanel visas längst ut till höger om gruppen.](./media/tutorial-walkthrough-intune-portal/azure-pin-to-dashboard.png)

Den här funktionen är mer relevant när du har lagt till mer innehåll, exempelvis grupper och användare, i Intune.

## <a name="next-steps"></a>Nästa steg

För att komma igång snabbt med Microsoft Intune går du igenom Intune-snabbstarterna genom att först skapa ett kostnadsfritt Intune-konto.

> [!div class="nextstepaction"]
> [Snabbstart: Prova Microsoft Intune utan kostnad](free-trial-sign-up.md)
