---
title: Så här återställer du lösenordet från företagsportalens webbplats | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
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
ms.openlocfilehash: 690fb81350c0c264677c6c75b8942e9cdcd4e8f0
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163365"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Så återställer du enhetens lösenord från företagsportalens webbplats

Om du har tappat bort PIN-koden eller lösenordet kan du återställa det på [företagsportalens webbplats](https://portal.manage.microsoft.com). 

Alternativet Återställ lösen ord kanske inte visas för en företags registrerad enhet. I det här fallet kontaktar du företagets support för att återställa den åt dig.  

Återställning av lösen ord är inte tillgängligt för enheter som kör Android 7,0 och senare. Om du glömmer ditt lösen ord på någon av dessa enheter måste du återställa det till fabriks inställningarna.  

## <a name="reset-your-passcode"></a>Återställa lösenordet

1. Öppna [webbplatsen för företagsportalen](https://portal.manage.microsoft.com) och välj knappen __Meny__ > __Enheter__.  

2. Välj den enhet vars lösenord behöver återställas.  

    ![En skärmbild av sidan Enheter med två paneler som visar oidentifierade, allmänt namngivna enheter. En grå banderoll visas under enheterna och uppmanar användaren att identifiera den enhet som används eller att lägga till en ny.](./media/rename-reset-device-step2-1808.png) 

3. Välj **Återställ lösenord**. Om lösenordsalternativet inte visas längst upp på sidan väljer du **Mer (…)**  > **Återställ lösenord**.   

   ![Sidan med enhetsinformation för en vald enhet på webbplatsen för företagsportalen, med en lista över länkar längst upp som visar Byt namn, Ta bort, Återställ enhet, Återställ lösenord och Fjärrlås. ](./media/rename-reset-device-1808.png)   

    ![Skärmbild av ikonen Mer, som visas med en röd pil.](./media/rename-reset-device-step3-more-1808.png)  

4. När du uppmanas till detta klickar du på **Logga ut**. Logga in igen när en ny uppmaning visas. Du måste logga in på företagsportalens webbplats inom fem minuter för att enhetens lösenord ska återställas.  

   > [!NOTE]
   > Du måste logga in för att bekräfta din identitet. Det här görs för att förhindra skadliga försök att återställa enhetens lösenord.

   ![Exempel på skärmbilder som visar en uppmaning att logga ut från företagsportalen. Knapparna för indata från användaren är Logga ut och Avbryt.](./media/iwp-reset-passcode-popup-1808.png)

5. Ett meddelande visas som varnar dig om att det befintliga enhetslösenordet kommer att tas bort. Klicka på **Återställ lösenord** för att bekräfta.  
    > [!WARNING]
    > När du har återställt lösenordet kommer alla som har fysisk åtkomst till enheten att kunna komma åt det mesta av den personliga informationen och företagsinformationen på den. Återställ inte lösenordet om du för tillfället inte har enheten i din ägo.  

   ![Exempel på skärmbild som visar det andra meddelandet för att återställa lösenord. Innehåller länkar så att du kan läsa mer om att ange ett nytt lösenord i dokumentationen, samt enskilda knappar för att återställa lösenord och avbryta.](./media/iwp-reset-passcode-popup2-1808.png) 

6. Om du återställer lösenordet för en iOS-enhet kommer dess befintliga lösenord att tas bort. För Windows- eller Android-enheter får du ett tillfälligt lösenord så att du kan låsa upp enheten och ange ett nytt lösenord. 

   > [!NOTE]
   > Du hittar det tillfälliga lösenordet för Windows- och Android-enheter i företagsportalen, på sidan med information om enheten. I avsnittet [Ställa in ett nytt lösenord](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode) finns mer operativsystemspecifika beskrivningar om lösenord.  
   
7. På din enhet går du till **Inställningar** och ändrar det tillfälliga lösenordet. 

8. En flagga visas längst upp till höger på företagsportalens webbplats. Klicka för att läsa meddelandet och bekräfta att lösenordet har återställts.  

## <a name="set-up-a-new-passcode"></a>Ställa in ett nytt lösenord  

Det här avsnittet beskriver återställning av lösenord och funktionen med tillfälliga lösenord för varje enhetsplattform.  

**Android**: Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller både bokstäver och siffror.

**iOS**: Tar bort det befintliga lösenordet, men skapar inte något tillfälligt lösenord. Om du använder Touch ID för att öppna din enhet eller göra inköp måste du konfigurera den igen.  

**Windows 10 Mobile**: Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller bokstäver och siffror. Om ansiktsigenkänning med Windows Hello har konfigurerats fungerar det fortfarande med enheten.

**Windows Phone 8.1**: Tar bort det befintliga lösenordet och skapar ett tillfälligt lösenord som innehåller siffror.  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
