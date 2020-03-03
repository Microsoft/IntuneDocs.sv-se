---
title: Tilldela Managed Google Play-appar till Android enterprise-enheter
titleSuffix: Microsoft Intune
description: Förstå hur du synkroniserar och tilldelar appar till Android enterprise-enheter från Managed Google Play Butik.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2f6c06bf-e29a-4715-937b-1d2c7cf663d4
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a4b3bd06bad6c31c2d0fb4c31a7ad605af96be86
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609197"
---
# <a name="add-managed-google-play-apps-to-android-enterprise-devices-with-intune"></a>Lägg till Google Play för företag-appar till Android enterprise-enheter med Intune

Google Play för företag är Googles appbutik för företag och den enda källan till appar för Android Enterprise. Du kan använda Intune för att samordna distributionen av appar via Google Play för företag för alla Android Enterprise-scenarier (inklusive arbetsprofilregistreringar, samt dedikerade och fullständigt hanterade registreringar). Tillvägagångssättet för att lägga till Google Play för företag-appar i Intune skiljer sig från hur Android-appar läggs till på Android-enheter som inte är för företag. Store-appar, branschspecifika appar (LOB) och webbappar godkänns i eller läggs till i Google Play för företag och synkroniseras sedan till Intune så att de visas i listan över klientappar. När de visas i listan med klientappar kan du hantera tilldelning av alla Google Play för företag-appar på samma sätt som du gör med andra appar.

Intune lägger automatiskt till fyra vanliga Android Enterprise-relaterade appar till Intune-administratörskonsolen när du ansluter din Intune-klient till Google Play för företag för att göra det enklare för dig att konfigurera och använda Android Enterprise-hantering. De fyra apparna är följande:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – Används för fullständigt hanterade Android Enterprise-scenarier. Den här appen installeras automatiskt till fullständigt hanterade enheter under registrerings processen för enheten.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – Hjälper dig att logga in på dina konton om du använder tvåfaktorautentisering. Den här appen installeras automatiskt till fullständigt hanterade enheter under registrerings processen för enheten.
- **[Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – Används för appskyddsprinciper och scenarier med Android Enterprise-arbetsprofiler.
- **[Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise)** – Används för dedikerade/helskärmslägesscenarier i Android Enterprise. IT-administratörer bör skapa en tilldelning för att installera den här appen på dedikerade enheter som ska användas i kioskscenarier med flera appar.

>[!NOTE]
>När en slutanvändare registrerar sina fullständigt hanterade Android-enheter installeras Intune-företagsportalappen automatiskt och programikonen kan visas för slutanvändaren. Om slutanvändaren försöker starta Intune-företagsportalappen omdirigeras slutanvändaren till Microsoft Intune-appen och ikonen för företagsportalappen kommer att döljas senare.

## <a name="before-you-start"></a>Innan du börjar
- Se till att du har anslutit din Intune-klient till Google Play för företag.  Läs [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md) för mer information.
- Om du planerar att registrera arbetsprofilenheter ska du kontrollera att du har konfigurerat Intune och Android-arbetsprofiler så att de fungerar tillsammans i arbetsbelastningen **Enhetsregistrering** i Azure Portal. Mer information finns i [Registrera Android-enheter](../enrollment/android-work-profile-enroll.md).

>[!NOTE]
>När du arbetar med Microsoft Intune, rekommenderar vi att du använder antingen webbläsaren Google Chrome eller Microsoft Edge.

## <a name="managed-google-play-app-types"></a>Hanterade Google Play-apptyper
Det finns tre typer av hanterade appar som är tillgängliga med Google Play för företag:

- **Hanterad Google Play Store-app** – offentliga appar som är allmänt tillgängliga i Play Store. Hantera de här apparna i Intune genom att bläddra efter de appar som du vill hantera, godkänna dem och sedan synkronisera dem i Intune.
- **Privat hanterad Google Play-app** – dessa är LOB-appar som publicerats till Google Play för företag av Intune-administratörer.  Dessa appar är privata och endast tillgängliga för din Intune-klient. PÅ detta vis hanteras och distribueras LOB-appar med Google Play för företag och Android Enterprise.
- **Hanterad Google Play-webblänk** – webblänkar med ikoner som har definierats av IT-administratörer som kan distribueras till Android Enterprise-enheter. De visas på enheterna i deras applista precis som vanliga appar.

## <a name="managed-google-play-store-apps"></a>Hanterade appar från Google Play Store
Det finns två sätt att söka efter och godkänna hanterade Google Play Store-appar med Intune:

1. Direkt i Intune-konsolen – bläddra och godkänn appar från Google Play Store i en vy som finns i Intune. Den öppnas direkt i Intune-konsolen och kräver inte att du autentiserar igen med ett annat konto.
1. I konsolen för Google Play för företag – du kan välja att öppna konsolen för Google Play för företag direkt och godkänna appar där. Mer information finns i [Synkronisera en hanterad Google Play-app med Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).  Detta kräver en separat inloggning med det konto som du använde för att ansluta din Intune-klient till Google Play för företag.

### <a name="add-a-managed-google-play-store-app-directly-in-the-intune-console"></a>Lägg till en hanterad Google Play Store-app direkt i Intune-konsolen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Managed Google Play-app** i rutan **Välj apptyp** bland de tillgängliga typerna av **Store-appar**.
4. Klicka på **Välj**. **Managed Google Play** Store för appar visas.

    > [!NOTE]
    > Ditt Intune-konto måste vara anslutet till ditt Android Enterprise-konto för att kunna söka Managed Google Play Store-appar. Läs [Anslut ditt Intune-konto till ditt hanterade Google Play-konto](../enrollment/connect-intune-android-enterprise.md) för mer information.

5. Välj en app för att visa information om appen.
6. På sidan som visar appen väljer du **Godkänn**. Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder.
7. Välj **Godkänn** för att godkänna appbehörigheterna och fortsätta.
8. Välj **Behåll godkända när appen begär nya behörigheter** i fliken **Inställningar för godkännande** och klicka sedan på **Spara**. 

    > [!IMPORTANT]
    > Om du inte väljer det här alternativet måste du manuellt godkänna alla nya behörigheter om apputvecklaren publicerar en uppdatering. Detta innebär att installationer och uppdateringar av appen stoppas tills behörigheterna har godkänts. Av detta skäl rekommenderar vi att du väljer alternativet för att automatiskt godkänna nya behörigheter. 

9. Klicka på **Välj** för att välja appen.
10. Klicka på **Synkronisera** i längst upp på bladet för att synkronisera med tjänsten Managed Google Play.
11. Klicka på **Uppdatera** för att uppdatera applistan och visa den nyligen tillagda appen.

### <a name="add-a-managed-google-play-store-app-in-the-managed-google-play-console-alternative"></a>Lägg till en hanterad Google Play Store-app i konsolen för Google Play för företag (alternativ)
Om du vill synkronisera en hanterad Google Play-app med Intune i stället för att lägga till den direkt med hjälp av Intune kan du använda följande steg.

> [!IMPORTANT]
> Informationen nedan är en alternativ metod för att lägga till en hanterad Google Play-app med Intune enligt beskrivningen ovan.

1. Gå till [Managed Google Play Butik](https://play.google.com/work). Logga in med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android Enterprise.
2. Sök i butiken och välj app som du vill tilldela med hjälp av Intune.
3. På sidan som visar appen väljer du **Godkänn**.  
    I följande exempel har Microsoft Excel-appen valts.

    ![Knappen Godkänn i Managed Google Play Butik](./media/apps-add-android-for-work/approve.png)

   Ett fönster för appen öppnas där du uppmanas att tilldela behörigheter till appen för att utföra olika åtgärder.

4. Välj **Godkänn** för att godkänna appbehörigheterna och fortsätta.

    ![Knappen Godkänn för app-behörigheter](./media/apps-add-android-for-work/approve-app-permissions.png)

5. Välj ett alternativ för att hantera nya begäranden om app-behörighet och välj sedan **Spara**.

    ![Alternativ för att hantera nya begäranden om app-behörighet](./media/apps-add-android-for-work/approve-app-settings.png)

    Appen godkänns och den visas i IT-administrationskonsolen. Därefter kan du [synkronisera Android-arbetsprofilappen med Intune](apps-add-android-for-work.md#sync-a-managed-google-play-app-with-intune).

## <a name="managed-google-play-private-lob-apps"></a>Privata LOB-appar för Google Play för företag-konto

Det finns två sätt att lägga till LOB-appar i Google Play för företag:

1. Direkt i Intune-konsolen – på så sätt kan du lägga till LOB-appar genom att helt enkelt skicka appens APK och ett namn direkt i Intune. Den här metoden kräver inte att du har ett Google Developer-konto och du behöver inte betala avgiften för att registrera dig hos Google som utvecklare.  Den här metoden är enklare och har betydligt färre steg och gör LOB-appar tillgängliga för hantering på så lite som tio minuter.
1. I Google Play Developer-konsolen – om du har ett Google Developer-konto eller om du vill konfigurera avancerade distributionsfunktioner som bara är tillgängliga i Google Play Developer-konsolen (som att lägga till fler bildskärmar) kan du använda [Google Play Developer-konsolen](https://play.google.com/apps/publish). 

### <a name="managed-google-play-private-lob-app-publishing-directly-in-the-intune-console"></a>Privata hanterade Google Play-appar (LOB) publiceras direkt i Intune-konsolen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Managed Google Play-app** i rutan **Välj apptyp** bland de tillgängliga typerna av **Store-appar**.
4. Klicka på **Välj**. **Managed Google Play** Store för appar visas i Intune.
5. Välj **Privata appar** (bredvid *lås*ikonen) i Google Play-fönstret. 
6. Lägg till en ny app genom att klicka på knappen **"+"** längst ned till höger.
7. Lägg till et **Appnamn**, klicka på **Ladda upp APK** och lägg till APK-appaketet.
8. Klicka på **Skapa**.
9. Stäng fönstret Google Play för företag om du är färdig med att lägga till appar.
10. Klicka på **Synkronisera** i **app**fönstret för att synkronisera med den hanterade Google Play-tjänsten. 

    > [!NOTE]
    > Det kan ta flera minuter för privata appar att bli tillgängliga för synkronisering. Om appen inte visas första gången du utför en synkronisering kan du vänta ett par minuter och starta en ny synkronisering.

Mer information om privata hanterade Google Play-appar, inklusive vanliga frågor och svar, finns i denna supportartikel från Google: https://support.google.com/googleplay/work/answer/9146439

>[!IMPORTANT]
>Privata appar som läggs till med den här metoden kan aldrig göras offentliga. Använd bara det här publicerings alternativet om du är säker på att appen alltid ska vara privat i din organisation.

### <a name="managed-google-play-private-lob-app-publishing-using-the-google-developer-console"></a>Publicera en hanterad privat Google Play-app (LOB) med Google Developer-konsolen

1. Logga in till [Google Play Developer-konsolen](https://play.google.com/apps/publish) med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android enterprise.  
    Om du loggar in för första gången måste du registrera dig och betala en avgift för att bli medlem i Google-utvecklarprogrammet.
2. I konsolen väljer du **Lägg till nytt program**.
3. Du kan överföra och tillhandahålla information om din app på samma sätt som du publicerar en app i Google Play-butiken. Du måste dock välja **Gör det här programmet tillgängligt endast för min organisation (<*organisationsnamn*>)** .

    ![Gör appen tillgänglig endast för din organisation](./media/apps-add-android-for-work/restrict.png)

    Den här åtgärden gör bara appen tillgänglig för din organisation. Den blir inte tillgänglig på i offentliga Google Play-butiken.

    Mer information om att ladda upp och publicerar Android-appar finns i [Google Developer Console Help](https://support.google.com/googleplay/android-developer/answer/113469) (Hjälp med Google-utvecklarkonsolen).
4. När du har publicerat din app kan du logga in på [Google Play-butiken för företag](https://play.google.com/work) med samma konto som du använde för att konfigurera anslutningen mellan Intune och Android för företag.
5. I noden **Appar** i butiken, kontrollerar du att den app som du har publicerat visas.  
    Appen godkänns automatiskt för att synkroniseras med Intune.

## <a name="managed-google-play-web-links"></a>Hanterade Google Play-webblänkar

Hanterade Google Play-webblänkar kan installeras och hanteras precis som andra Android-appar. När de installeras på en enhet visas de i användarens applista tillsammans med andra appar som de har installerat. När användaren trycker på dem startar de i enhetens webbläsare.

Webblänkar öppnas med Microsoft Edge eller någon annan webbläsarapp som du väljer att distribuera. Se till att distribuera minst en webbläsarapp till enheterna. Annars kommer webblänkarna inte att öppnas korrekt. Alla **Visningsalternativ** som är tillgängliga för webblänkar (fullskärm, fristående och minimalt gränssnitt) fungerar endast i webbläsaren Chrome. 

> [!IMPORTANT]
> Vid publiceringen av det här dokumentet finns en känd bugg hos GOogle som förhindrar att webblänkar öppnas på enheter med andra webbläsare än Chrome. Google har åtagit sig att åtgärda det här felet.  Detta meddelande kommer att tas bort när Microsoft har bekräftat att Google har publicerat sin korrigering.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Managed Google Play-app** i rutan **Välj apptyp** bland de tillgängliga typerna av **Store-appar**.
4. Klicka på **Välj**. **Managed Google Play** Store för appar visas i Intune.
5. Välj **Webbappar** (bredvid *jordglobs*ikonen) i Google Play-fönstret.
6. Lägg till en ny app genom att klicka på knappen **"+"** längst ned till höger.
7. Lägg till en **Apprubrik**, webbappens  **URL**, välj hur appen ska visas och välj en appikon.
8. Klicka på **Skapa**.
9. Stäng fönstret Google Play för företag om du är färdig med att lägga till appar.
10. Klicka på **Synkronisera** i **app**fönstret för att synkronisera med den hanterade Google Play-tjänsten. 

    > [!NOTE]
    > Observera att det kan ta flera minuter för webbappar att bli tillgängliga för synkronisering. Om appen inte visas första gången du utför en synkronisering kan du vänta ett par minuter och starta en ny synkronisering.

## <a name="sync-a-managed-google-play-app-with-intune"></a>Synkronisera en Managed Google Play-app med Intune

Om du har godkänt en app från butiken men inte ser den i arbetsbelastningen **Appar** kan du framtvinga en omedelbar synkronisering genom att göra följande:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Välj **Appar** > **Klientadministration** > **Anslutningsappar och token** > **Hanterat Google Play-konto**.
5. I fönstret **Hanterat Google Play-konto** väljer du **Uppdatera**.  
    Sidan uppdaterar tid och status för den senaste synkroniseringen.
6. Välj  **Appar** > **Alla appar** i administrationscentret för Microsoft Endpoint Manager.  
    Den nya tillgängliga Managed Google Play-appen visas.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices"></a>Tilldela en hanterad Google Play-app för Android Enterprise-arbetsprofilenheter

När appen visas i noden **Applicenser** i arbetsbelastningsfönstret **Appar** kan du [tilldela den på samma sätt som du gör med andra appar](/intune-azure/manage-apps/deploy-apps) genom att tilldela användargrupper appen.

När du har tilldelat appen installeras den (eller görs tillgänglig för installation) på de enheter vars användare du har som mål. Användaren av enheten behöver inte godkänna installationen. Mer information om Android Enterprise-arbetsprofilenheter finns i [Konfigurera registrering av Android Enterprise-arbetsprofilenheter](../enrollment/android-work-profile-enroll.md). 

> [!NOTE] 
> Endast appar som har tilldelats visas för slutanvändaren i Google Play-butiken för företag. Detta är ett viktigt steg för administratören att vidta i samband med konfigurering av appar med Google Play för företag.

## <a name="assigning-a-managed-google-play-app-to-android-enterprise-fully-managed-devices"></a>Tilldela en hanterad Google Play-app till fullständigt hanterade Android Enterprise-enheter

[Fullständigt hanterade Android Enterprise-enheter](../enrollment/android-fully-managed-enroll.md) är företagsägda enheter som är associerade med en enskild användare och som endast används för arbete och inte för personligt bruk. Användare på fullständigt hanterade enheter kan få sina tillgängliga företagsappar från den hanterade Google Play-appen på sina enheter.

Som standard tillåter en fullständigt hanterad Android-enhet inte att anställda installerar appar som inte har godkänts av organisationen. Dessutom kan de anställda inte ta bort några installerade appar i strid mot principen. Om du vill ge användare åtkomst till appar från hela Google Play-butiken istället för att bara ha åtkomst till godkända appar i Google Play för företag-butiker kan du ställa in **Tillåt åtkomst till alla appar i Google Play Store** på **Tillåt**. Med den här inställningen kan användaren komma åt alla appar i Google Play-butiken med sitt företagskonto men köp kan dock begränsas. Du kan ta bort inköpsbegränsningen genom att låta användare lägga till nya konton på enheten. Om du gör det får slutanvändare köpa appar från Google Play Store med hjälp av personliga konton, samt att genomföra köp i appen. Mer information finns i [Enhetsinställningarna för Android Enterprise tillåter eller begränsar funktioner med hjälp av Intune](../configuration/device-restrictions-android-for-work.md). 

> [!NOTE]
> Microsoft Intune-appen och Microsoft Authenticator-appen installeras som obligatoriska appar på alla fullständigt hanterade enheter under registreringen. Att de här apparna installeras automatiskt ger stöd för villkorlig åtkomst och Microsoft Intune App-användare kan se och lösa kompatibilitetsproblem. 

## <a name="manage-android-enterprise-app-permissions"></a>Hantera behörigheter för Android Enterprise-app
Android Enterprise kräver att du godkänner appar i den Managed Google Play-webbkonsolen innan du synkroniserar dem med Intune och tilldelar dem till användarna. Eftersom Android Enterprise låter dig distribuera dessa appar till användarnas enheter tyst och automatiskt måste du acceptera appens behörigheter för alla användare. Användare ser inga programbehörigheter när de installerar apparna, så det är viktigt att du har förstått dessa behörigheter.

När apputvecklare uppdaterar behörigheter med en ny version av appen tillåts de inte automatiskt, även om du har godkänt tidigare behörigheter. Enheter som kör den tidigare versionen av appen kan fortfarande använda den. Appen uppgraderas dock inte förrän de nya behörigheterna har godkänts. Enheter utan appen installerar den inte förrän du har godkänt dess nya behörigheter. 

### <a name="update-app-permissions"></a>Uppdatera app-behörigheter

Du bör regelbundet besöka den hanterade Google Play-konsolen för att söka efter nya behörigheter. Du kan konfigurera Google Play att skicka dig eller andra ett e-postmeddelande när nya behörigheter krävs för en godkänd app. Om du tilldelar en app och noterar att den inte installeras på enheterna, söker du efter nya behörigheter genom att göra följande:

1. Gå till [Google Play](https://play.google.com/work).
2. Logga in med det Google-konto som du använde för att publicera och godkänna apparna.
3. Välj fliken **Uppdateringar** och kontrollera om några appar behöver en uppdatering.  
    Alla listade appar kräver nya behörigheter och tilldelas inte innan de tillämpas.

Du kan också konfigurera Google Play att automatiskt godkänna app-behörigheter på nytt skilt för varje app.

## <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices"></a>Ytterligare rapportering för Managed Google Play-app för Android Enterprise-arbetsprofilenheter

För Managed Google Play-appar som distribueras till Android Enterprise-arbetsprofilenheter kan du visa status och versionsnumret för den app som är installerad på en enhet som använder Intune. 

## <a name="delete-managed-google-play-apps"></a>Radera hanterade Google Play-appar
Du kommer att kunna ta bort hanterade Google Play-appar från Microsoft Intune om nödvändigt. Om du vill ta bort en hanterad Google Play-app öppnar du Microsoft Intune i Azure Portal och väljer **Appar** > **Alla appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

> [!NOTE]
> Om en app är ej godkänd eller har tagits bort från den hanterade Google Play-butiken tas den inte bort från listan över appar i Intune-klienten. På så sätt kan du fortfarande rikta en avinstallationsprincip till användare även om appen är ej godkänd.

## <a name="android-enterprise-system-apps"></a>Android Enterprise-systemprogram

Du kan aktivera en Android Enterprise-systemapp för [dedikerade Android Enterprise-enheter](../enrollment/android-kiosk-enroll.md) eller [fullständigt hanterade enheter](../enrollment/android-fully-managed-enroll.md). Du hittar mer information om att lägga till en Android Enterprise-systemapp i [Lägg till Android Enterprise-systemappar i Microsoft Intune](apps-ae-system.md).

## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)
