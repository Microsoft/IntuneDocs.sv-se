---
title: Skicka anpassade meddelanden till användare med Microsoft Intune
titleSuffix: Microsoft Intune
description: Använda Intune för att skapa och skicka anpassade push-meddelanden till användare av iOS- och Android-enheter
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 443e1e2fff2a0c4641d3446bf72e455cc92ce784
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907295"
---
# <a name="send-custom-notifications-in-intune"></a>Skicka anpassade meddelanden i Intune  

Använd Microsoft Intune för att skicka anpassade meddelanden till användare av hanterade iOS- och Android-enheter. Dessa meddelanden visas som push-standardmeddelanden från företagsportalappen och Microsoft Intune-appen på en användares enhet, på samma sätt som meddelanden från andra program visas på enheten. Anpassade Intune-meddelanden stöds inte av macOS- och Windows-enheter.   

Anpassade meddelanden innehåller en kort rubrik och en meddelandetext på högst 500 tecken. Dessa meddelanden kan anpassas för valfritt kommunikationssyfte.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Vanliga scenarier för att skicka anpassade meddelanden  

- Meddela alla anställda om en ändring i schemat, till exempel om nedstängning av en byggnad på grund av dåligt väder.
- Skicka ett meddelande till användaren av en enskild enhet för att kommunicera en brådskande begäran, till exempel att starta om enheten för att slutföra installationen av en uppdatering. 

## <a name="considerations-for-using-custom-notifications"></a>Att tänka på när du använder anpassade meddelanden

**Enhetskonfiguration** 

- Företagsportalappen eller Microsoft Intune-appen måste vara installerad på enheten innan användarna kan ta emot anpassade meddelanden. De måste också ha konfigurerat behörigheter som tillåter att företagsportalappen eller Microsoft Intune-appen skickar push-meddelanden. Om det behövs kan företagsportalappen och Microsoft Intune-appen uppmana användarna att tillåta aviseringar.  
- Google Play Services är ett obligatoriskt beroende i Android.  
- Enheten måste vara MDM-registrerad.

**Behörigheter**:
- Om du vill skicka meddelanden till grupper måste ditt konto har följande RBAC-behörighet i Intune: *Organisation* > **Uppdatering**.
- Om du vill skicka meddelanden till en enhet måste ditt konto har följande RBAC-behörighet i Intune: *Fjärruppgifter* > **Skicka anpassade meddelanden**.

**Skapa meddelanden**:  
- Om du vill skapa ett meddelande använder du ett konto som har tilldelats en Intune-roll som har behörigheten **Uppdatera** för **Organisation**. Information om hur du tilldelar behörigheter till en användare finns i [Rolltilldelningar](../fundamentals/role-based-access-control.md#role-assignments)  
- Anpassade meddelanden är begränsade till rubriker med högst 50 tecken och meddelanden med högst 500 tecken.  
- Intune sparar inte skickade meddelanden. Om du vill skicka ett meddelande igen måste du återskapa meddelandet.  
- Du kan bara skicka upp till 25 meddelanden till grupper per timme. Den här begränsningen finns på klientnivån. Den här begränsningen gäller inte när du skickar meddelanden till enskilda användare.
- När du skickar meddelanden till enskilda enheter kan du bara skicka upp till 10 meddelanden per timme till samma enhet. 
- Du kan skicka meddelanden till flera användare eller enheter genom att tilldela meddelandet till grupper. När du använder grupper kan varje meddelande vara direkt riktat till 25 grupper. Kapslade grupper räknas inte mot den här summan.  

  Grupper kan innehålla användare eller enheter, men meddelanden skickas endast till användare, och till alla iOS- eller Android-enheter som användaren har registrerat.  
- Du kan skicka meddelanden till en enskild enhet. I stället för att använda grupper väljer du en enhet och använder sedan en fjärransluten [enhetsåtgärd](device-management.md#available-device-actions) för att skicka det anpassade meddelandet.  

**Leverans**:  
- Intune skickar meddelandet till användarnas företagsportalapp eller Microsoft Intune-appen, som sedan skapar push-meddelandet. Användarna behöver inte vara inloggade i appen för att meddelandet ska kunna push-överföras till enheten.  
- Varken Intune, företagsportalappen eller Microsoft Intune-appen kan garantera att ett anpassat meddelande levereras. Anpassade meddelanden kan visas efter flera timmars fördröjning, eller kanske inte alls. Därför bör de inte användas för brådskande meddelanden.  
- Anpassade meddelanden från Intune visas på enheter som vanliga push-meddelanden. Om appen Företagsportal är öppen på en iOS-enhet när den tar emot meddelandet visas meddelandet i appen i stället för som ett push-meddelande.  
- Anpassade meddelanden kan visas på låsskärmar på både iOS- och Android-enheter, beroende på enhetsinställningarna.  
- Andra appar kan ha åtkomst till data i dina anpassade meddelanden på Android-enheter. Använd dem inte för känslig kommunikation.  
- Användare av en enhet som nyligen har avregistrerats eller användare som har tagits bort från en grupp kan fortfarande få ett anpassat meddelande som skickas till den gruppen senare.  Om du lägger till en användare i en grupp efter att ett anpassat meddelande har skickats till gruppen, kan den nyligen tillagda användaren på motsvarande sätt ta emot det meddelande som skickades tidigare.  

## <a name="send-a-custom-notification-to-groups"></a>Skicka ett anpassat meddelande till grupper  

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med ett konto som har behörighet att skapa och skicka meddelanden och gå till **Administration av klientorganisation** > **Anpassade meddelanden**.  

2. På fliken Grundläggande anger du följande och väljer sedan **Nästa** för att fortsätta.  
   - **Rubrik** – Ange en rubrik för meddelandet. Rubriken får innehålla högst 50 tecken.  
   - **Brödtext** – Ange meddelandet. Meddelanden får innehålla högst 500 tecken.

   ![Skapa ett anpassat meddelande](./media/custom-notifications/custom-notifications.png)  

3. På fliken **Tilldelningar** väljer du de grupper som du vill skicka det här anpassade meddelandet till och väljer sedan Nästa för att fortsätta.  

4. På fliken **Granska + skapa** granskar du informationen och när du vill skicka meddelandet väljer du **Skapa**.  

Intune bearbetar meddelanden som du skapar direkt. Den enda bekräftelsen på att meddelandet skickades är Intune-aviseringen som bekräftar att det anpassade meddelandet har skickats.  

![Bekräftelse av ett skickat meddelande](./media/custom-notifications/notification-sent.png)  

Intune spårar inte de anpassade meddelanden som du skickar, och enheterna loggar inte mottagandet utanför enhetens meddelandecenter.  

## <a name="send-a-custom-notification-to-a-single-device"></a>Skicka ett anpassat meddelande till en enskild enhet  

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med ett konto som har behörighet att skapa och skicka meddelanden och gå sedan till **Enheter** > **Alla enheter**.  

2. Välj en enhet som du vill skicka ett meddelande till.  

3. På enhetssidan **Översikt** väljer du alternativet **…** (ellips) högst upp till höger på sidan.  

4. Välj **Skicka anpassad notis** för att öppna fönstret *Skicka anpassad notis* där du anger följande meddelandeinformation:  

   - **Rubrik** – Ange en rubrik för meddelandet. Rubriken får innehålla högst 50 tecken.  
   - **Brödtext** – Ange meddelandet. Meddelanden får innehålla högst 500 tecken.  

5. Välj **Skicka** för att skicka det anpassade meddelandet till enheten. Till skillnad från meddelanden du skickar till grupper kan du inte konfigurera en tilldelning eller granska meddelandet innan du skickar det.  

Intune bearbetar meddelandet direkt. Den enda bekräftelse på att meddelandet har skickats är den Intune-avisering du får i konsolen, som visar texten för meddelandet du har skickat.  

## <a name="receive-a-custom-notification"></a>Ta emot ett anpassat meddelande  

På en enhet ser användarna anpassade meddelanden som skickas av Intune som ett push-standardmeddelande från företagsportalappen eller Microsoft Intune-appen. Dessa meddelanden liknar de push-meddelanden som användarna tar emot från andra appar på enheten.  

Om appen Företagsportal är öppen när ett meddelande tas emot på en iOS-enhet visas meddelandet i appen i stället för som ett push-meddelande.  

Meddelandet är kvar tills användaren stänger det.  

## <a name="next-steps"></a>Nästa steg  

[Hantera enheter](device-management.md)
