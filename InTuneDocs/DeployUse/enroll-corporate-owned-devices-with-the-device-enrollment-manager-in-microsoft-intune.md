---
# required metadata

title: Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune
Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot *enhetsregistreringshanterare* är ett särskilt Intune-konto med behörighet att registrera högst fem enheter. Du kan utse en arkivhanterare eller -kontrollant, till exempel ett användarkonto för enhetsregistreringshanteraren som kan användas för att göra följande:

-   Registrera enheter i Intune

-   Logga in på företagsportalen för att hämta företagsappar

-   Installera och avinstallera program

-   Konfigurera åtkomst till företagsdata

Använd endast enhetshanterarkontot för enheter som inte tar emot e-post eller inloggning som en specifik användare. Enheter som hanteras med enhetshanterarkontot kan inte konfigureras med villkorlig åtkomst, eftersom dessa också är scenarier per användare. Arkivhanteraren kan inte återställa enheten från företagsportalen.

Exempelscenario för enhetsregistreringshanteraren: En restaurang vill ha surfplattor vid kassan för servitörerna. Kökspersonalen behöver också surfplattor för att se beställningarna. Medarbetarna behöver aldrig logga in eller komma åt företagets data. Intune-administratören skapar ett konto för enhetsregistreringshanteraren och använder det kontot för att registrera de enheter som ägs av företaget.

Alternativt kan administratören ge inloggningsuppgifterna för enhetsregistrering till restaurangchefen, så att han eller hon kan registrera och hantera enheter. Administratören eller restaurangchefen kan distribuera rollspecifika appar till restaurangens enheter.

> [!NOTE]
> Administratören kan också välja enheten i Intune-konsolen och dra tillbaka den från enhetshanteringen med administrationskonsolen. Användarkonton i enhetsregistreringshanteraren med fler än 20 registrerade enheter kan få problem med att använda företagsportalappen.

## Om du vill distribuera appar till enheter som hanteras med enhetsregistreringshanteraren distribuerar du företagsportalappen som en **obligatorisk installation** till enhetsregistreringshanterarens användarkonto.
Skapa konton för enhetsregistreringshanterare Konton för enhetsregistreringshanteraren är användarkonton med behörighet att registrera ett stort antal enheter som ägs av företaget.

#### Endast användare i Intune-konsolen kan vara enhetsregistreringshanterare.

1.  Lägg till en enhetsregistreringshanterare i Intune

2.  Gå till [Microsoft Intune-kontoportalen](http://go.microsoft.com/fwlink/?LinkId=698854) och logga in på ditt administratörskonto.

3.  Klicka på **Lägg till användare** Kontrollera att det användarkonto som ska bli enhetsregistreringshanterare finns med i listan. Om den inte finns med lägger du till användaren genom att klicka på **Ny** och slutföra processen att lägga till användare. En prenumerationslicens krävs för varje användare som använder tjänsten och *enhetsregistreringshanteraren* får inte vara Intune-administratör.

4.  Avgör om du behöver lägga till fler licenser innan du använder den här funktionen.

5.  Logga in på [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) med ditt administratörskonto. I navigeringsfönstret klickar du på **Admin**, går till **Administratörshantering** och väljer **Enhetsregistreringshanteraren**.

6.  Sidan Enhetsregistreringshanteraren öppnas. Klicka på **Lägg till...**.

7.  Dialogrutan **Lägg till enhetsregistreringshanterare** öppnas. Ange **användar-ID** för Intune-kontot och klicka sedan på **OK**.

8.  Den användare som är Enhetsregistreringshanterare får inte vara Intune-administratör.

## Enhetsregistreringshanteraren kan nu registrera mobila enheter på samma sätt som när en slutanvändare registrerar en BYOD i företagsportalen.

1.  Ta bort en enhetsregistreringshanterare från Intune

2.  Logga in på [Microsoft Intune-administrationsportalen](http://manage.microsoft.com) med ditt administratörskonto. I navigeringsfönstret klickar du på **Admin** , går till **Administratörshantering** och väljer **Enhetsregistreringshanteraren**.

3.  Sidan Enhetsregistreringshanteraren öppnas. Välj den **användare** i Enhetsregistreringshanteraren som du vill ta bort och klicka sedan på **Ta bort**. Den här användaren kommer inte att tas bort från Intune och de enheter som den här användaren hanterar förblir registrerade i Intune.

4.  Genom att ta bort en enhetsregistreringshanterare förhindras den användaren att registrera ytterligare enheter i Intune.

Klicka på **Ja** för att bekräfta att du vill ta bort enhetsregistreringshanteraren. Redan registrerade enheter påverkas inte av att en enhetsregistreringshanterare tas bort.

-   När en enhetsregistreringshanterare tas bort:

-   Påverkas inga registrerade enheter

-   Fortsätter registrerade enheter att vara fullständigt hanterade

-   Gäller de borttagna kontouppgifterna för enhetsregistreringshanteraren fortfarande för inloggning på företagsportalen för att komma åt appar

-   Kan de borttagna kontouppgifterna för den borttagna enhetsregistreringshanteraren fortfarande inte rensa eller dra tillbaka enheter


<!--HONumber=May16_HO2-->


