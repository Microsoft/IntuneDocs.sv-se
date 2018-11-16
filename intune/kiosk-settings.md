---
title: Kioskinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera dina Windows 10-enheter (och senare) med helskärmsläget för enstaka och flera appar, inklusive att anpassa startmenyn, lägga till appar, aktivitetsfältet och konfigurera en webbläsare. Konfigurera även Windows Holographic for Business-enheter som kiosker med flera appar i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0d749d51f0ae146b68be8abb3a59a0504aea1180
ms.sourcegitcommit: cfce9318b5b5a3005929be6eab632038a12379c3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51298147"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Kioskinställningar för Windows 10 (och senare) i Intune

På Windows 10-enheter kan du använda Intune för att köra dessa enheter i helskärmsläge. Helskärmsläget kan köra en app eller flera appar. Du kan också visa och anpassa en startmeny, lägga till olika appar, inklusive Win32-appar, lägga till en viss startsida i en webbläsare och mycket mer. 

Använd stegen i den här artikeln för att skapa ett helskärmsläge för enstaka och flera appar i Intune.

Intune stöder en helskärmsprofil per enhet. Om du behöver flera helskärmsprofiler på en enskild enhet, kan du använda en [Anpassad OMA-URI](custom-settings-windows-10.md).

## <a name="kiosk-settings"></a>Kioskinställningar

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster**, filtrerar på **Intune** och väljer **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på den nya profilen.
   - **Beskrivning:** Ange en beskrivning för profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj **Windows 10 och senare**
   - **Profiltyp**: Välj **Helskärmsläge (förhandsgranskning)**

4. Välj ett **helskärmsläge**. **Helskärmsläge**: Identifierar den typ av kioskläge som stöds av principen. Alternativen är:

    - **Inte konfigurerad** (standard): Den här principen aktiverar inte helskärmsläge.
    - **Enskild app, helskärmsläge**: Enheten körs som ett enda användarkonto och låser det till en enda Store-app. När användaren loggar in startar alltså en specifik app. Det här läget gör också att användaren inte kan öppna nya appar eller ändra appen som körs.
    - **Helskärmsläge för flera appar**: Enheten kör flera Store-appar, Win32-appar eller inkorgens Windows-appar med hjälp av ett ID för programanvändarmodell (AUMID). Det är bara de appar som du lägger till som är tillgängliga på enheten.

        Med en kiosk för flera appar, eller en enhet för ett bestämt ändamål, skapas en mer användarvänlig upplevelse för användarna eftersom de endast ser de appar de behöver. Appar som de inte behöver visas inte.

## <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge
När du väljer helskärmsläge för enskilda appar kan du ange följande inställningar:

- **Användarens inloggningstyp**: De appar som du lägger till körs som det användarkonto du anger. Alternativen är:

  - **Automatisk inloggning (Windows 10 version 1803 och senare)**: För helskärmslägen i offentliga miljöer som inte kräver att användaren loggar in, vilket liknar ett gästkonto. Den här inställningen använder [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokalt användarkonto**: Ange det lokala (för enheten) användarkontot. Det konto som du anger används för att logga in i helskärmsläget.

- **Programtyp**: Välj **Store-app**.

- **App som körs i helskärmsläge**: Välj **Lägg till en Store-app** och välj en app i listan.

    Har du inte några appar i listan? Lägg till några med hjälp av anvisningarna i [Klientappar](apps-add.md).

    Klicka på **OK** för att spara ändringarna.

- **Kiosk Browser-inställningar**: Dessa inställningar styr en webbläsarapp i helskärmsläget. Se till att du får [Kiosk Browser-appen](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) från Store, lägg till den i Intune som en [Klientapp](apps-add.md) och tilldela sedan appen till enheter i helskärmsläge.

  Ange följande inställningar:

  - **Webbadress till standardhemsida**: Ange standard-URL:en som ska visas när Kiosk Browser öppnas eller när webbläsaren startas om. Ange till exempel `http://bing.com` eller `http://www.contoso.com`.

  - **Startknapp**: **Visa** eller **dölj** knappen på startsidan i webbläsaren på kioskenheten. Standardinställningen är att knappen inte visas.

  - **Navigeringsknappar**: **Visa** eller **dölj** framåt- och bakåtknapparna. Som standard visas inte navigeringsknapparna.

  - **Knapp för att avsluta sessionen**: **Visa** eller **dölj** knappen för att avsluta sessionen. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och öppnar sedan den webbadress som är standard. Standardinställningen är att knappen inte visas.

  - **Uppdatera webbläsaren efter viloläge**: Ange efter hur lång tids inaktivitet (1–1440 minuter) webbläsaren på kioskenheten ska startas om. Hur inaktivitetstiden är antalet minuter sedan den senaste interaktionen från en användare. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

  - **Tillåtna webbplatser**: Använd den här inställningen för att tillåta att vissa webbplatser öppnas. Med andra ord kan du använda denna funktion till att begränsa eller förhindra webbplatser på enheten. Du kan till exempel tillåta att alla webbplatser på `http://contoso.com*` öppnas. Som standard tillåts alla webbplatser.
 
      Ladda upp en fil som innehåller en lista med tillåtna webbplatser på separata rader om du vill tillåta specifika webbplatser. Om du inte lägger till någon fil tillåts alla webbplatser. Intune stöder * (asterisk) som jokertecken.

      Exempelfilen bör likna följande lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  Klicka på **OK** för att spara ändringarna.

## <a name="multi-app-kiosks"></a>Helskärmsläge för flera appar

Appar i det här läget är tillgängliga på startmenyn. De här apparna är de enda appar som användaren kan öppna.

När du väljer helskärmsläge för flera appar kan du ange följande inställningar:

- **Rikta in enheter med Windows 10 i S-läge**: Välj **Ja** för att tillåta Store-appar och AUMID-appar (omfattar ej Win32-appar) i kioskprofilen. Välj **Nej** för att tillåta Store-appar, Win32-appar och AUMID-appar i kioskprofilen. När du väljer **Nej** distribueras kioskprofilen inte till enheter i S-läge.

- **Användarens inloggningstyp**: De appar som du lägger till körs som det användarkonto du anger. Alternativen är:

  - **Automatisk inloggning (Windows 10 version 1803 och senare)**: För helskärmslägen i offentliga miljöer som inte kräver att användaren loggar in, vilket liknar ett gästkonto. Den här inställningen använder [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokalt användarkonto**: **Lägg till** det lokala användarkontot (för enheten). Det konto som du anger används för att logga in i helskärmsläget.
  - **Azure AD-användare eller grupp (Windows 10 version 1803 och senare)**: Välj **Lägg till** för att välja Azure AD-användare eller grupper i listan. Du kan välja flera användare och grupper. Välj **OK** för att spara ändringarna.
  - **HoloLens-besökare**: besökarkontot är ett gästkonto som inte kräver autentiseringsuppgifter eller autentisering, enligt beskrivningen i [begrepp om delat PC-läge](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Program**: Lägg till appar som ska köras på kioskenheten. Kom ihåg att du kan lägga till flera appar.

  - **Lägg till Store-app**: Lägg till en app från Microsoft Store för företag. Om du inte har några appar i listan kan du hämta appar och [lägga till dem i Intune](store-apps-windows.md). Du kan till exempel lägga till Kiosk Browser, Excel, OneNote etc.

  - **Lägg till Win32-App**: En Win32-app är en traditionell skrivbordsapp, till exempel Visual Studio Code eller Google Chrome. Ange följande egenskaper:

    - **Programnamn**: Krävs. Ange ett namn på programmet.
    - **Lokal sökväg**: Krävs. Ange sökvägen till den körbara filen, till exempel `C:\Program Files (x86)\Microsoft VS Code\Code.exe` eller `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **ID för programanvändarmodell (AUMID)**: Ange ID:t för programanvändarmodellen (AUMID) för Win32-appen. Den här inställningen avgör panelens startlayout på skrivbordet. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
    - **Panelstorlek**: Krävs. Välj storleken Liten, Medel, Bred eller Stor för appanelen.
  
  - **Lägg till via AUMID**: Använd det här alternativet för att lägga till inkorgens Windows-appar, till exempel Anteckningar eller Kalkylatorn. Ange följande egenskaper: 

    - **Programnamn**: Krävs. Ange ett namn på programmet.
    - **Appens programanvändarmodell ID (AUMID)**: Krävs. Ange appens programanvändarmodell-ID (AUMID) för Windows-appen. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Panelstorlek**: Krävs. Välj storleken Liten, Medel, Bred eller Stor för appanelen.

  > [!TIP]
  > När du har lagt till alla appar kan du ändra visningsordning genom att klicka och dra apparna i listan.  

  Klicka på **OK** för att spara ändringarna.

- **Kiosk Browser-inställningar**: Dessa inställningar styr en webbläsarapp i helskärmsläget. Kontrollera att du har distribuerat en webbläsarapp till kioskenheterna via [Klientappar](apps-add.md).

  Ange följande inställningar:

  - **Webbadress till standardhemsida**: Ange standard-URL:en som ska visas när Kiosk Browser öppnas eller när webbläsaren startas om. Ange till exempel `http://bing.com` eller `http://www.contoso.com`.

  - **Startknapp**: **Visa** eller **dölj** knappen på startsidan i webbläsaren på kioskenheten. Standardinställningen är att knappen inte visas.

  - **Navigeringsknappar**: **Visa** eller **dölj** framåt- och bakåtknapparna. Som standard visas inte navigeringsknapparna.

  - **Knapp för att avsluta sessionen**: **Visa** eller **dölj** knappen för att avsluta sessionen. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och öppnar sedan den webbadress som är standard. Standardinställningen är att knappen inte visas.

  - **Uppdatera webbläsaren efter viloläge**: Ange efter hur lång tids inaktivitet (1–1440 minuter) webbläsaren på kioskenheten ska startas om. Hur inaktivitetstiden är antalet minuter sedan den senaste interaktionen från en användare. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

  - **Tillåtna webbplatser**: Använd den här inställningen för att tillåta att vissa webbplatser öppnas. Med andra ord kan du använda denna funktion till att begränsa eller förhindra webbplatser på enheten. Du kan till exempel tillåta att alla webbplatser på `contoso.com*` öppnas. Som standard tillåts alla webbplatser.

    Ladda upp en .csv-fil som innehåller en lista med tillåtna webbplatser om du vill tillåta specifika webbplatser. Om du inte lägger till någon .csv-fil tillåts alla webbplatser.

  Klicka på **OK** för att spara ändringarna.

- **Använd alternativ startlayout**: Välj **Ja** för att ange en XML-fil som beskriver hur apparna ska visas på startmenyn, inklusive apparnas inbördes ordning. Använd det här alternativet om du behöver anpassa mer på startmenyn. [Anpassa och exportera Start-layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) innehåller viss vägledning och XML-exempel.

- **Aktivitetsfältet**: Välj att **visa** eller **dölja** aktivitetsfältet. Standardinställningen är att aktivitetsfältet inte visas.

## <a name="windows-holographic-for-business"></a>Windows 10 Holographic for Business

På Windows Holographic for Business-enheter kan du konfigurera enheterna att köra i helskärmsläge för en enskild app eller helskärmsläge för flera appar. Vissa funktioner stöds inte i Windows Holographic for Business.

#### <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge
När du väljer helskärmsläge för enskilda appar kan du ange följande inställningar:

- **Användarens inloggningstyp**: Välj **Lokalt användarkonto** för att ange det lokala användarkontot (för enheten) eller ett Microsoft-konto som är associerat med kioskappen. Användarkontotyper med **Automatisk inloggning** stöds inte på Windows Holographic for Business.

- **Programtyp**: Välj **Store-app**.

- **App som körs i helskärmsläge**: Välj **Lägg till en Store-app** och välj en app i listan.

    Har du inte några appar i listan? Lägg till några med hjälp av anvisningarna i [Klientappar](apps-add.md).

    Klicka på **OK** för att spara ändringarna.

#### <a name="multi-app-kiosks"></a>Helskärmsläge för flera appar
Appar i det här läget är tillgängliga på startmenyn. De här apparna är de enda appar som användaren kan öppna. När du väljer helskärmsläge för flera appar kan du ange följande inställningar:

- **Rikta in enheter med Windows 10 i S-läge**: Välj **Nej**. S-läge stöds inte i Windows Holographic for Business.

- **Användarens inloggningstyp**: Lägg till ett eller flera användarkonton som kan använda de appar som du lägger till. Alternativen är: 

  - **Automatisk inloggning**: Stöds inte i Windows Holographic for Business.
  - **Lokala användarkonton**: **Lägg till** det lokala användarkontot (för enheten). Det konto som du anger används för att logga in i helskärmsläget.
  - **Azure AD-användare eller grupp (Windows 10, version 1803 och senare)**: Kräver autentiseringsuppgifter för att kunna logga in på enheten. Välj **Lägg till** för att välja Azure AD-användare eller grupper i listan. Du kan välja flera användare och grupper. Välj **OK** för att spara ändringarna.
  - **HoloLens-besökare**: besökarkontot är ett gästkonto som inte kräver autentiseringsuppgifter eller autentisering, enligt beskrivningen i [begrepp om delat PC-läge](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Program**: Lägg till appar som ska köras på kioskenheten. Kom ihåg att du kan lägga till flera appar.

  - **Lägg till Store-appar**: Välj en befintlig app som du har lagt till via [Klientappar](apps-add.md). Om du inte har några appar i listan kan du hämta appar och [lägga till dem i Intune](store-apps-windows.md).
  - **Lägg till Win32-app**: Stöds inte i Windows Holographic for Business.
  - **Lägg till via AUMID**: Använd det här alternativet för att lägga till inkorgens Windows-appar. Ange följande egenskaper: 

    - **Programnamn**: Krävs. Ange ett namn på programmet.
    - **Appens programanvändarmodell ID (AUMID)**: Krävs. Ange appens programanvändarmodell-ID (AUMID) för Windows-appen. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Panelstorlek**: Krävs. Välj storleken Liten, Medel, Bred eller Stor för appanelen.

- **Kiosk Browser-inställningar**: Stöds inte i Windows Holographic for Business.

- **Använd alternativ startlayout**: Välj **Ja** för att ange en XML-fil som beskriver hur apparna ska visas på startmenyn, inklusive apparnas inbördes ordning. Använd det här alternativet om du behöver anpassa mer på startmenyn. [Anpassa och exportera Start-layout](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) ger viss vägledning och innehåller en specifik XML-fil för Windows Holographic for Business-enheter.

- **Aktivitetsfältet**: Stöds inte i Windows Holographic for Business.



## <a name="next-steps"></a>Nästa steg
[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
