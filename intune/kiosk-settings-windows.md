---
title: Kioskinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera dina enheter som kör Windows 10 (eller senare) med helskärmsläget för en app eller flera appar, anpassa startmenyn, lägg till appar, visa aktivitetsfältet och konfigurera en webbläsare i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 61cb1a3c9de10020381d62a2a7795d5ff728db22
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199429"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Inställningar för enheter med Windows 10 (och senare) som ska köras med helskärmsläge i Intune

På enheter som kör Windows 10 (och senare) kan du konfigurera att enheterna körs i helskärmsläge för en enskild app eller helskärmsläge för flera appar.

Den här artikeln beskriver de olika inställningar som du kan styra på enheter med Windows 10 och senare. I din MDM-lösning (hantering av mobilenheter) använder du dessa inställningar till att konfigurera att dina enheter med Windows 10 (och senare) körs i helskärmsläge.

Som Intune-administratör kan du skapa och tilldela dessa inställningar till dina enheter.

Mer information om Windows helskärmsfunktion i Intune finns i [Konfigurera inställningar för helskärmsläge](kiosk-settings.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa profilen](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge

När du väljer helskärmsläge för enskilda appar kan du ange följande inställningar:

- **Typ av användarinloggning**: De appar som du lägger till körs som det användarkonto du anger. Alternativen är:

  - **Automatisk inloggning (Windows 10 version 1803 och senare)**: För kioskenheter i offentliga miljöer som inte kräver att användaren loggar in, ungefär som ett gästkonto. Den här inställningen använder [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokalt användarkonto**: Ange det lokala användarkontot (för enheten). Det konto som du anger används för att logga in i helskärmsläget.

- **Programtyp**: Välj **Store-app**.

- **App som ska köras i helskärmsläge**: Välj **Lägg till en Store-app** och välj en app i listan.

    Har du inte några appar i listan? Lägg till några med hjälp av anvisningarna i [Klientappar](apps-add.md).

    Klicka på **OK** för att spara ändringarna.

- **Kiosk Browser-inställningar**: Dessa inställningar definierar hur en webbläsare visas på kioskenheten. Se till att du får [Kiosk Browser-appen](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) från Store, lägg till den i Intune som en [Klientapp](apps-add.md) och tilldela sedan appen till enheter i helskärmsläge.

  Ange följande inställningar:

  - **Webbadress till standardhemsida**: Ange standard-URL:en som ska visas när Kiosk Browser öppnas eller när webbläsaren startas om. Ange till exempel `http://bing.com` eller `http://www.contoso.com`.

  - **Startknapp**: **Visa** eller **dölj** knappen på startsidan i webbläsaren på kioskenheten. Standardinställningen är att knappen inte visas.

  - **Navigeringsknappar**: **Visa** eller **dölj** framåt- och bakåtknappen. Som standard visas inte navigeringsknapparna.

  - **Avsluta session-knapp**: **Visa** eller **dölj** knappen för att avsluta session. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och öppnar sedan den webbadress som är standard. Standardinställningen är att knappen inte visas.

  - **Uppdatera webbläsaren efter inaktivitetstid**: Ange hur lång inaktivitetstiden (1–1 440 minuter) ska vara innan kioskenhetens webbläsare startar om med ny status. Hur inaktivitetstiden är antalet minuter sedan den senaste interaktionen från en användare. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

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

- **Rikta in enheter med Windows 10 i S-läge**: Välj **Ja** för att tillåta Store-appar och AUMID-appar (exkluderar Win32-appar) i kioskprofilen. Välj **Nej** för att tillåta Store-appar, Win32-appar och AUMID-appar i kioskprofilen. När du väljer **Nej** distribueras kioskprofilen inte till enheter i S-läge.

- **Typ av användarinloggning**: De appar som du lägger till körs som det användarkonto du anger. Alternativen är:

  - **Automatisk inloggning (Windows 10 version 1803 och senare)**: För kioskenheter i offentliga miljöer som inte kräver att användaren loggar in, ungefär som ett gästkonto. Den här inställningen använder [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp).
  - **Lokalt användarkonto**: **Lägg till** det lokala användarkontot (för enheten). Det konto som du anger används för att logga in i helskärmsläget.
  - **Azure AD-användare eller -grupp (Windows 10 version 1803 och senare)**: Välj **Lägg till** för att välja Azure AD-användare eller grupper i listan. Du kan välja flera användare och grupper. Välj **OK** för att spara ändringarna.
  - **HoloLens-besökare**: Besökarkontot är ett gästkonto som inte kräver autentiseringsuppgifter eller autentisering, enligt beskrivningen i [begrepp om delat PC-läge](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Program**: Lägg till appar som ska köras på kioskenheten. Kom ihåg att du kan lägga till flera appar.

  - **Lägg till Store-app**: Lägg till en app från Microsoft Store för företag. Om du inte har några appar i listan kan du hämta appar och [lägga till dem i Intune](store-apps-windows.md). Du kan till exempel lägga till Kiosk Browser, Excel, OneNote etc.

  - **Lägg till Win32-App**: En Win32-app är en traditionell skrivbordsapp, till exempel Visual Studio Code eller Google Chrome. Ange följande egenskaper:

    - **Programnamn**: Obligatoriskt. Ange ett namn på programmet.
    - **Lokal sökväg**: Obligatoriskt. Ange sökvägen till den körbara filen, till exempel `C:\Program Files (x86)\Microsoft VS Code\Code.exe` eller `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`.
    - **ID för programanvändarmodell (AUMID)**: Ange ID för programanvändarmodellen (AUMID) för Win32-appen. Den här inställningen avgör panelens startlayout på skrivbordet. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps).
    - **Panelstorlek**: Obligatoriskt. Välj storleken Liten, Medel, Bred eller Stor för appanelen.
  
  - **Lägg till via AUMID**: Använd det här alternativet för att lägga till inkorgens Windows-appar, till exempel Anteckningar eller Kalkylatorn. Ange följande egenskaper: 

    - **Programnamn**: Obligatoriskt. Ange ett namn på programmet.
    - **ID för programanvändarmodell (AUMID)**: Obligatoriskt. Ange appens programanvändarmodell-ID (AUMID) för Windows-appen. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Panelstorlek**: Obligatoriskt. Välj storleken Liten, Medel, Bred eller Stor för appanelen.

  > [!TIP]
  > När du har lagt till alla appar kan du ändra visningsordning genom att klicka och dra apparna i listan.  

  Klicka på **OK** för att spara ändringarna.

- **Kiosk Browser-inställningar**: Dessa inställningar definierar hur en webbläsare visas på kioskenheten. Kontrollera att du har distribuerat en webbläsarapp till kioskenheterna via [Klientappar](apps-add.md).

  Ange följande inställningar:

  - **Webbadress till standardhemsida**: Ange standard-URL:en som ska visas när Kiosk Browser öppnas eller när webbläsaren startas om. Ange till exempel `http://bing.com` eller `http://www.contoso.com`.

  - **Startknapp**: **Visa** eller **dölj** knappen på startsidan i webbläsaren på kioskenheten. Standardinställningen är att knappen inte visas.

  - **Navigeringsknappar**: **Visa** eller **dölj** framåt- och bakåtknappen. Som standard visas inte navigeringsknapparna.

  - **Avsluta session-knapp**: **Visa** eller **dölj** knappen för att avsluta session. När det här visas väljer användaren knappen så uppmanar appen om att avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata (cookies, cache och så vidare) och öppnar sedan den webbadress som är standard. Standardinställningen är att knappen inte visas.

  - **Uppdatera webbläsaren efter inaktivitetstid**: Ange hur lång inaktivitetstiden (1–1 440 minuter) ska vara innan kioskenhetens webbläsare startar om med ny status. Hur inaktivitetstiden är antalet minuter sedan den senaste interaktionen från en användare. Värdet är tomt som standard, vilket innebär att det inte finns någon tidsgräns för inaktivitet.

  - **Tillåtna webbplatser**: Använd den här inställningen för att tillåta att vissa webbplatser öppnas. Med andra ord kan du använda denna funktion till att begränsa eller förhindra webbplatser på enheten. Du kan till exempel tillåta att alla webbplatser på `contoso.com*` öppnas. Som standard tillåts alla webbplatser.

    Ladda upp en .csv-fil som innehåller en lista med tillåtna webbplatser om du vill tillåta specifika webbplatser. Om du inte lägger till någon .csv-fil tillåts alla webbplatser.

  Klicka på **OK** för att spara ändringarna.

- **Använd alternativ startlayout**: Välj **Ja** för att ange en XML-fil som beskriver hur apparna ska visas på Start-menyn, inklusive apparnas inbördes ordning. Använd det här alternativet om du behöver anpassa mer på startmenyn. [Anpassa och exportera Start-layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout) innehåller viss vägledning och XML-exempel.

- **Aktivitetsfältet**: Välj om du vill **visa** eller **dölja** aktivitetsfältet. Standardinställningen är att aktivitetsfältet inte visas. Ikoner som exempelvis Wi-Fi-ikonen visas, men inställningarna kan inte ändras av slutanvändarna.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa helskärmsprofiler för [Android](device-restrictions-android.md#kiosk)-, [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings)- och [Windows Holographic for Business](kiosk-settings-holographic.md)-enheter.
