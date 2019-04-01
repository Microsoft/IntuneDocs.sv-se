---
title: Kioskinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera dina enheter som kör Windows 10 (eller senare) med helskärmsläget för en app eller flera appar, anpassa startmenyn, lägg till appar, visa aktivitetsfältet och konfigurera en webbläsare i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/11/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55a0cb45cd3e3a8e367b0bff7bd8e856b02af953
ms.sourcegitcommit: aab39bf86707ccaef45fd6527fff4f1c89336710
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/25/2019
ms.locfileid: "58429699"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge i Intune

På enheter som kör Windows 10 (och senare) kan du konfigurera att enheterna körs i helskärmsläge för en enskild app eller helskärmsläge för flera appar.

Den här artikeln beskriver de olika inställningar som du kan styra på enheter med Windows 10 och senare. I din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar till att konfigurera att dina enheter med Windows 10 (och senare) körs i helskärmsläge.

Som Intune-administratör kan du skapa och tilldela dessa inställningar till dina enheter.

Mer information om Windows helskärmsfunktion i Intune finns i [Konfigurera inställningar för helskärmsläge](kiosk-settings.md).

## <a name="before-you-begin"></a>Innan du börjar

- [Skapa profilen](kiosk-settings.md#create-the-profile).

- Den här kioskprofilen är direkt relaterad till profilen för enhetsbegränsningar du skapar med den [Microsoft Edge-inställningar för helskärmsläge](device-restrictions-windows-10.md#microsoft-edge-browser). Sammanfattningsvis:

  1. Skapa den här kioskprofilen för att köra enheten i helskärmsläge.
  2. Skapa den [enhetsbegränsningsprofil](device-restrictions-windows-10.md#microsoft-edge-browser), och konfigurera specifika funktioner och inställningar i Microsoft Edge.

> [!IMPORTANT] 
> Se till att tilldela den här kioskprofilen till samma enheter som din [Microsoft Edge-profilen](device-restrictions-windows-10.md#microsoft-edge-browser).

## <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge

Kör endast en app på enheten.

- **Välj ett helskärmsläge**: Välj **enskild app, helskärmsläge helskärmsläge**.

- **Användarens inloggningstyp**: De appar som du lägger till körs som det användarkonto du anger. Alternativen är:

  - **Automatisk inloggning (Windows 10 version 1803 och senare)**: Använd i helskärmslägen i offentliga miljöer som inte kräver att användaren loggar in, vilket liknar ett gästkonto. Den här inställningen använder [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokalt användarkonto**: Ange det lokala (för enheten) användarkontot. Det konto som du anger loggar in till kiosken.

- **Programtyp**: Välj vilken typ av program. Alternativen är:

  - **Lägg till Microsoft Edge-webbläsaren**: Välj **Microsoft Edge-webbläsaren**, och välj den **Edge-helskärmsläge läge typ**:

    - **Digital/interaktiv signering**: öppnar en fullständig URL-skärmen och visar bara innehållet på webbplatsen. [Ställ in digitala loggar](https://docs.microsoft.com/windows/configuration/setup-digital-signage) finns mer information om den här funktionen.
    - **Offentliga surfning (InPrivate)**: kör en begränsad flera fliken version av Microsoft Edge. Användare kan bläddra offentligt eller avslutar sin session.

    Mer information om dessa alternativ finns i [distribuera Microsoft Edge helskärmsläge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

    > [!NOTE]
    > Den här inställningen gör det möjligt för Microsoft Edge-webbläsaren på enheten. För att konfigurera Microsoft Edge-specifika inställningar, skapa en profil för enhetskonfiguration (**enhetskonfiguration** > **profiler** > **skapa profil**  >  **Windows 10** för plattform > **Enhetsbegränsningar** >  **Microsoft Edge-webbläsaren**). [Microsoft Edge-webbläsaren](device-restrictions-windows-10.md#microsoft-edge-browser) listas och beskrivs de tillgängliga inställningarna.

    Klicka på **OK** för att spara ändringarna.

  - **Lägg till helskärmsläge webbläsare**: Välj **helskärmsläge webbläsarinställningar**. Dessa inställningar definierar hur en webbläsare visas på kioskenheten. Se till att du får [Kiosk Browser-appen](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) från Store, lägg till den i Intune som en [Klientapp](apps-add.md) och tilldela sedan appen till enheter i helskärmsläge.

    Ange följande inställningar:

    - **Webbadress till standardhemsida**: Ange standard-URL:en som ska visas när Kiosk Browser öppnas eller när webbläsaren startas om. Ange till exempel `http://bing.com` eller `http://www.contoso.com`.

    - **Startknapp**: **Visa** eller **dölj** knappen på startsidan i webbläsaren på kioskenheten. Standardinställningen är att knappen inte visas.

    - **Navigeringsknappar**: **Visa** eller **dölj** framåt- och bakåtknapparna. Som standard visas inte navigeringsknapparna.

    - **Knapp för att avsluta sessionen**: **Visa** eller **dölj** knappen för att avsluta sessionen. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och öppnar sedan den webbadress som är standard. Standardinställningen är att knappen inte visas.

    - **Uppdatera webbläsaren efter viloläge**: Ange efter hur lång tids inaktivitet (1–1440 minuter) webbläsaren på kioskenheten ska startas om. Hur inaktivitetstiden är antalet minuter sedan den senaste interaktionen från en användare. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

    - **Tillåtna webbplatser**: Använd den här inställningen för att tillåta att vissa webbplatser öppnas. Med andra ord kan du använda denna funktion till att begränsa eller förhindra webbplatser på enheten. Du kan till exempel tillåta att alla webbplatser på `http://contoso.com*` öppnas. Som standard tillåts alla webbplatser.

      Ladda upp en fil som innehåller en lista med tillåtna webbplatser på separata rader om du vill tillåta specifika webbplatser. Om du inte lägger till någon fil tillåts alla webbplatser. Intune stöder `*` (asterisk) som jokertecken.

      Exempelfilen bör likna följande lista:

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

    Klicka på **OK** för att spara ändringarna.

  - **Lägg till Store-app**: Välj **lägga till en store-app**, och välj en app i listan.

    Har du inte några appar i listan? Lägg till några med hjälp av anvisningarna i [Klientappar](apps-add.md).

  Klicka på **OK** för att spara ändringarna.

## <a name="multi-app-kiosks"></a>Helskärmsläge för flera appar

Appar i det här läget är tillgängliga på startmenyn. De här apparna är de enda appar som användaren kan öppna. Om en app har ett beroende på en annan app, måste båda vara med i listan över tillåtna appar. Internet Explorer 64-bitars har ett beroende på Internet Explorer 32-bitars, så du måste tillåta både ”C:\Program c:\Program\Internet explorer\iexplore.exe” och ”C:\Program Files (x86) \Internet Explorer\iexplore.exe”. 

- **Välj ett helskärmsläge**: Välj **Flerappsläge för kiosk**.

- **Rikta in enheter med Windows 10 i S-läge**:
  - **Ja**: Tillåter Store-appar och AUMID-appar (förutom Win32-appar) i kioskprofilen.
  - **Nej**: Tillåta Store-appar, Win32-appar och AUMID-appar i kioskprofilen. Den här kioskprofilen inte är distribuerat till enheter för S-läge.

- **Användarens inloggningstyp**: De appar som du lägger till körs som det användarkonto du anger. Alternativen är:

  - **Automatisk inloggning (Windows 10 version 1803 och senare)**: Använd i helskärmslägen i offentliga miljöer som inte kräver att användaren loggar in, vilket liknar ett gästkonto. Den här inställningen använder [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokalt användarkonto**: **Lägg till** det lokala användarkontot (för enheten). Det konto som du anger loggar in till kiosken.
  - **Azure AD-användare eller grupp (Windows 10 version 1803 och senare)**: Välj **Lägg till** och välj Azure AD-användare eller grupper i listan. Du kan välja flera användare och grupper. Välj **OK** för att spara ändringarna.
  - **HoloLens-besökare**: besökarkontot är ett gästkonto som inte kräver autentiseringsuppgifter eller autentisering, enligt beskrivningen i [begrepp om delat PC-läge](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Webbläsare och program**: Lägg till de appar som ska köras på kioskenheten. Kom ihåg att du kan lägga till flera appar.

  - **Webbläsare**

    - **Lägg till Microsoft Edge**: Microsoft Edge har lagts till i rutnätet app och alla program kan köras på den här helskärmsläge. Välj den **Microsoft Edge helskärmsläge läge typ**:

      - **Normalt läge (fullständig version av Microsoft Edge)**: kör en fullständig version av Microsoft Edge med alla webbläsarens funktioner. Användardata och tillstånd sparas mellan sessioner.
      - **Offentliga surfning (InPrivate)**: kör en flera fliken version av Microsoft Edge InPrivate med en anpassad upplevelse för informationsdatorer som kör i helskärmsläge.

      Mer information om dessa alternativ finns i [distribuera Microsoft Edge helskärmsläge](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types).

      > [!NOTE]
      > Den här inställningen gör det möjligt för Microsoft Edge-webbläsaren på enheten. För att konfigurera Microsoft Edge-specifika inställningar, skapa en profil för enhetskonfiguration (**enhetskonfiguration** > **profiler** > **skapa profil**  >  **Windows 10** för plattform > **Enhetsbegränsningar** >  **Microsoft Edge-webbläsaren**). [Microsoft Edge-webbläsaren](device-restrictions-windows-10.md#microsoft-edge-browser) listas och beskrivs de tillgängliga inställningarna.

      Klicka på **OK** för att spara ändringarna.

    - **Lägg till Kiosk-webbläsare**: Dessa inställningar styr en webbläsarapp i helskärmsläget. Kontrollera att du har distribuerat en webbläsarapp till kioskenheterna via [Klientappar](apps-add.md).

      Ange följande inställningar:

      - **Webbadress till standardhemsida**: Ange standard-URL:en som ska visas när Kiosk Browser öppnas eller när webbläsaren startas om. Ange till exempel `http://bing.com` eller `http://www.contoso.com`.

      - **Startknapp**: **Visa** eller **dölj** knappen på startsidan i webbläsaren på kioskenheten. Standardinställningen är att knappen inte visas.

      - **Navigeringsknappar**: **Visa** eller **dölj** framåt- och bakåtknapparna. Som standard visas inte navigeringsknapparna.

      - **Knapp för att avsluta sessionen**: **Visa** eller **dölj** knappen för att avsluta sessionen. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och öppnar sedan den webbadress som är standard. Standardinställningen är att knappen inte visas.

      - **Uppdatera webbläsaren efter viloläge**: Ange efter hur lång tids inaktivitet (1–1440 minuter) webbläsaren på kioskenheten ska startas om. Hur inaktivitetstiden är antalet minuter sedan den senaste interaktionen från en användare. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

      - **Tillåtna webbplatser**: Använd den här inställningen för att tillåta att vissa webbplatser öppnas. Med andra ord kan du använda denna funktion till att begränsa eller förhindra webbplatser på enheten. Du kan till exempel tillåta att alla webbplatser på `contoso.com*` öppnas. Som standard tillåts alla webbplatser.

        Ladda upp en .csv-fil som innehåller en lista med tillåtna webbplatser om du vill tillåta specifika webbplatser. Om du inte lägger till någon .csv-fil tillåts alla webbplatser.

      Klicka på **OK** för att spara ändringarna.

  - **Program**

    - **Lägg till Store-app**: Lägg till en app från Microsoft Store för företag. Om du inte har några appar i listan kan du hämta appar och [lägga till dem i Intune](store-apps-windows.md). Du kan till exempel lägga till Kiosk Browser, Excel, OneNote etc.

      Klicka på **OK** för att spara ändringarna.

    - **Lägg till Win32-App**: En Win32-app är en traditionell skrivbordsapp, till exempel Visual Studio Code eller Google Chrome. Ange följande egenskaper:

      - **Programnamn**: Krävs. Ange ett namn på programmet.
      - **Lokal sökväg**: Krävs. Ange sökvägen till den körbara filen, till exempel `C:\Program Files (x86)\Microsoft VS Code\Code.exe` eller `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
      - **ID för programanvändarmodell (AUMID)**: Ange ID:t för programanvändarmodellen (AUMID) för Win32-appen. Den här inställningen avgör panelens startlayout på skrivbordet. Se [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps) för hur du hämtar detta ID.

      Klicka på **OK** för att spara ändringarna.

    - **Lägg till via AUMID**: Använd det här alternativet för att lägga till inkorgens Windows-appar, till exempel Anteckningar eller Kalkylatorn. Ange följande egenskaper:

      - **Programnamn**: Krävs. Ange ett namn på programmet.
      - **Appens programanvändarmodell ID (AUMID)**: Krävs. Ange appens programanvändarmodell-ID (AUMID) för Windows-appen. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).

      Klicka på **OK** för att spara ändringarna.

    - **AutoLaunch**: valfritt. Välj ett program till AutoLaunch när användaren loggar in. Endast en enda app kan vara AutoLaunched.
    - **Panelstorlek**: Krävs. Välj storleken Liten, Medel, Bred eller Stor för appanelen.

  > [!TIP]
  > När du har lagt till alla appar kan du ändra visningsordning genom att klicka och dra apparna i listan.  

- **Använd alternativ startlayout**: Välj **Ja** för att ange en XML-fil som beskriver hur apparna ska visas på startmenyn, inklusive apparnas inbördes ordning. Använd det här alternativet om du behöver anpassa mer på startmenyn. [Anpassa och exportera Start-layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) innehåller viss vägledning och XML-exempel.

- **Aktivitetsfältet**: Välj att **visa** eller **dölja** aktivitetsfältet. Standardinställningen är att aktivitetsfältet inte visas. Ikoner som exempelvis Wi-Fi-ikonen visas, men inställningarna kan inte ändras av slutanvändarna.

- **Tillåt åtkomst till hämtar mappen**: Välj **Ja** så att användarna kan komma åt mappen hämtade filer i Windows Explorer. Åtkomst till mappen hämtade filer är inaktiverad som standard. Den här funktionen används ofta för slutanvändare för att få tillgång till objekt som hämtats från en webbläsare.

Klicka på **OK** för att spara ändringarna.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa helskärmsprofiler för [Android](device-restrictions-android.md#kiosk)-, [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)- och [Windows Holographic for Business](kiosk-settings-holographic.md)-enheter.
