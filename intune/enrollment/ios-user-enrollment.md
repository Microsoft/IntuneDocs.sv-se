---
title: Registrera iOS-enheter – Användarregistrering
titleSuffix: Microsoft Intune
description: Lär dig hur du konfigurerar Användarregistrering för iOS och iPad.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e538204306ce80d6a13739fc981edf2748a622de
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713454"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>Konfigurera Användarregistrering för iOS och iPadOS (förhandsversion)

Du kan konfigurera registreringen av iOS- och iPad-enheter i Intune med hjälp av Apples användarregistreringsprocess. Med Användarregistrering får administratörer tillgång till en enklare deluppsättning hanteringsalternativ jämfört med andra registreringsmetoder.

Mer information om vilka alternativ som är tillgängliga med Användarregistrering finns i [Åtgärder, lösenord och andra alternativ som stöds i Användarregistrering](ios-user-enrollment-supported-actions.md).

> [!NOTE]
> Stöd för Apples användarregistrering i Intune är för närvarande tillgänglig som en förhandsversion.

## <a name="prerequisites"></a>Krav
- [Utfärdare för hantering av mobil enhet (MDM)](../fundamentals/mdm-authority-set.md)
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- [Hanterade Apple-ID:n](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Skapa en profil för Användarregistrering i Intune

En registreringsprofil definierar inställningarna som tillämpas på en grupp enheter vid registreringen. 

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringstyper (förhandsversion)**  > **Skapa profil** > **iOS**. I den här profilen väljer du registreringsupplevelsen för iOS- och iPad-slutanvändare på enheter som inte har registrerats via en företagsspecifik Apple-metod. Om du vill göra ändringar kan du redigera profilen i efterhand.

    ![Skapa en Apple-registreringsprofil](./media/ios-user-enrollment/create-profile.png)

2. På sidan **Grundinställningar**, anger du ett **Namn** och **Beskrivning** för profilen för administrationssyfte. Användarna kan inte se den här informationen. Du kan använda fältet **Namn** för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om [dynamiska Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Sidan Grundinställningar](./media/ios-user-enrollment/basics-page.png)


3. Välj **Nästa**.

4. På sidan **Inställningar** kan du välja att ge användarna möjlighet att välja typen av registrering. Alternativt kan du ange ett standardvärde.

    ![Sidan Inställningar](./media/ios-user-enrollment/settings-page.png)

    - Följ dessa steg om du vill att alla användare i den här profilen ska använda Användarregistrering:
        1. Välj **Inte konfigurerat** för **Användaren måste välja enhetstyp**.
        2. Välj **Användarregistrering** för **Standardregistreringstyp**.
    - Följ dessa steg om du vill att alla användare i den här profilen ska använda Enhetsregistrering:
        1. Välj **Inte konfigurerat** för **Användaren måste välja enhetstyp**.
        2. Välj **Enhetsregistrering** för **Standardregistreringstyp**.
    - Om du vill att användarna i den här gruppen ska kunna välja registreringstypen väljer du **Obligatorisk** för **Användaren måste välja enhetstyp**. När användarna registrerar sina enheter kan de välja mellan **Jag äger den här enheten** och **(Företaget) äger den här enheten**. Om de väljer det första alternativet registreras enheten via Användarregistrering. Om de väljer det andra alternativet registreras enheten via Enhetsregistrering. Om användaren väljer **Jag äger den här enheten** måste han eller hon välja om hela enheten ska skyddas eller endast arbetsrelaterade appar och data. Vilket alternativ slutanvändaren väljer vad gäller ägarskap av enheten avgör endast vilken typ av registrering som implementeras på deras enheter. Det här användarvalet visas inte i attributet Ägarskap för enhet i Intune. Mer information om användarupplevelsen finns i [Konfigurera iOS-enhetsåtkomst till företagsresurser](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).
    
    > [!NOTE]
    > Följande meddelande är fel och kommer att tas bort från användargränssnittet.
    > ”För att villkorlig åtkomst ska fungera på enheter som kräver Användarregistrering måste du distribuera Azure Authenticator-appen som en obligatorisk app till den här användargruppen för att aktivera Enkel inloggning och Workplace Join.”
    > Som administratör behöver du inte vidta några åtgärder för att distribuera Authenticator-appen till dina användare. Användarna uppmanas att installera Authenticator-appen i företagsportalappen för att slutföra användarregistreringen och säkerställa att dessa scenarier fungerar korrekt.

5. Välj **Nästa**.

6. På sidan **Tilldelningar** väljer du användargrupperna som innehåller de användare som du vill tilldela den här profilen till. Du kan välja att tilldela profilen till alla användare eller till specifika grupper. Alla användare i de valda grupperna använder den registreringstyp du valt ovan. Enhetsgrupper stöds inte i användarregistreringsscenarier eftersom funktionen baseras på användaridentiteter i stället för enheter. Du kan välja att tilldela profilen till alla användare eller till specifika grupper.

    ![Sidan Tilldelningar](./media/ios-user-enrollment/assignments-page.png)

7. Välj **Nästa**.

8. Gå igenom dina val på sidan **Granska och skapa** och tilldela profilen till användarna genom att välja **Skapa**.

    ![Sidan Tilldelningar](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>Profilprioritet

När du har skapat mer än en profil för registreringstyper kan du ändra profilernas prioritetsordning.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringstyper (förhandsversion)** .
2. Dra och släpp profilerna i listan i den ordning som de ska tillämpas.

Om det uppstår konflikter mellan profiler för en användare används profilen med högre prioritet för användaren.


