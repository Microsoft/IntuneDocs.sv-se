---
title: Anslut ditt Intune-konto till ditt hanterade Google Play-konto.
titleSuffix: Microsoft Intune
description: Läs om hur du ansluter ditt Intune-konto till ditt hanterade Google Play-konto.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19efd0821deeac0e76c60ee67e6230da554391a0
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567393"
---
# <a name="connect-your-intune-account-to-your-managed-google-play-account"></a>Ansluta ditt Intune-konto till ditt hanterade Google Play-konto

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

För att kunna stödja [Android Enterprise-arbetsprofiler](android-work-profile-enroll.md), [fullständigt hanterade Android Enterprise-enheter](android-fully-managed-enroll.md) och [dedikerade Android Enterprise-enheter](android-kiosk-enroll.md), måste du ansluta ditt Intune-klientkonto till ditt hanterade Google Play-konto.  

> [!NOTE]
> På grund av interaktion mellan Google- och Microsoft-domäner kan det i det här steget krävas att du justerar inställningarna för webbläsaren.  Se till att ”portal.azure.com” och ”play.google.com” finns i samma säkerhetszon i webbläsaren.

1. Om du inte redan gjort det, förbereder du för hantering av mobila enheter genom att ange **Microsoft Intune** som [utfärdare för hantering av mobila enheter](mdm-authority-set.md).
2. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal), välj **Enhetsregistrering** > **Android-registrering** > **Hanterat Google Play-konto**.  Om du använder en anpassad Intune-administratörsroll krävs läs- och uppdateringsbehörigheter för organisationen för åtkomst till detta.
   
   ![Sidan för Android enterprise-registrering](./media/android-work-bind.png)

3. Välj **Jag accepterar** för att ge Microsoft behörighet att [skicka information om användare och enhet till Google](data-intune-sends-to-google.md). 
   
4. Välj **Starta Google för att ansluta nu** för att öppna Managed Google Play-webbplatsen. Webbplatsen öppnas på en ny flik i webbläsaren.
  
5. Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla Android Enterprise-hanteringsuppgifter för den här klienten. Det här är det Google-konto som företagets IT-administratörer delar för att hantera och publicera appar i Google Play-konsolen. Du kan använda ett befintligt Google-konto eller skapa ett nytt. Det konto du väljer får inte vara kopplat till en G Suite-domän.
    
    > [!Note]
    > Om du använder webbläsaren Microsoft Edge klickar du på **Logga in** i det övre högra hörnet för att logga in på ditt Google-konto.

6. Ange företagets namn för **Organisationsnamn**. **Microsoft Intune** ska visas som **Enterprise mobility management (EMM)-provider**.

7. Godkänn Android-avtalet och välj sedan **Bekräfta**. Din begäran kommer att behandlas.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Koppla från ditt administrativa Android Enterprise-konto

Du kan inaktivera Android Enterprise-registrering och -hantering. Om du vill göra detta måste du först dra tillbaka alla registrerade Android Enterprise-arbetsprofilenheter. Sedan väljer du **Koppla från** i Intune-administrationskonsolen för att ta bort alla registrerade Android Enterprise-arbetsprofilenheter och dedikerade enheter från registrering. Det här tar även bort relationen mellan det hanterade Google Play-kontot och Intune.

1. Som Intune-administratör väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune** i [Azure-portalen](https://portal.azure.com).
2. Välj **Enhetsregistrering** > **Android-registrering** > **Hanterat Google Play-konto** > **Koppla från**.
3. Välj **Ja** för att koppla från och avregistrera alla Android enterprise-enheter från Intune.

## <a name="next-steps"></a>Nästa steg

När du har anslutit till det hanterade Google Play-kontot kan du [konfigurera Android Enterprise-arbetsprofilenheter](android-work-profile-enroll.md) och [dedikerade Android Enterprise-enheter](android-kiosk-enroll.md).
