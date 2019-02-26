---
title: Helskärmsinställningar för Windows Holographic for Business i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera helskärmsläget i dina Windows Holographic for Business-enheter för en app eller för flera appar, anpassa startmenyn, lägg till appar, visa aktivitetsfältet och konfigurera en webbläsare i Microsoft Intune.
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c5fd9998a4816775b3fc1d7803dc26e223b1e39
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742447"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Enhetsinställningar i Windows Holographic for Business för att köra helskärmsläge i Intune

På Windows Holographic for Business-enheter kan du konfigurera enheterna att köra i helskärmsläge för en enskild app eller helskärmsläge för flera appar. Vissa funktioner stöds inte i Windows Holographic for Business.

Den här artikeln visar och beskriver de olika inställningar som du kan styra på Windows Holographic for Business-enheter. I din MDM-lösning (hantering av mobilenheter) använder du inställningarna till att konfigurera att dina Windows Holographic for Business-enheter körs i helskärmsläge.

Som Intune-administratör kan du skapa och tilldela dessa inställningar till dina enheter.

Mer information om Windows helskärmsfunktion i Intune finns i [Konfigurera inställningar för helskärmsläge](kiosk-settings.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa profilen](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>Kiosker med en enda app i helskärmsläge

När du väljer helskärmsläge för enskilda appar kan du ange följande inställningar:

- **Typ av användarinloggning**: Välj **Lokalt användarkonto** för att ange det lokala användarkontot (för enheten) eller ett Microsoft-konto som är associerat med kioskappen. Användarkontotyper med **Automatisk inloggning** stöds inte på Windows Holographic for Business.

- **Programtyp**: Välj **Store-app**.

- **App som ska köras i helskärmsläge**: Välj **Lägg till en Store-app** och välj en app i listan.

    Har du inte några appar i listan? Lägg till några med hjälp av anvisningarna i [Klientappar](apps-add.md).

    Klicka på **OK** för att spara ändringarna.

## <a name="multi-app-kiosks"></a>Helskärmsläge för flera appar

Appar i det här läget är tillgängliga på startmenyn. De här apparna är de enda appar som användaren kan öppna. När du väljer helskärmsläge för flera appar kan du ange följande inställningar:

- **Rikta in enheter med Windows 10 i S-läge**: Välj **Nej**. S-läge stöds inte i Windows Holographic for Business.

- **Typ av användarinloggning**: Lägg till ett eller flera användarkonton som kan använda de appar som du lägger till. Alternativen är: 

  - **Automatisk inloggning**: Stöds inte i Windows Holographic for Business.
  - **Lokala användarkonton**: **Lägg till** det lokala användarkontot (för enheten). Det konto som du anger används för att logga in i helskärmsläget.
  - **Azure AD-användare eller -grupp (Windows 10, version 1803 och senare)**: Kräver autentiseringsuppgifter för inloggning på enheten. Välj **Lägg till** för att välja Azure AD-användare eller grupper i listan. Du kan välja flera användare och grupper. Välj **OK** för att spara ändringarna.
  - **HoloLens-besökare**: Besökarkontot är ett gästkonto som inte kräver autentiseringsuppgifter eller autentisering, enligt beskrivningen i [begrepp om delat PC-läge](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts).

- **Program**: Lägg till appar som ska köras på kioskenheten. Kom ihåg att du kan lägga till flera appar.

  - **Lägg till Store-appar**: Välj en befintlig app som du har lagt till via [Klientappar](apps-add.md). Om du inte har några appar i listan kan du hämta appar och [lägga till dem i Intune](store-apps-windows.md).
  - **Lägg till Win32-app**: Stöds inte i Windows Holographic for Business.
  - **Lägg till via AUMID**: Använd det här alternativet för att lägga till inkorgens Windows-appar. Ange följande egenskaper: 

    - **Programnamn**: Obligatoriskt. Ange ett namn på programmet.
    - **ID för programanvändarmodell (AUMID)**: Obligatoriskt. Ange appens programanvändarmodell-ID (AUMID) för Windows-appen. Information om hur du hittar detta ID finns i [Hitta programanvändarmodell-ID för en installerad app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app).
    - **Panelstorlek**: Obligatoriskt. Välj storleken Liten, Medel, Bred eller Stor för appanelen.

- **Kiosk Browser-inställningar**: Stöds inte i Windows Holographic for Business.

- **Använd alternativ startlayout**: Välj **Ja** för att ange en XML-fil som beskriver hur apparna ska visas på Start-menyn, inklusive apparnas inbördes ordning. Använd det här alternativet om du behöver anpassa mer på startmenyn. [Anpassa och exportera Start-layout](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens) ger viss vägledning och innehåller en specifik XML-fil för Windows Holographic for Business-enheter.

- **Aktivitetsfältet**: Stöds inte i Windows Holographic for Business.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa helskärmsprofiler för enheter som kör [Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) samt [Windows 10 och senare](kiosk-settings-windows.md).
