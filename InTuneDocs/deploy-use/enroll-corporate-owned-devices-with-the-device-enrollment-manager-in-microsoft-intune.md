---
title: Registrera med enhetsregistreringshanteraren | Microsoft Intune
description: "Med kontot för enhetsregistreringshanterare (DEM) kan du hantera ett stort antal delade, företagsägda mobila enheter med ett enda användarkonto."
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 83b89d06793f6f3934537408fb600b3b89afd35b


---


# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Registrera företagsägda enheter med Enhetsregistreringshanteraren i Microsoft Intune
Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot för *enhetsregistreringshanterare* (DEM) är ett särskilt Intune-konto som kan registrera upp till 1 000 enheter. Varje registrerad enhet använder en enda licens. Vi rekommenderar att du använder enheter som registrerats via det här kontot som delade enheter snarare än personliga enheter (BYOD). Användarna kan till exempel inte använda ”interna” e-postappar. Licensiering för DEM är per enhet, inte per användare.

Du kan, exempelvis, tilldela en lagringshanterare eller övervakare ett användarkonto för enhetsregistreringshantering, så att denna kan göra följande:

-   Registrera enheter i Intune.

-   Logga in på företagsportalen och hämta företagsappar.

-   Installera och avinstallera program.

-   Konfigurera åtkomst till företagsdata.


**Scenario för enhetsregistreringshanteraren:** En restaurang vill ha surfplattor vid kassan för servitörerna. Kökspersonalen behöver också skärmar för att kunna se beställningarna. De anställda behöver aldrig ha tillgång till företagets data eller logga in som användare. Intune-administratören skapar ett konto för enhetsregistreringshantering och registrerar företagsägda enheter med hjälp av kontot. Alternativt kan administratören ge autentiseringsuppgifterna för enhetsregistreringshanteringen till restaurangchefen, som då skulle kunna registrera och hantera enheterna.

Administratören eller chefen kan distribuera rollspecifika appar till restaurangenheterna. En administratör kan även välja enheten på Intune-konsolen och dra tillbaka den från mobil tjänsthantering med administrationskonsolen.

Enheter som har registrerats med ett konto för enhetsregistreringshantering har följande begränsningar:
  - Det finns inge någon specifik ”enhetshanterare”. Därför finns det inte någon åtkomst för e-post eller företagsdata. Men VPN kan t.ex. ändå förse enhetsappar med åtkomst till data.
  - Det finns inte någon villkorlig åtkomst eftersom dessa scenarierna är per användare.
  - Det går inte att återställa enheterna från företagsportalen.
  - Endast den lokala enheten visas i företagsportalappen eller webbplatsen.
  - De kan inte använda apparna för Apples volymköpsprogram (VPP) på grund av Apple-ID-kraven per användare för apphantering.
  - (iOS) De kan inte även registreras med Apple Configurator eller Apple Device Enrollment Program (DEP), men enheter som hanteras med DEP eller Apple Configurator kan registreras utan användartillhörighet.

> [!NOTE]
> Om du vill distribuera appar till enheter som hanteras med enhetsregistreringshanteraren distribuerar du företagsportalappen som en **obligatorisk installation** till enhetsregistreringshanterarens användarkonto.
> I syfte att förbättra prestanda visar företagsportalappen på en enhet i DEM enbart den lokala enheten. Fjärrhantering av andra DEM-enheter kan bara utföras från Intune-administratörskonsolen.

## <a name="create-device-enrollment-manager-accounts"></a>Skapa konton för enhetsregistreringshanterare
Konton för enhetsregistreringshanteraren är användarkonton med behörighet att registrera ett stort antal enheter som ägs av företaget. Endast användare i Intune-konsolen kan vara enhetsregistreringshanterare.

#### <a name="add-a-device-enrollment-manager-to-intune"></a>Lägg till en enhetsregistreringshanterare i Intune

1.  Gå till [Microsoft Intune-kontoportalen](http://go.microsoft.com/fwlink/?LinkId=698854) och logga in på ditt administratörskonto.

2.  Välj **Lägg till användare**.

3.  Kontrollera att det användarkonto som ska bli enhetsregistreringshanterare finns med i listan. Om det inte finns med lägger du till användaren genom att välja **Ny** och slutföra processen **Lägg till användare**. En prenumerationslicens krävs för varje användare som får åtkomst till tjänsten. Enhetsregistreringshanteraren får inte vara Intune-administratör. Kontrollera om du behöver lägga till fler licenser innan du använder den här funktionen.

4.  Logga in på [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) med dina administratörsautentiseringsuppgifter.

5.  Gå till navigeringsfönstret och välj **Admin**, så sedan till **Administratörshantering** och välj **Enhetsregistreringshanteraren**. Sidan **Enhetsregistreringshanterare** visas.

6.  Välj **Lägg till...**. Dialogrutan **Lägg till enhetsregistreringshanterare** öppnas.

7.  Ange Intune-kontots **användar-ID** och välj sedan **OK**. Den användare som är enhetsregistreringshanterare får inte vara Intune-administratör.

8.  Enhetsregistreringshanteraren kan nu registrera mobila enheter på samma sätt som när en slutanvändare registrerar en BYOD i företagsportalen. Användaren av hanteraren kan installera företagsportalappen och registrera enheten med sina autentiseringsuppgifter för DEM på upp till 1000 enheter.

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Ta bort en enhetsregistreringshanterare från Intune

1.  Logga in på [Microsoft Intune-administrationsportalen](http://manage.microsoft.com) med dina administratörsautentiseringsuppgifter.

2.  Gå till navigeringsfönstret och välj **Admin**, så sedan till **Administratörshantering** och välj **Enhetsregistreringshanteraren**. Sidan **Enhetsregistreringshanterare** visas.

3.  Välj den **användare** i Enhetsregistreringshanteraren som du vill ta bort och välj sedan **Ta bort**. Den här användaren kommer inte att tas bort från Intune och de enheter som den här användaren hanterar förblir registrerade i Intune. Genom att ta bort en enhetsregistreringshanterare förhindras den användaren att registrera ytterligare enheter i Intune.

4.  Bekräfta att du vill ta bort enhetsregistreringshanteraren genom att välja **Ja**.

Redan registrerade enheter påverkas inte av att en enhetsregistreringshanterare tas bort. När en enhetsregistreringshanterare tas bort:

-   Inga registrerade enheter påverkas.

-   De registrerade enheterna fortsätter att vara fullständigt hanterade.

-   De borttagna kontouppgifterna för enhetsregistreringshanteraren förblir giltiga för inloggning på företagsportalen och åtkomst till appar.

-   De borttagna kontoautentiseringsuppgifterna för den borttagna enhetsregistreringshanteraren kan ändå inte rensa eller dra tillbaka enheter.

-   Det borttagna enhetsregistreringshanterarkontots relation till registrerade enheter finns kvar, men inga ytterligare enheter kan registreras.



<!--HONumber=Dec16_HO2-->


