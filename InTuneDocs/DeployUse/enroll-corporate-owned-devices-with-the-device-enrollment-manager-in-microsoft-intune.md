---
title: Registrera med enhetsregistreringshanteraren | Microsoft Intune
description: "Med kontot för enhetsregistreringshanterare (DEM) kan du hantera ett stort antal delade, företagsägda mobila enheter med ett enda användarkonto."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de3296e81c88b3ac04e3ba3f3d3ca222a59df7bd
ms.openlocfilehash: 450a5764005643a2f890780530d1f2880a4e517b


---


# Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune
Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot för *enhetsregistreringshanterare* (DEM) är ett särskilt Intune-konto med behörighet att registrera upp till 1 000 enheter. Använd enheter som registrerats med kontot för enhetsregistreringshanterare som delade enheter i stället för att använda personliga enheter (”BYOD”). Användarna kan till exempel inte använda ”interna” e-postappar. Du kan utse en arkivhanterare eller -kontrollant, till exempel ett användarkonto för enhetsregistreringshanteraren som kan användas för att göra följande:

-   Registrera enheter i Intune

-   Logga in på företagsportalen för att hämta företagsappar

-   Installera och avinstallera program

-   Konfigurera åtkomst till företagsdata


**Exempelscenario för enhetsregistreringshanteraren:** En restaurang vill ha surfplattor vid kassan för servitörerna. Kökspersonalen behöver också skärmar för att kunna se beställningarna. Medarbetarna behöver aldrig logga in eller komma åt företagets data. Intune-administratören skapar ett konto för enhetsregistreringshanteraren och använder det kontot för att registrera de enheter som ägs av företaget. Alternativt kan administratören ge inloggningsuppgifterna för enhetsregistrering till restaurangchefen, så att han eller hon kan registrera och hantera enheter.

Administratören eller restaurangchefen kan distribuera rollspecifika appar till restaurangens enheter. Administratören kan också välja enheten i Intune-konsolen och dra tillbaka den från enhetshanteringen med administrationskonsolen.

Enheter som registrerats med ett konto för enhetsregistreringshanterare har följande begränsningar:
  - Ingen specifik användare så alla enheter är ”användarlösa”; därför ingen åtkomst till e-psot eller företagsdata även om VPN, exempelvis, fortfarande kan ge enhetsappar åtkomst till data
  - Ingen villkorlig åtkomst eftersom de är scenarier per användare
  - Det går inte att återställa enheterna från företagsportalen
  - Endast den lokala enheten visas i företagsportalappen eller webbplatsen
  - Inget Apple Volume Purchase Program (VPP) på grund av kraven på Apple-ID per användare för apphantering
  - Kan inte heller registreras med Apple Configurator eller Apples DEP-program (iOS-enheter)

> [!NOTE]
> Om du vill distribuera appar till enheter som hanteras med enhetsregistreringshanteraren distribuerar du företagsportalappen som en **obligatorisk installation** till enhetsregistreringshanterarens användarkonto.
> I syfte att förbättra prestanda visar företagsportalappen på en enhet i DEM enbart den lokala enheten. Fjärrhantering av andra DEM-enheter kan bara utföras från Intune-administratörskonsolen.

## Skapa konton för enhetsregistreringshanterare
Konton för enhetsregistreringshanteraren är användarkonton med behörighet att registrera ett stort antal enheter som ägs av företaget. Endast användare i Intune-konsolen kan vara enhetsregistreringshanterare.

#### Lägg till en enhetsregistreringshanterare i Intune

1.  Gå till [Microsoft Intune-kontoportalen](http://go.microsoft.com/fwlink/?LinkId=698854) och logga in på ditt administratörskonto.

2.  Välj **Lägg till användare**.

3.  Kontrollera att det användarkonto som ska bli enhetsregistreringshanterare finns med i listan. Om den inte finns med lägger du till användaren genom att välja **Ny** och slutföra processen att lägga till användare. En prenumerationslicens krävs för varje användare som använder tjänsten och *enhetsregistreringshanteraren* får inte vara Intune-administratör. Avgör om du behöver lägga till fler licenser innan du använder den här funktionen.

4.  Logga in på [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) med ditt administratörskonto.

5.  I navigeringsfönstret väljer du **Admin**, **Administratörshantering** och sedan **Enhetsregistreringshanteraren**. Sidan Enhetsregistreringshanteraren öppnas.

6.  Välj **Lägg till...**. Dialogrutan **Lägg till enhetsregistreringshanterare** öppnas.

7.  Ange **användar-ID** för Intune-kontot och välj sedan **OK**. Den användare som är Enhetsregistreringshanterare får inte vara Intune-administratör.

8.  Enhetsregistreringshanteraren kan nu registrera mobila enheter på samma sätt som när en slutanvändare registrerar en BYOD i företagsportalen.

## Ta bort en enhetsregistreringshanterare från Intune

1.  Logga in på [Microsoft Intune-administrationsportalen](http://manage.microsoft.com) med ditt administratörskonto.

2.  I navigeringsfönstret väljer du **Admin**, **Administratörshantering** och sedan **Enhetsregistreringshanteraren**. Sidan Enhetsregistreringshanteraren öppnas.

3.  Välj den **användare** i Enhetsregistreringshanteraren som du vill ta bort och välj sedan **Ta bort**. Den här användaren kommer inte att tas bort från Intune och de enheter som den här användaren hanterar förblir registrerade i Intune. Genom att ta bort en enhetsregistreringshanterare förhindras den användaren att registrera ytterligare enheter i Intune.

4.  Välj **Ja** för att bekräfta att du vill ta bort enhetsregistreringshanteraren.

Redan registrerade enheter påverkas inte av att en enhetsregistreringshanterare tas bort. När en enhetsregistreringshanterare tas bort:

-   Påverkas inga registrerade enheter

-   Fortsätter registrerade enheter att vara fullständigt hanterade

-   Gäller de borttagna kontouppgifterna för enhetsregistreringshanteraren fortfarande för inloggning på företagsportalen för att komma åt appar

-   Kan de borttagna kontouppgifterna för den borttagna enhetsregistreringshanteraren fortfarande inte rensa eller dra tillbaka enheter

-   Finns den borttagna enhetsregistreringshanterarkontots relation till registrerade enheter kvar, men inga ytterligare enheter kan registreras



<!--HONumber=Jul16_HO5-->


