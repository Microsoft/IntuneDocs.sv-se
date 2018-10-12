---
title: Ange registreringsbegränsningar i Microsoft Intune
titlesuffix: ''
description: Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: de77ad92eac4aa869aec504f1762ad6f216c74d2
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602154"
---
# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du skapa och hantera registreringsbegränsningar som definierar antalet och typerna av enheter som kan registreras för hantering med Intune. Du kan skapa flera begränsningar och applicera dem på olika användargrupper. Du kan ange [prioriteringsordningen](#change-enrollment-restriction-priority) för dina olika begränsningar.

>[!NOTE]
>Begränsningar vid registrering ska inte betraktas som säkerhetsfunktioner. Komprometterade enheter kan ju utge sig för att vara en helt annan enhet. Det här är dock en bra barriär för att stänga ute användare utan skadliga avsikter.

Bland de specifika registreringsbegränsningarna som du kan skapa finns:

- Högsta tillåtna antal registrerade enheter.
- Enhetsplattformar som får registreras:
  - Android
  - Android-arbetsprofil
  - iOS
  - macOS
  - Windows
- Version av plattformsoperativsystem för iOS, Android, Android-arbetsprofil och Windows. (Endast Windows 10-versioner kan användas. Lämna tomt om Windows 8.1 tillåts.)
  - Lägsta version.
  - Högsta version.
- Begränsningar gentemot privatägda enheter (endast iOS, Android, Android-arbetsprofil, macOS och Windows).

## <a name="default-restrictions"></a>Standardbegränsningar

Standardbegränsningar tillhandahålls automatiskt för både begränsningar för enhetstyp och begränsningar för enhetsgränsregistrering. Du kan ändra alternativen för vad som är standard. Standardbegränsningarna gäller för alla användare och användarlösa registreringar. Du kan åsidosätta de här standardinställningarna genom att skapa nya begränsningar med högre prioritet.

## <a name="create-a-restriction"></a>Skapa en begränsning

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter **Intune** och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Välj **Skapa begränsning**.
5. Ange ett namn och en beskrivning för begränsningen.
6. Välj en **begränsningstyp** och välj sedan **Skapa**.
7. För begränsningar för enhetsgräns väljer du **Enhetsgräns** för att ange det maximala antalet enheter som en användare kan registrera.
8. För begränsningar för enhetstyp väljer du **Plattformar** och **Plattformskonfigurationer** för att tillåta eller blockera olika plattformar och versioner.
9. Välj **Tilldelningar** > **+ Välj grupper**.
10. Under **Välj grupper** väljer du en eller flera grupper och väljer sedan **Välj**. Begränsningen gäller endast för grupper som den är tilldelad till. Om du inte tilldelar en begränsning till minst en grupp så påverkar den inte något.
11. Välj **Spara**.
12. Den nya begränsningen skapas med prioritet precis ovanför standardvärdet. Du kan [ändra prioriteten](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Ange begränsningar för enhetstyp

Du kan ändra inställningarna för en begränsning för enhetstyp genom att följa stegen nedan. Dessa begränsningar påverkar inte enheter som redan har registrerats. Enheter som registreras med [Intune PC-agenten](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter **Intune** och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Under **Begränsningar för enhetstyp** väljer du den begränsning som du vill ange > **Egenskaper** > **Välj plattformar**. Välj **Tillåt** eller **Blockera** för varje plattform som är med i listan.
    ![Skärmbild för att tillåta eller blockera en plattform](media/enrollment-restrictions-set/platform-allow-block.png)
5. Välj **OK**.
6. Välj **Konfigurera plattformar**.
    ![Skärmbild för att konfigurera plattformar](media/enrollment-restrictions-set/configure-platforms.png)
7. Välj lägsta och högsta **Versioner** för de plattformar som anges. Versionsformat som stöds är:
    - Android-arbetsprofil har stöd för major.minor.rev.build.
    - iOS stöder major.minor.rev. Operativsystemversionerna gäller inte för Apple-enheter som registreras med programmet för enhetsregistrering, Apple School Manager eller Apple Configurator-appen.
    - Windows stöder endast major.minor.rev.build för Windows 10.
8. Välj om du vill **tillåta** eller **blockera** **personligt ägda** enheter för varje plattform i listan.
9. Välj **OK**.

### <a name="blocking-personal-android-devices"></a>Blockera personliga Android-enheter
- Om du blockerar registrering av personligt ägda Android-enheter kan du ändå registrera personligt ägda Android-arbetsprofilenheter.
- Som standard är dina inställningar för Android-arbetsprofilenheter samma som inställningarna för dina Android-enheter. När du har ändrat dina inställningar för Android-arbetsprofilenheter kommer det här inte längre att vara fallet.
- Om du blockerar registrering av personligt ägda Android-arbetsprofilenheter så kan endast företagsägda Android-enheter att registreras som Android-arbetsprofil.

### <a name="blocking-personal-windows-devices"></a>Blockera personliga Windows-enheter
Om du blockerar personligt ägda Windows-enheter från registrering så kontrollerar Intune att varje ny begäran om Windows-registrering har godkänts som en företagsregistrering. Obehöriga registreringar kommer att blockeras.

Följande metoder räknas som auktoriserade som Windows-företagsregistrering:
 - Den registrerande användaren använder ett [konto för enhetsregistreringshanteraren]( device-enrollment-manager-enroll.md).
- Enheten registreras via [Windows AutoPilot](enrollment-autopilot.md).
- Enheten registreras med Windows Autopilot men är inte ett enbart MDM-registreringsalternativ från Windows-inställningar.
- Enhetens IMEI-nummer anges i **Enhetsregistrering** > **[ID:n för företagsenheter](corporate-identifiers-add.md)**. (Stöds inte för Windows Phone 8.1.)
- Enheten registreras via ett [bulketableringspaket](windows-bulk-enroll.md).
- Enheten registreras via [automatisk registrering från SCCM för samhantering](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md).
 
Följande registreringar markeras som företagsregistreringar av Intune, men eftersom de inte innehåller per enhet-kontroll för Intune-administratören kommer de att blockeras:
 - [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Azure Active Directory-anslutning under Windows-installationen](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)\*.
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Azure Active Directory-anslutning från Windows-inställningar](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup.md)*.
 
Följande personliga registreringsmetoder blockeras också:
- [Automatisk MDM-registrering](windows-enroll.md#enable-windows-10-automatic-enrollment) med [Lägg till arbetskonto från Windows-inställningar](https://docs.microsoft.com/azure/active-directory/device-management-azuread-registered-devices-windows10-setup.md)\*.
- Alternativet [MDM enrollment only]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) (Endast MDM-registrering) från Windows-inställningarna.

\* Dessa kommer inte att blockeras om de registrerats med Autopilot.

## <a name="set-device-limit-restrictions"></a>Ange begränsningar för enhetsgräns

Du kan ändra inställningarna för en begränsning för enhetsgräns genom att följa dessa steg:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter **Intune** och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Under **Begränsningar för enhetsgräns** väljer du den begränsning som du vill ange.
5. Välj **Enhetsgräns** och sedan väljer du det maximala antalet enheter som en användare kan registrera i den nedrullningsbara listan.
    ![Bladet med begränsningar för enhetsgränsen](./media/device-restrictions-limit.png)
6. Välj **Spara**.


Ett meddelande visas för användarna med information om att de har uppnått gränsen för registrerade enheter. På iOS ser det till exempel ut så här:

![Avisering om enhetsbegränsning på iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Ändra prioritet för registreringsbegränsning

Prioritet används när en användare befinner sig i flera grupper som tilldelas begränsningar. Användarna berörs endast av begränsningen med högst prioritet som är tilldelad till en grupp där de finns. Till exempel är Jens i grupp A tilldelad begränsningar med prioritet 5 och i grupp B tilldelad begränsningar med prioritet 2. Jens berörs då endast av begränsningar med prioritet 2.

När du skapar en begränsning läggs den till i listan precis ovanför den som är standard.

Enhetsregistrering inkluderar standardbegränsningar för både enhetstyp och för enhetsgränsbegränsningar. De här två begränsningarna gäller för alla användare om de inte åsidosätts av begränsningar med högre prioritet.

Du kan ändra prioriteten för begränsningar som inte är standard.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter **Intune** och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Hovra över begränsningen i prioritetslistan.
5. Använd de tre lodräta punkterna och dra prioriteten till önskad plats i listan.
