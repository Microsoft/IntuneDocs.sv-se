---
title: Registrera Android enterprise-kioskenheter i Intune
titlesuffix: Microsoft Intune
description: Lär dig hur du registrera Android enterprise-kioskenheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 5ea4d41477f2f0c6dc1314e47072d2c4cf862e23
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184836"
---
# <a name="set-up-enrollment-of-android-enterprise-kiosk-devices"></a>Konfigurera registrering av Android enterprise-kioskenheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android stöder kioskenheter med COSU-lösningsuppsättningen (Corporate-Owned, Single-Use – företagsägd, en användning). Sådana enheter används bara för ett ändamål, till exempel digitala skyltar, biljettutskrifter eller lagerhantering. Administratörer låser användningen av enheten för en begränsad uppsättning appar och webblänkar. Användarna kan heller inte lägga till andra appar eller att vidta andra åtgärder på enheten.

Intune hjälper dig att distribuera appar och inställningar för Android-kioskenheter. Specifik information om Android enterprise finns i [Krav för Android enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Enheter som du hanterar på det här sättet registreras i Intune utan ett användarkonto och kopplas inte till någon slutanvändare. De är inte avsedda för program eller appar för personligt bruk som har starka krav på användarspecifika kontodata, till exempel Outlook eller Gmail.

## <a name="device-requirements"></a>Krav på enheten

Enheter måste uppfylla dessa krav för att kunna hanteras som en Android enterprise-kioskenhet:

- Android OS version 5.1 och senare.
- Enheter måste köra en distribution av Android som har anslutningsfunktioner för Google Mobile Services (GMS). Enheter måste ha GMS tillgängligt för att kunna ansluta till GMS.

## <a name="set-up-android-kiosk-management"></a>Konfigurera Android-kioskhantering

Följ dessa steg för att konfigurera Android-kioskhantering:

1. Förbered hantering av mobila enheter genom att [ange MDM-utfärdare som **Microsoft Intune**](mdm-authority-set.md) för instruktioner. Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.
2. [Anslut ditt Intune-klientkonto till ditt Android enterprise-konto](connect-intune-android-enterprise.md).
3. [Skapa en registreringsprofil](#create-an-enrollment-profile).
4. [Skapa en enhetsgrupp](#create-a-device-group).
5. [Registrera kioskenheterna](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>Skapa en registreringsprofil

Du måste skapa en registreringsprofil så att du kan registrera dina kioskenheter. När profilen har skapats får den en registreringstoken (slumpmässig sträng) och en QR-kod. Beroende på enhetens Android OS-version kan du använda token eller QR-koden för att [registrera kioskenheten](#enroll-the-kiosk-devices).

1. Gå till [Intune-portalen](https://portal.azure.com) och välj **Enhetsregistrering** > **Android-registrering** > **Registreringar av kiosk- och uppgiftsenheter**.
2. Välj **Skapa** och fyll i de obligatoriska fälten.
    - **Namn**: Ange ett namn som du vill använda när du tilldelar profilen till den dynamiska enhetsgruppen.
    - **Tokenförfallodatum**: Datumet då token går ut. Google använder ett maxvärde på 90 dagar.
3. Spara profilen genom att välja **Skapa**.

### <a name="create-a-device-group"></a>Skapa en enhetsgrupp

Du kan rikta appar och principer till tilldelade eller dynamiska enhetsgrupper. Du kan konfigurera dynamiska AAD-enhetsgrupper att automatiskt fylla i enheter som har registrerats med den viss registreringsprofil med hjälp av följande steg:

1. Gå till [Intune-portalen](https://portal.azure.com) och välj **Grupper** > **Alla grupper** > **Ny grupp**.
2. På bladet **Grupp** fyller du i de obligatoriska fälten så här:
    - **Grupptyp**: Säkerhet
    - **Gruppnamn**: Ange ett intuitivt namn (till exempel Fabrik 1-enheter)
    - **Medlemskapstyp**: Dynamisk enhet
3. Välj **Lägg till dynamisk fråga**.
4. På bladet **Regler för dynamiskt medlemskap** fyller du i fälten så här:
    - **Lägg till dynamisk medlemsregel**: Enkel regel
    - **Lägg till enheter där**: enrollmentProfileName
    - Välj **Matchning** i mittenrutan.
    - I det sista fältet anger du registreringsprofilnamnet som du har skapat tidigare.
    Mer information om regler för dynamiskt medlemskap finns i [Regler för dynamiskt medlemskap för grupper i AAD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Välj **Lägg till fråga** > **Skapa**.

### <a name="replace-or-remove-tokens"></a>Ersätta eller ta bort token

Du kan ersätta eller ta bort token och QR-koder.

- **Ersätt token**: Du kan generera en ny token/QR-kod när en håller på att gå ut genom at använda Ersätt token.
- **Återkalla token**: Du kan omedelbart återkalla token/QR-koden. Då kan token/QR-koden inte längre användas. Du kan använda det här alternativet om du:
    - av misstag delar token/QR-koden med en obehörig part
    - slutför alla registreringar och inte längre behöver token/QR-koden

När du ersätter eller återkallar en token/QR-kod påverkar inte enheter som redan har registrerats.

1. Gå till [Intune-portalen](https://portal.azure.com) och välj **Enhetsregistrering** > **Android-registrering** > **Registreringar av kiosk- och uppgiftsenheter**.
2. Välj den profil du vill arbeta med.
3. Välj **Token**.
4. Välj **Ersätt token** om du vill ersätta token.
5. Välj **Återkalla token** om du vill återkalla token.

## <a name="enroll-the-kiosk-devices"></a>Registrera kioskenheterna

När du har skapat registreringsprofilen och den dynamiska enhetsgruppen kan du registrera dina kioskenheterna. Hur du registrerar dina Android-enheter beror på operativsystem.

| Registreringsmetod | Lägsta Android OS-version som stöds |
| ----- | ----- |
| NFC (Near Field Communication) | 5.1 |
| Token | 6.0 |
| QR-kod | 7.0 |
| Zero Touch | 8.0, för deltagande tillverkare |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Registrera med NFC (Near Field Communication)

För enheter med Android 5.1 och senare som stöder NFC kan du etablera enheter genom att ange en särskilt formaterad NFC-tagg. Du kan använda en egen app eller valfritt verktyg som skapar NFC-taggar. Mer information finns i [Googles dokumentation om API för hantering av Android](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Registrera med en token

För enheter med Android 6 och senare kan du använda token för att registrera enheten. I Android 6.1 och senare versioner kan du även skanna QR-koder när du använder registreringsmetoden **aft#setup**.

1. Starta den rensade enheten.
2. Välj språk på **välkomstskärmen**.
3. Anslut till ditt **Wi-Fi** och välj **NÄSTA**.
4. Acceptera Googles villkor och välj **NÄSTA**.
5. På Googles inloggningsskärm anger du **afw#setup** istället för ett Gmail-konto och sedan **NÄSTA**.
6. Välj **INSTALLERA** för appen **Android Device Policy**.
7. Fortsätt installationen av principen.  Vissa enheter kan kräva ytterligare godkännande av villkor. 
8. På skärmen **Registrera den här enheten** låter du din enhet skanna QR-koden eller så väljer du att ange token manuellt.
9. Följ anvisningarna på skärmen för att slutföra registreringen. 

### <a name="enroll-by-using-a-qr-code"></a>Registrera med QR-kod

På enheter med Android 7 och senare kan du skanna QR-koden från registreringsprofilen för att registrera enheten.

> [!Note]
> Webbläsarens zoom kan göra att enheter inte kan skanna QR-koder. Du löser problemet genom att öka webbläsarens zoom.

1. Starta en QR-läsning på Android-enheten genom att trycka flera gånger på den första skärmen du ser efter en rensning.
2. För enheter med Android 7 och 8 devices uppmanas du att installera en QR-läsare. Enheter med Android 9 och senare har redan en installerad QR-läsare.
3. Använd QR-lädaren för att skanna registreringsprofilens QR-kod och följ sedan anvisningarna på skärmen för att registrera.

### <a name="enroll-by-using-google-zero-touch"></a>Registrera genom att använda Google Zero Touch

Om du vill använda Googles Zero Touch-system måste enheten ha stöd för det och vara kopplad till en leverantör som är en del av tjänsten.  Mer information finns på [webbplatsen för Googles Zero Touch-program](https://www.android.com/enterprise/management/zero-touch/). 


1. Skapa en ny konfiguration i Zero Touch-konsolen.
2. Välj **Microsoft Intune** i listrutan EMM DPC.
3. I Googles Zero Touch-konsol kopierar du och klistrar in följande JSON i fältet DPC extras. Ersätt strängen *YourEnrollmentToken* med den registreringstoken du har skapat som en del av din registreringsprofil. Omge registreringstoken med dubbla citattecken.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Välj **Använd**.

## <a name="managing-apps-on-android-kiosk-devices"></a>Hantera appar på Android-kioskenheter

Det är bara appar med tilldelningstypen [Obligatorisk](apps-deploy.md#to-assign-an-app) som kan installeras på Android-kioskenheter. Appar installeras från Managed Google Play Butik på samma sätt som Android-arbetsprofilenheter.

Appar uppdateras automatiskt på hanterade enheter när apputvecklaren publicerar en uppdatering på Google Play.

Om du vill ta bort en app från Android-kioskenheter kan du göra något av följande:
-   Ta bort den obligatoriska appdistributionen.
-   Skapa en avinstallation av distributionen för appen.


## <a name="next-steps"></a>Nästa steg
- [Distribuera Android-kioskappar](apps-deploy.md)
- [Lägga till Android-kioskkonfigurationsprinciper](device-profiles.md)
