---
title: Registrera med enhetsregistreringshanteraren | Microsoft Docs
description: "Med kontot för enhetsregistreringshanterare (DEM) kan du hantera ett stort antal delade, företagsägda mobila enheter med ett enda användarkonto."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: ea57a51f2855dea416ad4a76e657e1846ffe41f1
ms.lasthandoff: 04/24/2017


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot för *enhetsregistreringshanterare* (DEM) är ett särskilt användarkonto som kan registrera upp till 1 000 enheter. Du kan lägga till befintliga användare till DEM-kontot för att ge dem speciella DEM-funktioner. Varje registrerad enhet använder en enda licens. Vi rekommenderar att du använder enheter som registrerats via det här kontot som delade enheter (d.v.s. utan användartillhörighet) snarare än personliga enheter (BYOD).  

Användarna måste finnas i Azure Portal för att kunna läggas till som enhetsregistreringshanterare. För optimal säkerhet bör DEM-användare inte även vara Intune-administratörer.

>[!NOTE]
>DEM-registreringsmetoden kan inte användas med [Apple Configurator-installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md), [direktregistrering](ios-direct-enrollment-in-microsoft-intune.md) eller [DEP-registreringsmetoden](ios-device-enrollment-program-in-microsoft-intune.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exempelscenario för enhetsregistreringshanterare

En restaurang vill tillhandahålla 50 surfplattor vid kassan för servitörerna. Kökspersonalen behöver också surfplattor för att se beställningarna. De anställda behöver aldrig ha tillgång till företagets data eller logga in som användare. Intune-administratören skapar ett konto för enhetsregistreringshantering (DEM) och lägger till en restaurangchef till DEM-kontot, vilket i praktiken ger chefen DEM-funktioner. Chefen kan nu registrera de 50 surfplattorna med hjälp av DEM-autentiseringsuppgifter.

Endast användare i Intune-konsolen kan vara enhetsregistreringshanterare. Den användare som är enhetsregistreringshanterare får inte vara Intune-administratör.

DEM-användaren kan:

-   Registrera upp till 1000 enheter i Intune
-   Logga in på företagsportalsappen och hämta företagsappar
-   Konfigurera åtkomst till företagets data genom att distribuera rollspecifika appar till surfplattorna

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Begränsningar för enheter som registreras med ett DEM-konto

Enheter som har registrerats med ett konto för enhetsregistreringshantering har följande begränsningar:

  - Det finns ingen specifik "enhetsanvändare". Därför finns det inte någon åtkomst för e-post eller företagsdata. Men VPN kan ändå användas för att t. ex. förse enhetsappar med åtkomst till data.

  - Det finns inte någon villkorlig åtkomst eftersom dessa scenarierna är per användare.

  - DEM-användaren kan inte avregistrera DEM-registrerade enheter på själva enheten genom företagsportalen. Intune-administratörer kan använda den funktionen, men inte DEM-användare.

  - Endast den lokala enheten visas i företagsportalappen eller webbplatsen.

  - Användare kan inte använda apparna för Apples volymköpsprogram (VPP) på grund av Apple-ID-kraven per användare för apphantering.

  - (Endast iOS) Om du använder DEM för att registrera iOS-enheter kan du inte använda Apple Configurator eller Apples enhetsregistreringsprogram (DEP) för att registrera enheter.

> [!NOTE]
> Om du vill distribuera appar till enheter som hanteras med enhetsregistreringshanteraren distribuerar du företagsportalappen som en **obligatorisk installation** till enhetsregistreringshanterarens användarkonto.
> I syfte att förbättra prestanda visas endast den lokala enheten i företagsportalappen på en DEM-enhet. Fjärrhantering av andra DEM-enheter kan bara utföras från Intune-administratörskonsolen.


## <a name="add-a-device-enrollment-manager"></a>Lägg till en enhetsregistreringshanterare

1.  Kontrollera att användaren som du vill lägga till i DEM-kontot redan finns. Om du behöver lägga till användaren loggar du in på [Office 365-portalen](https://go.microsoft.com/fwlink/p/?LinkId=698854) och följer stegen i [Lägga till användare individuellt eller i grupp till Office 365-portalen](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

2.  Logga in på [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) med dina administratörsautentiseringsuppgifter.

3.  Gå till navigeringsfönstret och välj **Admin**, så sedan till **Administratörshantering** och välj **Enhetsregistreringshanteraren**. Sidan **Enhetsregistreringshanterare** visas.

4.  Välj **Lägg till...**. Dialogrutan **Lägg till enhetsregistreringshanterare** öppnas.

5.  Ange Intune-kontots **användar-ID** och välj sedan **OK**.

    DEM-användaren kan nu registrera mobila enheter på samma sätt som när en slutanvändare registrerar en BYOD i företagsportalen. Användaren av hanteraren kan installera företagsportalappen och registrera enheten med sina autentiseringsuppgifter för DEM på upp till 1000 enheter. Stegen för att registrera slutanvändare för varje plattform finns i:

  - [Registrera en iOS-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-ios)
  - [Registrera en macOS-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos)
  - [Registrera en Android-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android)
  - [Registrera en Windows-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Ta bort en enhetsregistreringshanterare från Intune

1.  Logga in på [Microsoft Intune-administrationsportalen](https://manage.microsoft.com) med dina administratörsautentiseringsuppgifter.

2.  Gå till navigeringsfönstret och välj **Admin**, så sedan till **Administratörshantering** och välj **Enhetsregistreringshanteraren**. Sidan **Enhetsregistreringshanterare** visas.

3.  Välj den **användare** i Enhetsregistreringshanteraren som du vill ta bort och välj sedan **Ta bort**. Den här användaren kommer inte att tas bort från Intune och de enheter som den här användaren hanterar förblir registrerade i Intune. Genom att ta bort en enhetsregistreringshanterare förhindras den användaren att registrera ytterligare enheter i Intune.

4.  Bekräfta att du vill ta bort enhetsregistreringshanteraren genom att välja **Ja**.

Redan registrerade enheter påverkas inte av att en enhetsregistreringshanterare tas bort. När en enhetsregistreringshanterare tas bort:

-   Inga registrerade enheter påverkas.

-   De registrerade enheterna fortsätter att vara fullständigt hanterade.

-   De borttagna kontouppgifterna för enhetsregistreringshanteraren förblir giltiga för inloggning på företagsportalen och åtkomst till appar.

-   De borttagna kontoautentiseringsuppgifterna för den borttagna enhetsregistreringshanteraren kan ändå inte rensa eller dra tillbaka enheter.

-   Det borttagna enhetsregistreringshanterarkontots relation till registrerade enheter finns kvar, men inga ytterligare enheter kan registreras.

