---
title: Konfigurera Intune-registrering för dedikerade Android Enterprise-enheter
titleSuffix: Microsoft Intune
description: Lär dig att registrera dedikerade Android Enterprise-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e07952b6e7147ffa9b84cfbd1988ebb927b411dd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723573"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>Konfigurera Intune-registrering av dedikerade Android Enterprise-enheter

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android Enterprise stöder företagsägda engångsenheter av kiosktyp med dess dedikerade lösningsuppsättning. Sådana enheter används bara för ett ändamål, till exempel digitala skyltar, biljettutskrifter eller lagerhantering. Administratörer låser användningen av enheten för en begränsad uppsättning appar och webblänkar. Användarna kan heller inte lägga till andra appar eller att vidta andra åtgärder på enheten.

Intune hjälper dig att distribuera appar och inställningar till dedikerade Android Enterprise-enheter. Specifik information om Android Enterprise finns i [Krav för Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Enheter som du hanterar på det här sättet registreras i Intune utan ett användarkonto och kopplas inte till någon slutanvändare. De är inte avsedda för program eller appar för personligt bruk som har starka krav på användarspecifika kontodata, till exempel Outlook eller Gmail.

## <a name="device-requirements"></a>Krav på enheten

Enheter måste uppfylla följande krav för att kunna hanteras som en dedikerad Android Enterprise-enhet:

- Android OS version 5.1 och senare.
- Enheter måste köra en distribution av Android som har anslutningsfunktioner för Google Mobile Services (GMS). Enheter måste ha GMS tillgängligt för att kunna ansluta till GMS.

## <a name="set-up-android-enterprise-dedicated-device-management"></a>Konfigurera hantering av dedikerade Android Enterprise-enheter

Konfigurera hanteringen av dedikerade Android Enterprise-enheter så här:

1. Förbered hantering av mobila enheter genom att [ange MDM-utfärdare som **Microsoft Intune**](../fundamentals/mdm-authority-set.md) för instruktioner. Du anger det här objektet bara när du konfigurerar Intune för hantering av mobila enheter.
2. [Anslut ditt Intune-klientkonto till ditt hanterade Google Play-konto](connect-intune-android-enterprise.md).
3. [Skapa en registreringsprofil](#create-an-enrollment-profile).
4. [Skapa en enhetsgrupp](#create-a-device-group).
5. [Registrera de dedikerade enheterna](#enroll-the-dedicated-devices).

### <a name="create-an-enrollment-profile"></a>Skapa en registreringsprofil

> [!NOTE]
> Om en token har upphört att gälla visas inte profilen som är kopplad till den i **Enhetsregistrering** > **Android-registrering** > **Företagsägda dedikerade enheter**. Om du vill se alla profiler som är kopplade till både aktiva och inaktiva token klickar du på **Filtrera** och markera kryssrutorna för principtillståndet ”Aktiv” såväl som ”Inaktiv”. 

Du måste skapa en registreringsprofil så att du kan registrera dina dedikerade enheter. När profilen har skapats får den en registreringstoken (slumpmässig sträng) och en QR-kod. Beroende på enhetens Android OS-version kan du använda token eller QR-koden för att [registrera den dedikerade enheten](#enroll-the-dedicated-devices).

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Enhetsregistrering** > **Android-registrering** > **Företagsägda dedikerade enheter**.
2. Välj **Skapa** och fyll i de obligatoriska fälten.
    - **Namn**: Skriv ett namn som ska användas när du tilldelar profilen till den dynamiska enhetsgruppen.
    - **Förfallodatum för token**: Det datum när token upphör att gälla. Google använder ett maxvärde på 90 dagar.
3. Spara profilen genom att välja **Skapa**.

### <a name="create-a-device-group"></a>Skapa en enhetsgrupp

Du kan rikta appar och principer till tilldelade eller dynamiska enhetsgrupper. Du kan konfigurera dynamiska AAD-enhetsgrupper att automatiskt fylla i enheter som har registrerats med den viss registreringsprofil med hjälp av följande steg:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Grupper** > **Alla grupper** > **Ny grupp**.
2. På bladet **Grupp** fyller du i de obligatoriska fälten så här:
    - **Grupptyp**: Säkerhet
    - **Gruppnamn:** Ange ett intuitivt namn (till exempel Fabrik 1-enheter)
    - **Typ av medlemskap**: Dynamisk enhet
3. Välj **Lägg till dynamisk fråga**.
4. På bladet **Regler för dynamiskt medlemskap** fyller du i fälten så här:
    - **Lägg till dynamisk medlemskapsregel**: Enkel regel
    - **Lägg till enheter där**: enrollmentProfileName
    - Välj **Matchning** i mittenrutan.
    - I det sista fältet anger du registreringsprofilnamnet som du har skapat tidigare.
    Mer information om regler för dynamiskt medlemskap finns i [Regler för dynamiskt medlemskap för grupper i AAD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Välj **Lägg till fråga** > **Skapa**.

### <a name="replace-or-remove-tokens"></a>Ersätta eller ta bort token

- **Ersätt token**: Du kan generera en ny token/QR-kod som håller på att förfalla med hjälp av Ersätt token.
- **Återkalla token**: Du kan omedelbart återkalla token/QR-koden. Då kan token/QR-koden inte längre användas. Du kan använda det här alternativet om du:
  - av misstag delar token/QR-koden med en obehörig part
  - slutför alla registreringar och inte längre behöver token/QR-koden

När du ersätter eller återkallar en token/QR-kod påverkar inte enheter som redan har registrerats.

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Enhetsregistrering** > **Android-registrering** > **Företagsägda dedikerade enheter**.
2. Välj den profil du vill arbeta med.
3. Välj **Token**.
4. Välj **Ersätt token** om du vill ersätta token.
5. Välj **Återkalla token** om du vill återkalla token.

## <a name="enroll-the-dedicated-devices"></a>Registrera de dedikerade enheterna

Du kan nu [registrera dina dedikerade enheter](android-dedicated-devices-fully-managed-enroll.md).

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>Hantera appar på dedikerade Android Enterprise-enheter

Det är bara appar med tilldelningstypen [Obligatorisk](../apps/apps-deploy.md#assign-an-app) som kan installeras på dedikerade Android Enterprise-enheter. Appar installeras från den hanterade Google Play-butiken på samma sätt som Android Enterprise-arbetsprofilenheter.

Appar uppdateras automatiskt på hanterade enheter när apputvecklaren publicerar en uppdatering på Google Play.

Om du vill ta bort en app från dedikerade Android Enterprise-enheter kan du göra något av följande:
- Ta bort den obligatoriska appdistributionen.
- Skapa en avinstallation av distributionen för appen.

## <a name="next-steps"></a>Nästa steg
- [Distribuera Android-appar](../apps/apps-deploy.md)
- [Lägga till Android-konfigurationsprinciper](../configuration/device-profiles.md)
