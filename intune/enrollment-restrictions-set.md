---
title: Ange registreringsbegränsningar i Microsoft Intune
titlesuffix: ''
description: Begränsa registrering per plattform och ange en gräns för enhetsregistrering i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 99c69d08bb11ed097e2262938d254074169492c3
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="set-enrollment-restrictions"></a>Ange registreringsbegränsningar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du skapa och hantera registreringsbegränsningar som definierar antalet och typerna av enheter som kan registreras för hantering med Intune. Du kan skapa flera begränsningar och applicera dem på olika användargrupper. Du kan ange [prioriteringsordningen](#change-enrollment-restriction-priority) för dina olika begränsningar.

>[!NOTE]
>Begränsningar vid registrering ska inte betraktas som säkerhetsfunktioner. Komprometterade enheter kan ju utge sig för att vara en helt annan enhet. Det här är dock en bra barriär för att stänga ute användare utan skadliga avsikter.

>[!NOTE]
>Den grupptilldelade begränsningen för registrering och prioritetsfunktionen som nämns i den här artikeln håller på att distribueras bland Intune-kunderna. Du kanske inte har åtkomst till grupp- och prioritetsfunktionerna förrän den här distributionen är slutförd.

Bland de specifika registreringsbegränsningarna som du kan skapa finns:

- Högsta tillåtna antal registrerade enheter.
- Enhetsplattformar som får registreras:
  - Android.
  - Android for Work.
  - iOS.
  - macOS.
  - Windows.
- Version av plattformsoperativsystem för iOS, Android, Android for Work och Windows. (Endast Windows 10-versioner kan användas. Lämna tomt om Windows 8.1 tillåts.)
  - Lägsta version.
  - Högsta version.
- Begränsningar gentemot privatägda enheter (endast iOS, Android, Android for Work och macOS).

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

Du kan ändra inställningarna för en begränsning för enhetstyp genom att följa dessa steg:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter **Intune** och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Under **Begränsningar för enhetstyp** väljer du den begränsning som du vill ange.
5. Under begränsningsnamnet (**Alla användare** för begränsningen som är standard) väljer du **Plattformar**. Välj **Tillåt** eller **Blockera** för varje plattform som är med i listan.
6. Välj **Spara**.
7. Under begränsningsnamnet (**Alla användare** för standardbegränsning) väljer du **Plattformskonfigurationer**. Välj sedan lägsta och högsta **Versioner** för de plattformar som anges. Versioner som stöds inkluderar:
    - Stöd för major.minor.rev.build för Android och Android for Work.
    - iOS stöder major.minor.rev.
    - Windows stöder endast major.minor.rev.build för Windows 10.
  Operativsystemversionerna gäller inte för Apple-enheter som registreras med programmet för enhetsregistrering, Apple School Manager eller Apple Configurator-appen.
8. Ange om du vill **tillåta** eller **blockera** **personligt ägda** enheter för varje plattform i listan.
    ![Enhetsbegränsningar med standardkonfigurationer för enhetsplattformar visar inställningar för personligt ägda enheter](media/device-restrictions-platform-configurations.png)
9. Välj **Spara**.


>[!NOTE]
>- Om du blockerar registrering av personligt ägda Android-enheter kan du ändå registrera personligt ägda Android for Work-enheter.
>- Som standard är dina Android for Work-enhetsinställningar samma som inställningarna för dina Android-enheter. När du har ändrat dina Android for Work-inställningar kommer det här inte längre att vara fallet.
>- Om du blockerar registrering av personligt ägda Android for Work-enheter så kan endast företagsägda Android-enheter att registrera Android for Work.

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
