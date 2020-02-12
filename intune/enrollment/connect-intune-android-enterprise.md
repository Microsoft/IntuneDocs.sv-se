---
title: Anslut ditt Intune-konto till ditt hanterade Google Play-konto.
titleSuffix: Microsoft Intune
description: Läs om hur du ansluter ditt Intune-konto till ditt hanterade Google Play-konto.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 581d88e49391bc874625e9c84318c039706b0c1b
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124834"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Ansluta ditt Intune-konto till ditt hanterade Google Play-konto

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

För att kunna stödja [Android Enterprise-arbetsprofiler](android-work-profile-enroll.md), [fullständigt hanterade Android Enterprise-enheter](android-fully-managed-enroll.md) och [dedikerade Android Enterprise-enheter](android-kiosk-enroll.md), måste du ansluta ditt Intune-klientkonto till ditt hanterade Google Play-konto.  

Intune lägger automatiskt till fyra vanliga Android Enterprise-relaterade appar till Intune-administratörskonsolen när du ansluter till Google Play för att göra det enklare för dig att konfigurera och använda Android Enterprise-hantering. Detta är de fyra Android Enterprise-apparna:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** – Används för fullständigt hanterade Android Enterprise-scenarier.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** – Hjälper dig att logga in på dina konton om du använder tvåfaktorautentisering.
- **[Intune-företagsportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** – Används för appskyddsprinciper och scenarier med Android Enterprise-arbetsprofiler.
- [Managed Home Screen](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) – Används för dedikerade/helskärmslägesscenarier i Android Enterprise.

> [!NOTE]
> På grund av interaktion mellan Google- och Microsoft-domäner kan det i det här steget krävas att du justerar inställningarna för webbläsaren.  Se till att ”portal.azure.com” och ”play.google.com” finns i samma säkerhetszon i webbläsaren.

1. Om du inte redan gjort det, förbereder du för hantering av mobila enheter genom att ange **Microsoft Intune** som [utfärdare för hantering av mobila enheter](../fundamentals/mdm-authority-set.md).
2. Logga in på [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), välj **Enheter** > **Android** > **Android-registrering** > **Hanterat Google Play-konto**.  Om du använder en anpassad Intune-administratörsroll krävs läs- och uppdateringsbehörigheter för organisationen för åtkomst till detta.
   
   ![Sidan för Android enterprise-registrering](./media/connect-intune-android-enterprise/android-work-bind.png)

3. Välj **Jag accepterar** för att ge Microsoft behörighet att [skicka information om användare och enhet till Google](../protect/data-intune-sends-to-google.md). 
   
4. Välj **Starta Google för att ansluta nu** för att öppna Managed Google Play-webbplatsen. Webbplatsen öppnas på en ny flik i webbläsaren.
  
5. Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla Android Enterprise-hanteringsuppgifter för den här klienten. Det här är det Google-konto som företagets IT-administratörer delar för att hantera och publicera appar i Google Play-konsolen. Du kan använda ett befintligt Google-konto eller skapa ett nytt. Det konto du väljer får inte vara kopplat till en G Suite-domän.
    
    > [!Note]
    > Om du använder webbläsaren Microsoft Edge klickar du på **Logga in** i det övre högra hörnet för att logga in på ditt Google-konto.

6. Ange företagets namn för **Organisationsnamn**. **Microsoft Intune** ska visas som **Enterprise mobility management (EMM)-provider**.

7. Godkänn Android-avtalet och välj sedan **Bekräfta**. Din begäran kommer att behandlas.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Koppla från ditt administrativa Android Enterprise-konto

Du kan inaktivera Android Enterprise-registrering och -hantering. För att göra detta måste du först återkalla alla registrerade Android Enterprise-enheter, inklusive arbetsprofilenheter, dedikerade enheter och fullständigt hanterade enheter. Sedan väljer du **Koppla från** i Intune-administrationskonsolen för att ta bort alla registrerade Android Enterprise-arbetsprofilenheter, dedikerade enheter och fullständight hanterade enheter från registreringen. Det här tar även bort relationen mellan det hanterade Google Play-kontot och Intune.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) som Intune-administratör.
2. Välj **Enheter** > **Android** > **Android-registrering** > **Hanterat Google Play-konto** > **Koppla från**.
3. Välj **Ja** för att koppla från och avregistrera alla Android enterprise-enheter från Intune.

## <a name="next-steps"></a>Nästa steg

När du har anslutit till Google Play för företag-kontot kan du [konfigurera Android Enterprise-arbetsprofilenheter](android-work-profile-enroll.md) och [dedikerade Android Enterprise-enheter](android-kiosk-enroll.md) och [ställa in fullständigt hanterade Android Enterprise-enheter](android-fully-managed-enroll.md)
