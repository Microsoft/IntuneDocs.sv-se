---
title: Registrera Android-enheter i Intune
titlesuffix: Microsoft Intune
description: Läs hur du registrerar Android-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3212d1a3d3454542dd9d34409fc788558f2d7eed
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="enroll-android-devices"></a>Registrera Android-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du hantera Android-enheter, inklusive Samsung Knox Standard-enheter. Du kan också hantera arbetsprofilen [Android for Work-enheter](#enable-enrollment-of-android-for-work-devices).

Enheter som kör Samsung Knox Standard har stöd för hantering av flera användare med Intune. Det innebär att användarna kan logga in och ut ur enheten med sina autentiseringsuppgifter för Azure AD. Enheten är centralt hanterad oavsett om den används eller inte. När användare loggar in får de tillgång till appar och eventuella principer tillämpas på dem. Alla appdata rensas när användaren loggar ut.

## <a name="prerequisite"></a>Krav

Förbered hantering av mobila enheter genom att ange MDM-utfärdare som **Microsoft Intune**. Fler anvisningar finns i [Ange MDM-utfärdare](mdm-authority-set.md). Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.

## <a name="set-up-android-enrollment"></a>Konfigurera Android-registrering

Som standard tillåter Intune registrering av Android- och Samsung Knox Standard-enheter.

Se [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md) för att blockera Android-enheter eller endast blockera personligt ägda Android-enheter från registrering.

Användarna måste registrera sina enheter genom att hämta appen Intune-företagsportal (tillgänglig från Google Play) och sedan öppna appen och följa anvisningarna. När Android-enheter hanteras kan du [tilldela efterlevnadsprinciper](compliance-policy-create-android.md), [hantera appar](app-management.md) med mera.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Aktivera registrering av Android for Work-enheter

Om du vill aktivera hantering av arbetsprofilen på enheter som har [stöd för Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), måste du lägga till en Android for Work-bindning i Intune. Om du vill registrera enheter i Android for Work, men enheterna redan har registrerats som vanliga Android-enheter, måste enheterna avregistreras och sedan registreras igen.

Om du registrerar Android for Work-enheter med hjälp av ett konto för [Enhetsregistreringshanterare](device-enrollment-manager-enroll.md) går det att registrera högst 10 enheter per konto.

Mer information finns i [Data som Intune skickar till Google](data-intune-sends-to-google.md).

## <a name="add-android-for-work-binding-for-intune"></a>Lägga till Android for Work-bindning för Intune

> [!NOTE]
> På grund av interaktion mellan Google- och Microsoft-domäner kan det i det här steget krävas att du justerar inställningarna för webbläsaren för att allt ska slutföras.  Se till att ”portal.azure.com” och ”play.google.com” finns i samma säkerhetszon i webbläsaren.

1. **Konfigurera Intune MDM**<br>
Om du inte redan gjort det, förbereder du för hantering av mobila enheter genom att ange **Microsoft Intune** som [utfärdare för hantering av mobila enheter](mdm-authority-set.md).
2. **Konfigurera Android for Work-bindning**<br>
    
   a. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal), välj **Enhetsregistrering** > **Android-registrering** > **Hanterat Google Play-konto**.  Om du använder en anpassad Intune-administratörsroll krävs läs- och uppdateringsbehörigheter för organisationen för åtkomst till detta.
   
   ![Registreringsskärm för Android for Work](./media/android-work-bind.png)

   b. Välj **Jag accepterar** för att ge Microsoft behörighet att [skicka information om användare och enhet till Google](data-intune-sends-to-google.md). 
   
   c. Välj **Launch Google to connect now** (Starta Google för att ansluta nu) för att öppna Android for Work i Google Play Butik. Webbplatsen öppnas på en ny flik i webbläsaren.
  
   d. **Logga in på Google**<br>
   Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla hanteringsuppgifter för Android for Work för den här klienten. Det här är det Google-konto som företagets IT-administratörer delar för att hantera och publicera appar i Play for Work-konsolen. Du kan använda ett befintligt Google-konto eller skapa ett nytt.  Det konto du väljer får inte vara kopplat till en G Suite-domän.

   e. **Ange organisationsinformation**<br>
   Ange företagets namn för **Organisationsnamn**. **Microsoft Intune** ska visas som **Enterprise mobility management (EMM)-provider**. Godkänn Android for Work-avtalet och välj sedan **Bekräfta**. Din begäran kommer att behandlas.

## <a name="specify-android-for-work-enrollment-settings"></a>Ange inställningar för registrering av Android for Work
Android for Work stöds endast på vissa Android-enheter. Se Googles [Android for Work requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22) (Krav för Android for Work). Alla enheter som har stöd för Android for Work stöder även konventionell Android-hantering. Intune gör det möjligt att ange hur enheter med stöd för Android for Work ska hanteras inifrån [Registreringsbegränsningar](enrollment-restrictions-set.md).

- **Blockera (ange som standard)**: Alla Android-enheter, inklusive enheter som stöder Android for Work, registreras som konventionella Android-enheter.
- **Tillåt**: Alla enheter som stöder Android for Work registreras som Android for Work-enheter. Alla Android-enheter som inte stöder Android for Work registreras som konventionella Android-enheter.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Godkänn företagsportalappen i den hanterade Google Play-butiken
Du måste godkänna företagsportalappen för Android i den hanterade Google Play-butiken för att den ska kunna ta emot automatiska appuppdateringar. Om du inte godkänner den kommer företagsportalappen till slut att bli inaktuell och kan därmed inte ta emot viktiga felkorrigeringar eller nya funktioner när Microsoft släpper dem.

Så här godkänner du Intune-företagsportalen:

1.  Bläddra till appen Företagsportal i [hanterade Google Play Butik](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Logga in på den hanterade Google Play-butiken med samma Google-konto som du använde när du konfigurerade bindningen för Android for Work.
3.  Klicka på **Godkänn** för att öppna en ny dialogruta.
4.  Granska behörigheterna i den här dialogrutan och klicka sedan på **Godkänn**. Du måste tillåta dessa behörigheter för att företagsportalappen ska kunna hantera arbetsprofilen på enheten.
5.  Välj **Keep approved when app requests new permissions** (Behåll godkända när appen begär nya behörigheter) och klicka sedan på **Spara.**

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Instruera slutanvändarna att de ska gå till Google Play för att hämta Intune-företagsportalappen, öppna appen och följa anvisningarna för att registrera sina enheter. Appen hjälper användarna genom registreringsprocessen och förklarar vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

Du kan även skicka dem en länk till stegen för registrering online: [Registrera en Android-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Information om andra användaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](end-user-educate.md)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>Ta bort bindning för ditt administratörskonto för Android for Work

Du kan inaktivera Android for Work-registrering och hantering. Om du väljer **Ta bort bindning** i Intunes administratörskonsol tas alla registrerade Android for Work-enheter bort från registreringen. Relationen mellan Android for Work-kontot och Intune tas också bort.

### <a name="to-unbind-an-android-for-work-account"></a>Ta bort bindningen för ett Android for Work-konto

1. **Ta bort en Android for Work-bindning**<br>
    Som Intune-administratör väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune** i [Azure-portalen](https://portal.azure.com).  I fönstret **Intune** väljer du **Enhetsregistrering**, > **Android for Work-registrering** och väljer sedan **Ta bort bindning**.

2. **Godkänn borttagningen av Android for Work-bindningen**<br>
  Välj **Ja** för att ta bort bindningen och avregistrera alla Android for Work-enheter från Intune.

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Slutanvändarens upplevelse när en Samsung Knox-enhet registreras
Det finns flera saker att tänka på vid registrering av Samsung Knox-enheter:
-   Även om inga principer kräver en PIN-kod, måste enheten ha en PIN-kod på minst fyra siffror för att kunna registreras. Om enheten inte har någon PIN-kod, uppmanas användaren att skapa en.
-   Det finns inga användaråtgärder för Workplace Join-certifikat (WPJ).
-   Användaren får information om tjänstregistreringen och om vad appen kan göra.
-   Användaren får information om Knox-registreringen och om vad Knox kan göra.
-   Om en krypteringsprincip tillämpas måste användarna ange ett avancerat lösenord på sex tecken som enhetens lösenord.
-   Det finns inga ytterligare användaruppmaningar att installera certifikat från en tjänst för åtkomst till företagsresurser.
- Vissa äldre Knox-enheter uppmanar användaren om ytterligare certifikat som används för åtkomst till företagsresurser.
- Om en Samsung Mini-enhet inte kan installera WPJ och får felet **Det gick inte att hitta certifikatet** eller **Det gick inte att registrera enheten**, installerar du de senaste uppdateringarna för inbyggd Samsung-programvara.
