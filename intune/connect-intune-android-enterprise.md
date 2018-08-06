---
title: Ansluta ditt Intune-konto till ditt Android enterprise-konto
titlesuffix: Microsoft Intune
description: Lär dig hur du ansluter ditt Intune-konto till ditt Android enterprise-konto.
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
ms.custom: intune-azure
ms.openlocfilehash: 1b1f54486ab2c3d98e663cfddded346eb61662ae
ms.sourcegitcommit: e4832ea81b9a707a6ad0699a18c8b3988413c283
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279431"
---
# <a name="connect-your-intune-account-to-your-android-enterprise-account"></a>Ansluta ditt Intune-konto till ditt Android enterprise-konto

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

För att kunna stödja Android-arbetsprofilenheter och Android-kioskenheter måste du ansluta ditt Intune-klientkonto till ditt Android enterprise-konto. 

> [!NOTE]
> På grund av interaktion mellan Google- och Microsoft-domäner kan det i det här steget krävas att du justerar inställningarna för webbläsaren.  Se till att ”portal.azure.com” och ”play.google.com” finns i samma säkerhetszon i webbläsaren.

1. Om du inte redan gjort det, förbereder du för hantering av mobila enheter genom att ange **Microsoft Intune** som [utfärdare för hantering av mobila enheter](mdm-authority-set.md).
2. Logga in på [Intune i Azure Portal](https://aka.ms/intuneportal), välj **Enhetsregistrering** > **Android-registrering** > **Hanterat Google Play-konto**.  Om du använder en anpassad Intune-administratörsroll krävs läs- och uppdateringsbehörigheter för organisationen för åtkomst till detta.
   
   ![Sidan för Android enterprise-registrering](./media/android-work-bind.png)

3. Välj **Jag accepterar** för att ge Microsoft behörighet att [skicka information om användare och enhet till Google](data-intune-sends-to-google.md). 
   
4. Välj **Starta Google för att ansluta nu** för att öppna Managed Google Play-webbplatsen. Webbplatsen öppnas på en ny flik i webbläsaren.
  
5. Logga in på Googles inloggningssida med det Google-konto som ska associeras med alla hanteringsuppgifter för Android för företag för den här klienten. Det här är det Google-konto som företagets IT-administratörer delar för att hantera och publicera appar i Google Play-konsolen. Du kan använda ett befintligt Google-konto eller skapa ett nytt. Det konto du väljer får inte vara kopplat till en G Suite-domän.
    
    > [!Note]
    > Om du använder webbläsaren Microsoft Edge klickar du på **Logga in** i det övre högra hörnet för att logga in på ditt Google-konto.

6. Ange företagets namn för **Organisationsnamn**. **Microsoft Intune** ska visas som **Enterprise mobility management (EMM)-provider**.

7. Godkänn Android-avtalet och välj sedan **Bekräfta**. Din begäran kommer att behandlas.

## <a name="disconnect-your-android-enterprise-administrative-account"></a>Koppla från ditt administrativa Android enterprise-konto

Du kan inaktivera Android enterprise-registrering och -hantering. Om du vill göra detta måste du först dra tillbaka alla registrerade Android-arbetsprofilenheter. Sedan väljer du **Koppla från** i Intune-administrationskonsolen för att ta bort alla registrerade Android-arbetsprofilenheter och kioskenheter från registrering. Det här tar även bort relationen mellan Android enterprise-kontot och Intune.

1. Som Intune-administratör väljer du **Alla tjänster** > **Övervakning + hantering** > **Intune** i [Azure-portalen](https://portal.azure.com).
2. Välj **Enhetsregistrering** > **Android-registrering** > **Hanterat Google Play-konto** > **Koppla från**.
3. Välj **Ja** för att koppla från och avregistrera alla Android enterprise-enheter från Intune.

## <a name="next-steps"></a>Nästa steg

När du har anslutit till Android enterprise-kontot kan du [konfigurera Android-arbetsprofilenheter](android-work-profile-enroll.md) och [konfigurera Android-kioskenheter](android-kiosk-enroll.md).
