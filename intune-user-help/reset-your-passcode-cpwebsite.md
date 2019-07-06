---
title: Så här återställer du lösenordet från företagsportalens webbplats | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2cd69725ad10c08f7c137f4444cce831160dd88
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546806"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Så återställer du enhetens lösenord från företagsportalens webbplats

Om du har tappat bort PIN-koden eller lösenordet kan du återställa det på [företagsportalens webbplats](https://portal.manage.microsoft.com).  

Om du använder en företagsregistrerad enhet kan det hända att du inte ser alternativet för att återställa enhetens lösenord. Kontakta företagets support som kan återställa lösenordet åt dig.

   > [!NOTE]
   > Du kan inte återställa lösenord för enheter som kör Android 7.0 eller senare. Om du glömmer ditt lösenord måste du återställa enheten till fabriksinställningarna. 

## <a name="reset-your-passcode"></a>Återställa lösenordet

1. Öppna [webbplatsen för företagsportalen](https://portal.manage.microsoft.com) och välj knappen __Meny__ > __Enheter__.  

2. Välj den enhet vars lösenord behöver återställas.  

    ![En skärmbild av sidan Enheter med två paneler som visar oidentifierade, allmänt namngivna enheter. En grå banderoll finns direkt under enheterna och uppmanar användaren att identifiera den enhet som används eller lägga till en ny.](./media/rename-reset-device-step2-1808.png) 

3. Välj **Återställ lösenord**. Om lösenordsalternativet inte visas längst upp på sidan väljer du **Mer (…)**  > **Återställ lösenord**.   

   ![Sidan med enhetsinformation för en vald enhet på webbplatsen för företagsportalen, med en lista över länkar längst upp som visar Byt namn, Ta bort, Återställ enhet, Återställ lösenord och Fjärrlås. ](./media/rename-reset-device-1808.png)   

    ![Närbild på ikonen Mer, markerad med en röd pil.](./media/rename-reset-device-step3-more-1808.png)  

4. När du uppmanas till detta klickar du på **Logga ut**. Logga in igen när en ny uppmaning visas. Du måste logga in på webbplatsen för företagsportalen igen inom fem minuter, annars återställer inte företagsportalen enhetens lösenord.  

   > [!NOTE]
   > Du måste logga in för att bekräfta din identitet. Det här görs för att förhindra skadliga försök att återställa enhetens lösenord.

   ![Exempel på skärmbilder som visar en uppmaning att logga ut från företagsportalen. Knapparna för indata från användaren är Logga ut och Avbryt.](./media/iwp-reset-passcode-popup-1808.png)

5. Ett meddelande visas som varnar dig om att det befintliga enhetslösenordet kommer att tas bort. Klicka på **Återställ lösenord** för att bekräfta.  
    > [!WARNING]
    > När du har återställt lösenordet kommer alla som har fysisk åtkomst till enheten att kunna komma åt det mesta av den personliga informationen och företagsinformationen på den. Återställ inte lösenordet om du för tillfället inte har enheten i din ägo.  

   ![Exempel på skärmbild som visar det andra meddelandet för att återställa lösenord. Innehåller länkar så att du kan läsa mer om att ange ett nytt lösenord i dokumentationen, samt enskilda knappar för att återställa lösenord och avbryta.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Om du återställer lösenordet för en iOS-enhet kommer dess befintliga lösenord att tas bort. För Windows- eller Android-enheter kommer du att få ett tillfälligt lösenord så att du kan låsa upp enheten och ange ett nytt lösenord. 

   > [!NOTE]
   > Du hittar det tillfälliga lösenordet för Windows- och Android-enheter i företagsportalen, på sidan med information om enheten. I avsnittet [Ställa in ett nytt lösenord](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) finns mer operativsystemspecifika beskrivningar om lösenord.  
   
7. På din enhet går du till **Inställningar** och ändrar det tillfälliga lösenordet. 

8. En flagga visas längst upp till höger på företagsportalens webbplats. Klicka för att läsa meddelandet och bekräfta att lösenordet har återställts.  

## <a name="set-up-a-new-passcode"></a>Ställa in ett nytt lösenord  

Det här avsnittet beskriver återställning av lösenord och funktionen med tillfälliga lösenord för varje enhetsplattform.  

**Android**: Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller både bokstäver och siffror.

**iOS**: Tar bort det befintliga lösenordet, men skapar inte något tillfälligt lösenord. Om du använder fingeravtrycksläsning med Touch ID för att öppna enheten eller göra köp måste du konfigurera detta igen.  

**Windows 10 Mobile**: Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller bokstäver och siffror. Om ansiktsigenkänning med Windows Hello har konfigurerats fungerar det fortfarande med enheten.

**Windows Phone 8.1**: Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller siffror.  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
