---
title: Skicka anpassade meddelanden till användare med Microsoft Intune
titleSuffix: Microsoft Intune
description: Använda Intune för att skapa och skicka anpassade push-meddelanden till användare av iOS/iPadOS- och Android-enheter
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2020
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
ms.openlocfilehash: 5195ee83efb68cea061e69f5cad49e9d43458450
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609368"
---
# <a name="send-custom-notifications-in-intune"></a>Skicka anpassade meddelanden i Intune  

Använd Microsoft Intune för att skicka anpassade meddelanden till användare av hanterade iOS/iPadOS- och Android-enheter. Dessa meddelanden visas som push-standardmeddelanden från företagsportalappen och Microsoft Intune-appen på en användares enhet, på samma sätt som meddelanden från andra program visas på enheten. Anpassade Intune-meddelanden stöds inte av macOS- och Windows-enheter.   

Anpassade meddelanden innehåller en kort rubrik och en meddelandetext på högst 500 tecken. Dessa meddelanden kan anpassas för valfritt kommunikationssyfte.

### <a name="what-the-notification-looks-like-on-an-iosipados-device"></a>Så här ser meddelandet ut på en iOS/iPadOS-enhet

Om du har företagsportalappen öppen på en iOS/iPadOS-enhet ser meddelandet ut ungefär som på följande skärmbild:

> [!div class="mx-imgBorder"]
> ![Testmeddelande för företagsportalen i iOS/iPadOS](./media/custom-notifications/105046-1.png)

Om enheten är låst liknar meddelandet följande skärmbild:

> [!div class="mx-imgBorder"]
> ![Testmeddelande om låst iOS/iPadOS-enhet](./media/custom-notifications/105046-2.png)

### <a name="what-the-notification-looks-like-on-an-android-device"></a>Så här ser meddelandet ut på en Android-enhet

Om du har företagsportalappen öppen på en Android-enhet liknar meddelandet följande skärmbild:

> [!div class="mx-imgBorder"]
> ![Testmeddelande för Android](./media/custom-notifications/105046-3.png)

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
 
- Om du vill skapa ett meddelande använder du ett konto som har tilldelats en Intune-roll som har rätt behörighet enligt beskrivningen i föregående avsnitt (*Behörigheter*). Information om hur du tilldelar behörigheter till en användare finns i [Rolltilldelningar](../fundamentals/role-based-access-control.md#role-assignments).
- Anpassade meddelanden är begränsade till rubriker med högst 50 tecken och meddelanden med högst 500 tecken.  
- Intune sparar inte text från anpassade meddelanden som skickats tidigare. Om du vill skicka ett meddelande igen måste du återskapa meddelandet.  
- Du kan bara skicka upp till 25 meddelanden till grupper per timme. Den här begränsningen finns på klientnivån. Den här begränsningen gäller inte när du skickar meddelanden till enskilda enheter.
- Du kan bara skicka upp till 25 meddelanden till grupper per timme. Den här begränsningen finns på klientnivån. Den här begränsningen gäller inte när du skickar meddelanden till enskilda användare.
- När du skickar meddelanden till enskilda enheter kan du bara skicka upp till 10 meddelanden per timme till samma enhet.
- Du kan skicka meddelanden till användare i grupper. När du skickar meddelanden till grupper kan varje meddelande vara direkt riktat till 25 grupper. Kapslade grupper räknas inte mot den här summan. När du skickar ett meddelande till en grupp riktas meddelandena endast till användarna i gruppen, och de skickas till alla iOS- eller Android-enheter som användaren har registrerat. Enheter i gruppen ignoreras.
- Du kan skicka meddelanden till en enskild enhet. I stället för att använda grupper väljer du en enhet och använder sedan en fjärransluten [enhetsåtgärd](device-management.md#available-device-actions) för att skicka det anpassade meddelandet.  

**Leverans**:

- Intune skickar meddelandet till användarnas företagsportalapp eller Microsoft Intune-appen, som sedan skapar push-meddelandet. Användarna behöver inte vara inloggade i appen för att meddelandet ska kunna push-överföras till enheten, men enheten måste ha registrerats av målanvändaren.
- Intune, företagsportalappen och Microsoft Intune-appen kan inte garantera att ett anpassat meddelande levereras. Anpassade meddelanden kan visas efter flera timmars fördröjning, eller kanske inte alls. Därför bör de inte användas för brådskande meddelanden.  
- Anpassade meddelanden från Intune visas på enheter som vanliga push-meddelanden. Om företagsportalappen är öppen på en iOS-enhet när meddelandet mottas visas meddelandet i appen och inte som ett push-meddelande i systemet.  
- Anpassade meddelanden kan visas på låsskärmar på både iOS/iPadOS- och Android-enheter, beroende på enhetsinställningarna.  
- Andra appar kan ha åtkomst till data i dina anpassade meddelanden på Android-enheter. Använd dem inte för känslig kommunikation.  
- Användare av en enhet som nyligen har avregistrerats eller användare som har tagits bort från en grupp kan fortfarande få ett anpassat meddelande som skickas till den gruppen senare.  Om du lägger till en användare i en grupp efter att ett anpassat meddelande har skickats till gruppen, kan den nyligen tillagda användaren på motsvarande sätt ta emot det meddelande som skickades tidigare.  

## <a name="send-a-custom-notification-to-groups"></a>Skicka ett anpassat meddelande till grupper

1. Logga in på [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med ett konto som har behörighet att skapa och skicka meddelanden och gå till **Administration av klientorganisation** > **Anpassade meddelanden**.  

2. På fliken Grundläggande anger du följande och väljer sedan **Nästa** för att fortsätta.  
   - **Rubrik** – Ange en rubrik för meddelandet. Rubriken får innehålla högst 50 tecken.  
   - **Brödtext** – Ange meddelandet. Meddelanden får innehålla högst 500 tecken.

   ![Skapa ett anpassat meddelande](./media/custom-notifications/custom-notifications.png)  

3. På fliken **Tilldelningar** väljer du de grupper som du vill skicka det här anpassade meddelandet till och väljer sedan Nästa för att fortsätta. Om du skickar ett meddelande till en grupp riktas meddelandet endast till användarna i den gruppen. Meddelandet skickas till alla iOS- och Android-enheter som användaren har registrerat.

4. På fliken **Granska + skapa** granskar du informationen och när du vill skicka meddelandet väljer du **Skapa**.  

Intune bearbetar meddelanden som du skapar direkt. Den enda bekräftelsen på att meddelandet skickades är Intune-aviseringen som bekräftar att det anpassade meddelandet har skickats.  

![Bekräftelse av ett skickat meddelande](./media/custom-notifications/notification-sent.png)  

Intune spårar inte de anpassade meddelanden som du skickar, och enheterna loggar inte mottagandet utanför enhetens meddelandecenter. Meddelandet kan finnas i en temporär diagnostiklogg om en användare begär support i företagsportalappen eller Intune-appen.

## <a name="send-a-custom-notification-to-a-single-device"></a>Skicka ett anpassat meddelande till en enskild enhet

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med ett konto som har behörighet att skapa och skicka meddelanden och gå sedan till **Enheter** > **Alla enheter**.

2. Öppna *översiktssidan* för den hanterade enhet som du vill skicka en avisering till genom att dubbelklicka på namnet på enheten.

3. Öppna fönstret **Skicka anpassad notis** genom att välja enhetsåtgärden **Skicka anpassad notis** på *översiktssidan* för enheten. Om det här alternativet inte är tillgängligt väljer du alternativet **...** (ellipser) längst upp till höger på sidan och väljer sedan **Skicka anpassad notis**.

4. Ange följande meddelandeinformation i fönstret **Skicka anpassad notis**:  

   - **Rubrik** – Ange en rubrik för meddelandet. Rubriken får innehålla högst 50 tecken.  
   - **Brödtext** – Ange meddelandet. Meddelanden får innehålla högst 500 tecken.  

5. Välj **Skicka** för att skicka det anpassade meddelandet till enheten. Till skillnad från meddelanden du skickar till grupper kan du inte konfigurera en tilldelning eller granska meddelandet innan du skickar det.  

Intune bearbetar meddelandet direkt. Den enda bekräftelse på att meddelandet har skickats är den Intune-avisering du får i konsolen, som visar texten för meddelandet du har skickat.  

## <a name="receive-a-custom-notification"></a>Ta emot ett anpassat meddelande

På en enhet ser användarna anpassade meddelanden som skickas av Intune som ett push-standardmeddelande från företagsportalappen eller Microsoft Intune-appen. Dessa meddelanden liknar de push-meddelanden som användarna tar emot från andra appar på enheten.  

Om appen Företagsportal är öppen när ett meddelande tas emot på en iOS/iPadOS-enhet visas meddelandet i appen i stället för som ett push-meddelande.  

Meddelandet är kvar tills användaren stänger det.  

## <a name="next-steps"></a>Nästa steg

[Hantera enheter](device-management.md)
