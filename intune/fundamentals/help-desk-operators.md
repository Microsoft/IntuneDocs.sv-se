---
title: Supportavdelningens felsökningsportal
titleSuffix: Microsoft Intune
description: Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0094cdd12b2594cb60260d768daec8c5bed04c9c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510251"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Använd felsökningsportalen för att hjälpa användare i ditt företag

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I felsökningsportalen kan supportansvariga och Intune-administratörer se användarinformation för att tillgodose användarnas begäran om hjälp. Organisationer som har en supportavdelning kan tilldela rollen **supportavdelning** till en grupp användare. Rollen som supportansvarig kan nu använda **felsökningsfönstret**.

Fönstret **Felsökning** visar nu även problem med användarregistreringen. Information om problemet och förslagna lösningar kan hjälpa administratörer och medarbetare på supportavdelningen att felsöka problem. Vissa problem med registreringen inte fångas upp, och vissa fel kanske inte har några reparationsförslag.

Anvisningar om att lägga till rollen supportansvarig finns i [Rollbaserad administrationskontroll (RBAC) med Intune](/intune/role-based-access-control)

När en användare kontaktar supporten om ett tekniskt problem i Intune kan supportansvarig ange användarens namn. Intune visar användbara data som kan hjälpa dig att lösa många nivå 1-problem, inklusive:

- Användarstatus
- Tilldelningar
- Efterlevnadsproblem
- Enheten svarar inte
- Enheten saknar VPN- eller Wi-Fi-inställningar
- Appinstallationsfel

## <a name="to-review-troubleshooting-details"></a>Granska information om felsökning

I felsökningsfönstret kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter.  

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Felsök** i fönstret **Intune**.
4. Klicka på **Välj** för att välja en användare att felsöka.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Välj**. Felsökningsinformationen för användaren visas i fönstret Felsökning. Följande tabell förklarar informationen.

> [!Note]  
> Du kan också få åtkomst till **felsökningsfönstret** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Områden för felsökning av instrumentpanelen

Du kan använda fönstret **Felsökning** för att granska användarinformation.

![Fel söknings instrument panel med numrerade områden som beskrivs i följande tabell](./media/help-desk-operators/troubleshooting-dash.png)

| Område | Namn | Beskrivning |
| ---  | ---  | ---         |
| 1.   | Kontostatus  | Visar status för aktuell Intune-klient som **Aktiv** eller **Inaktiv**.       |
| 2.   | Val av användare  | Namnet på den valda användaren. Välj en ny användare genom att klicka på **Ändra användare**.       |
| 3.   | Användarstatus  | Visar status för användarens Intune-licens, antal enheter, varje enhetskompatibilitet, antalet appar och appkompatibilitet.       |
| 4.   | Användarinformation  | Använd listan för att välja information som du vill läsa i fönstret. <br>Du kan välja: <ul><li>Klientappar<li>Efterlevnadsprinciper<li> Konfigurationsprinciper<li>Appskyddsprinciper <li>Registreringsbegränsningar</ul>      |
| 5.   | Gruppmedlemskap  | Visar de grupper som den valda användaren är medlem i.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>Referens för registreringsfel

Tabellen för registreringsfel visar misslyckade registreringsförsök. En enhet som visas i tabellen nedan kan ha registrerats korrekt vid ett senare försök. Vissa misslyckade försök kanske inte visas. Åtgärdsinformation är inte tillgänglig för alla fel.

| Tabellkolumn | Beskrivning |
|-------------|----------|
| Registreringsstart | Starttiden när användaren påbörjade registreringen. |
| Operativsystem | Enhetens operativsystem. |
| OS-version | Enhetens operativsystemversion. |
| Fel | Orsaken till felet. |

### <a name="failure-details"></a>Information om felet

När du väljer en felrad visas mer information.

| Avsnitt | Beskrivning |
|-------------|----------|
| Information om felet | En mer detaljerad förklaring av felet. |
| Potentiella åtgärder | Föreslagna steg för att lösa problemet. Vissa fel kanske inte har någon rekommenderad åtgärd. |
| Resurser (valfritt) | Länkar till ytterligare läsning eller områden på portalen där du kan vidta åtgärder. |

### <a name="enrollment-errors"></a>Registreringsfel

| Fel | Information |
|-------------|----------|
| iOS-timeout eller iOS-fel | En timeout mellan enheten och Intune som beror på att användaren tar för lång tid på sig att slutföra registreringen. |
| Användaren hittades inte eller är inte licensierad | Användaren saknar en licens eller har tagits bort från tjänsten. |
| Enheten är redan registrerad | Någon har försökt registrera en enhet med hjälp av företagsportalen på en enhet som fortfarande är registrerad av en annan användare. |
| Inte registrerad i Intune | En registrering gjordes när MDM-utfärdaren (hantering av mobilenheter) för Intune inte hade konfigurerats. |
| Registreringsauktoriseringen misslyckades | Ett registreringsförsök gjordes med hjälp av en äldre version av företagsportalen. |
| Enheten stöds inte | Enheten uppfyller inte minimikraven för Intune-registrering. |
| Registreringsbegränsningarna uppfylls inte | Registreringen blockerades på grund av att en administratör har konfigurerat registreringsbegränsningar. |
| Enhetsversionen är för låg | Administratören har konfigurerat en registreringsbegränsning som kräver en högre enhetsversion. |
| Enhetsversionen är för hög | Administratören har konfigurerat en registreringsbegränsning som kräver en lägre enhetsversion. |
| Enheten kan inte registreras som privat | Administratören har konfigurerat en registreringsbegränsning för att blockera privata registreringar och enheten som misslyckades var inte fördefinierad som företagsenhet. |
| Enhetsplattform har blockerats | Administratören har konfigurerat en registreringsbegränsning som blockerar den här enhetens plattform. |
| Masstoken har upphört att gälla | Masstoken i konfigurationspaketet har upphört att gälla. |
| Autopilot-enheten eller informationen hittades inte | Autopilot-enheten hittades inte vid försök till registrering. |
| Autopilot-profilen hittades inte eller har inte tilldelats | Enheten har ingen aktiv Autopilot-profil. |
| Oväntad registreringsmetod för Autopilot | Enheten försökte registrera med en otillåten metod. |
| Autopilot-enheten har tagits bort | Enheten som försökte registrera har tagits bort från Autopilot för det här kontot. |
| Enhetstaket har nåtts | Registreringen blockerades på grund av att en administratör har konfigurerat enhetsbegränsningar. |
| Apple-registrering | Inga iOS-enheter registrerades vid detta tillfälle eftersom ett Apple MDM-pushcertifikat i Intune saknas eller har upphört att gälla. |
| Enheten har inte förregistrerats | Enheten har inte förregistrerats som företagsägd och alla personliga registreringar blockerades av en administratör. |
| Funktionen stöds inte | Användaren försökte antagligen registrera via en metod som inte är kompatibel med din Intune-konfiguration. |

## <a name="collect-available-data-from-mobile-device"></a>Samla in tillgängliga data från mobil enhet

Använd följande resurser för att samla in enhetsdata när du felsöker problem med användarens enheter:
- [Skicka iOS-registreringsfel till IT-administratören](/intune-user-help/send-errors-to-your-it-admin-ios)
- [Hjälp företagets support att åtgärda enhetsproblem med hjälp av utförlig loggning](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
- [Skicka Android-loggar till företagets support via en USB-kabel](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [Skicka loggar med Android-diagnostikdata till IT-administratören via e-post](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [Skicka Android-registreringsfel till IT-administratören](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Nästa steg

Du kan läsa mer om rollbaserad administrationskontroll (RBAC) för att definiera roller till organisationens enheter, hantering av mobilprogram och dataskyddsåtgärder. Mer information finns i [Rollbaserad administrationskontroll (RBAC) med Intune](/intune/role-based-access-control).

Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kända problem i Microsoft Intune](/intune/known-issues).

Lär dig hur du skapar ett supportärende och får hjälp när du behöver det. [Få support](/intune/get-support).
