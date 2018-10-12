---
title: Kioskinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera dina Windows 10-enheter (och senare) som kiosker med en enskild app och flera appar, inklusive anpassning av Start-menyn, lägga till appar, aktivitetsfältet och konfigurera en webbläsare. Konfigurera även Windows Holographic for Business-enheter som kiosker med flera appar i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9dd7608981da1454c1f3be29eb6ff40a5d7f3394
ms.sourcegitcommit: 23adbc50191f68c4b66ea845a044da19c659ac84
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45562875"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Kioskinställningar för Windows 10 (och senare) i Intune

Kioskprofiler används för att konfigurera Windows 10-enheter att köra en enda app eller flera appar. När du skapar en kioskprofil väljer du också om en startmeny ska visas, om en webbläsare ska finnas installerad och mer.

## <a name="kiosk-settings"></a>Kioskinställningar

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster**, filtrerar på **Intune** och väljer **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning:** Ange en beskrivning för profilen. Detta är valfritt, men rekommenderas.
   - **Plattform**: Välj **Windows 10 och senare**
   - **Profiltyp**: Välj **Helskärmsläge (förhandsgranskning)**
   
4. Välj **Helskärmsläge** > **Lägg till**.
5. Ange **Namn på kioskkonfiguration** för kiosken. Det här namnet specificerar en grupp med program, apparnas layout på startmenyn och de användare som associeras med kioskkonfigurationen.
6. Välj **Kioskläge**. **Helskärmsläge**: Identifierar den typ av kioskläge som stöds av principen. Alternativen är:

    - **Inte konfigurerad** (standard): Den här principen aktiverar inte helskärmsläge.
    - **Enstaka helskärmsapp för kioskenhet**: Den här profilen gör att enheten kan köras som ett enda användarkonto och begränsar den till en enda UWP-app (Universal Windows-plattform). När användaren loggar in startar alltså en specifik app. Det här läget gör också att användaren inte kan öppna nya appar eller ändra appen som körs.
    - **Flerappsläge för kiosk**: Den här profilen gör att enheten kan köra flera UWP-appar (Universal Windows-plattform), eller Win32-appar. Du kan också tilldela olika appar till olika användarkonton. Endast de appar som du lägger till är tillgängliga för användarna. Med en kiosk för flera appar, eller en enhet för ett bestämt ändamål, skapas en mer användarvänlig upplevelse för användarna eftersom de endast ser de appar de behöver. Appar som de inte behöver visas inte.

#### <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge
Ange följande inställningar:

- **ID för UWP-app (Universal Windows Platform)**: Ange kioskappens **programanvändarmodell-ID (AUMID)**. Du kan också välja en befintlig hanterad app som du har lagt till via [Client Apps](apps-add.md).

    Läs mer i informationen om att [hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

- **Användarkontotyp**: Du kan välja mellan följande alternativ:

  - **Automatisk inloggning**: För kiosker i offentliga miljöer bör en användartyp med minsta privilegier (till exempel det lokala standardanvändarkontot) användas. Om du konfigurerar ett Azure Active Directory-konto (AD) för helskärmsläge använder du formatet `AzureAD\user@contoso.com`.
  - **Lokalt användarkonto**: Ange det (för enheten) lokala användarkontot eller den Azure AD-kontoinloggning som är associerad med kioskappen. För konton som är kopplade till Azure AD-domäner ska kontot anges i formatet `domain\username@tenant.org`.

#### <a name="multi-app-kiosks"></a>Helskärmsläge för flera appar
Appar i det här läget är tillgängliga på Start-menyn. De här apparna är de enda appar som användaren kan öppna. 

I [helskärmsläget för flera appar](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune) används en helskärmskonfiguration som visar tillåtna appar och andra inställningar.

Ange följande inställningar:

- **Lägg till Win32-app**: En Win32-app är en traditionell skrivbordsapp. Ange **Appnamn** och **Identifierare**. **Identifieraren** är den fullständigt kvalificerade sökvägen till den körbara filen, i relation till enheten.
- **Lägg till hanterade appar**: Välj en befintlig hanterad app som du har lagt till via [Client Apps i Intune](apps-add.md).
- **Lägg till app via AUMID**: Ange [appens AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP-appar).
- **Aktivitetsfältet** – Välj **Aktivera** (visa) Aktivitetsfältet eller **Inte konfigurerad** (dölj) i helskärmsläget.
- **Startmenylayout**: Ange en XML-fil som beskriver hur apparna ska visas på Start-menyn, inklusive apparnas inbördes ordning. [Anpassa och exportera Start-layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) innehåller viss vägledning och XML-exempel.

  I [Create a Windows 10 kiosk that runs multiple apps](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file) (Skapa ett Windows 10-helskärmsläge som kör flera appar) finns mer information om hur du använder och skapar XML-filer.

- **Startmenylayout**: Lägg till ett eller flera användarkonton som kan använda de appar som du lägger till. När användaren med kontot loggar in är bara de appar som definierats i konfigurationen tillgängliga. Kontot kan vara lokalt på enheten eller en Azure AD-kontoinloggning som är associerad med kioskappen.

    För kiosker i offentliga miljöer med automatisk inloggning bör en användartyp med minsta privilegier (till exempel det lokala standardanvändarkontot) användas. Om du konfigurerar ett Azure Active Directory-konto (AD) för helskärmsläge använder du formatet `domain\user@tenant.com`.

## <a name="kiosk-web-browser-settings"></a>Webbläsarinställningar för kioskenhet

Dessa inställningar definierar hur en webbläsare visas på kioskenheten. Kontrollera att du har distribuerat en webbläsare till kioskenheterna via [Client Apps](apps-add.md).

1. Ange följande inställningar:

    - **Webbadress till standardhemsida**: Ange standard-URL:en som ska öppnas i webbläsaren på kioskenheten när webbläsaren öppnas eller startar om.

    - **Startknapp**: Visa (**Tillåt**) eller dölj (**Ej konfigurerad**) knappen för startsidan i webbläsaren på kioskenheten. Standardinställningen för knappen är Ej konfigurerad.

    - **Navigeringsknapp**: Visa (**Tillåt**) eller dölj (**Ej konfigurerad**) knapparna Framåt och Bakåt. Standardinställningen för navigeringsknapparna är Ej konfigurerad.

    - **Knappen Avsluta session**: Visa (**Tillåt**) eller dölj (**Ej konfigurerad**) knappen för att avsluta session. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och går tillbaka till den webbadress som är standard. Standardinställningen för knappen är Ej konfigurerad. 

    - **Uppdatera webbläsaren när användaren överskrider gränsen för inaktivitet**: Ange efter hur lång tids inaktivitet i antal minuter som webbläsaren på kioskenheten ska starta om. Värdet är ett heltal mellan 1 och 1 440 minuter. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

    - **Blockerade webbplatser**: Lista över blockerade webbplats-URL:er (jokertecken stöds). Använd den här inställningen om du vill förhindra att webbläsaren öppnar specifika platser. Du kan också **importera** en CSV-fil som innehåller en lista. Alternativt skapar du en CSV-fil (**exportera**) som innehåller de platser som du lägger till.

    - **Webbplatsundantag**: Lista över undantag till blockerade webbplats-URL:er (jokertecken stöds). Använd den här inställningen om du vill tillåta att specifika webbplatser öppnas i webbläsaren. Dessa undantag utgör en deluppsättning av de blockerade URL:erna. Om en URL finns med i listan över blockerade webbplatser och i listan med webbplatsundantag, gäller undantaget.

    Du kan också **importera** en CSV-fil som innehåller en lista. Alternativt skapar du en CSV-fil (**exportera**) som innehåller de platser som du lägger till.

2. Klicka på **OK** för att spara ändringarna.

## <a name="windows-holographic-for-business"></a>Windows 10 Holographic for Business

På Windows Holographic for Business-enheter kan du konfigurera enheterna att köra i helskärmsläge för en enskild app eller helskärmsläge för flera appar. 

#### <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge
Ange följande inställningar:

- **ID för UWP-app (Universal Windows Platform)**: Ange kioskappens **programanvändarmodell-ID (AUMID)**. Du kan också välja en befintlig hanterad app som du har lagt till via [Mobile Apps](apps-add.md).

    Information om hur du hittar ID finns i [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Hitta programanvändarmodell-ID för en installerad app).

- **Användarkontotyp**: Välj **Lokalt användarkonto** för att ange det (för enheten) lokala användarkontot eller en Microsoft-kontoinloggning (MSA) som är associerad med kioskappen. Användarkontotyper med **Automatisk inloggning** stöds inte på Windows Holographic for Business.

#### <a name="multi-app-kiosks"></a>Helskärmsläge för flera appar
Appar i det här läget är tillgängliga på Start-menyn. De här apparna är de enda appar som användaren kan öppna.

Ange följande inställningar:

- **Lägg till hanterade appar**: Välj en befintlig hanterad app som du har lagt till via [Client Apps i Intune](apps-add.md).
- **Lägg till app via AUMID**: Ange [appens AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (UWP-appar).
- **Startmenylayout**: Ange en XML-fil som beskriver hur apparna ska visas på Start-menyn, inklusive apparnas inbördes ordning. [Anpassa och exportera Start-layout](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) ger viss vägledning och innehåller en specifik XML-fil för Windows Holographic for Business-enheter.
- **Startmenylayout**: Lägg till ett eller flera användarkonton som kan använda de appar som du lägger till. Alternativ som stöds är: 
  - **HoloLens-besökare**: besökarkontot är ett gästkonto som inte kräver autentiseringsuppgifter eller autentisering, enligt beskrivningen i [begrepp om delat PC-läge](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).
  - **Azure AD-användare**: Kräver autentiseringsuppgifter för inloggning på enheten. Använd formatet `domain\user@tenant.com`.
  - **Lokala användarkonton**: Kräver autentiseringsuppgifter för inloggning på enheten. 

När användaren med kontot loggar in är bara de appar som definierats i konfigurationen tillgängliga.

## <a name="next-steps"></a>Nästa steg
[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
