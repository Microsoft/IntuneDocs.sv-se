---
title: "Hantera volyminköpta iOS-appar"
titleSuffix: Intune on Azure
description: "Läs mer om synkronisering av volyminköpta appar från iOS store i Intune och hantering och spårning av deras användning.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16b7ce81eb63a81534af2911b34904d870ac41ad
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Så här hanterar du iOS-appar som du har köpt via ett volymköpsprogram med Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I iOS App Store kan du köpa flera licenser för en app som du vill använda i företaget. Köp av flera exemplar av en app hjälper dig att minska det administrativa arbetet med att spåra flera köpta exemplar av appar.

Microsoft Intune hjälper dig att hantera appar som du har köpt via det här programmet genom att:

- Importera licensinformationen från appbutiken
- Spåra antalet använda licenser
- Hindra dig från att installera ytterligare exemplar av en app du äger

Du kan dessutom synkronisera, hantera och tilldela böcker som du har köpt från Apples butik för volymköpsprogram med Intune. Använd arbetsbelastningen **Böcker** i Intune-portalen för att hantera böcker. Metoden för att hantera böcker är samma som du använder när du hanterar appar.
Du måste ha laddat ner en token för Apples volymköpsprogram innan du börjar. För närvarande kan du endast tilldela böcker som en **obligatorisk** installation.
När du tilldelar en bok till en enhet måste enheten ha den inbyggda iBooks-appen installerad. Om den inte finns måste användaren installera appen på nytt för att kunna läsa boken. Du kan för närvarande inte använda Intune för att återställa borttagna inbyggda appar.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Hantera appar som köpts genom volyminköpsprogrammet för iOS-enheter
Du kan köpa flera licenser för iOS-appar via [Apples volymköpsprogram för företag](http://www.apple.com/business/vpp/) eller [Apples volymköpsprogram för utbildning](http://volume.itunes.apple.com/us/store). Processen innebär bland annat att skapa ett Apple VPP-konto från Apples webbplats och ladda upp en Apple VPP-token till Intune.  Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet.

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar måste du skaffa en VPP-token från Apple och ladda upp den till ditt Intune-konto. Du bör också känna till följande kriterier:

* Du kan associera flera token för volymköpsprogram till Intune-kontot.
* Om du tidigare har använt en VPP-token med en annan produkt måste du generera en ny som ska användas med Intune.
* Varje token är giltig i ett år.
* Som standard synkroniserar Intune med Apple VPP-tjänsten två gånger om dagen. Du kan starta en manuell synkronisering när som helst.
* När du har importerat VPP-token i Intune ska du inte importera samma token till andra enhetshanteringslösningar. Om du gör det kan licenstilldelningen och användarposter gå förlorade.
* Innan du börjar använda iOS VPP med Intune tar du bort alla befintliga VPP-användarkonton som skapats med andra MDM-leverantörer (hantering av mobila enheter). Av säkerhetsskäl synkroniserar Intune inte dessa användarkonton till Intune. Intune synkroniserar endast data från den Apple VPP-tjänst som skapades av Intune.
* Intune har stöd för att lägga till upp till 256 VPP-token.
* Om du tilldelar en volyminköpt app till en enhet som har registrerats via en enhetsregistreringsprofil eller Apple Configurator, fungerar endast appar som är riktade till enheter. Du kan inte rikta volyminköpsappar för användare av en DEP-enhet som inte har någon användartillhörighet.
* En VPP-token har endast stöd för användning på ett Intune-konto i taget. Återanvänd inte samma VPP-token för flera Intune-klienter.
* När du tilldelar VPP-appar med hjälp av användarlicensieringsmodellen till användare eller enheter (med användartillhörighet), måste varje Intune-användare associeras med ett unikt Apple-ID eller en e-postadress när de accepterar Apples villkor på sin enhet.
När du ställer in en enhet för en ny Intune-användare ser du till att konfigurera den med användarens unika Apple-ID eller e-postadress. Kombinationen av Intune-användare och Apple-ID:t eller e-postadress bildar ett unikt par och kan användas på upp till 5 enheter.


## <a name="to-get-and-upload-an-apple-vpp-token"></a>Så här skaffar du och laddar upp en Apple VPP-token

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
1.  I arbetsbelastningen **Mobilappar** väljer du **Installationsprogrammet** > **iOS VPP-token**.
2.  På listan över VPP-tokenblad, väljer du **Lägg till**.
3.  På bladet **Ny VPP-token** anger du följande information:
    - **VPP-tokenfil** – Om du inte redan gjort det, registrerar du dig för volymköpsprogram för företag eller programmet för utbildning. När du har registrerat dig laddar du ned Apple VPP-token för ditt konto och väljer det här.
    - **Apple-ID** – Ange Apple-ID för det konto som är associerat med inköpsprogrammet för volymen.
    - **Typ av VPP-konto** – Välj mellan **Företag** eller **Utbildning**.
4. När du är klar klickar du på **Ladda upp**.

Token visas i listan över tokenblad.


Du kan synkronisera data från Apple med Intune när som helst genom att välja **Synkronisera nu**.

> [!NOTE]
> Microsoft Intune synkroniserar endast information om appar som finns tillgängliga för allmänheten via iTunes Store. **Anpassade B2B-appar för iOS** stöds inte än. Om ditt scenario använder sådana appar kommer informationen för dessa inte att synkroniseras.

## <a name="to-assign-a-volume-purchased-app"></a>Tilldela en volyminköpt app

1. I arbetsbelastningen **Hantera appar**, väljer du **Hantera** > **Licensierade appar**.
2. I listan över appblad, väljer du den app du vill tilldela och väljer sedan **...**  > **Tilldela grupper**.
3. På bladet <*appnamn*> - **Tilldelade grupper**, väljer du **hantera** > **Tilldelade grupper**.
4. Välj **Tilldela grupper**, klicka sedan på bladet **Välj grupper**, välj de Azure AD-användare eller enhetsgrupper som du vill tilldela appen.
Du måste välja en tilldelningsåtgärd för **Krävd**. Tilldelningar till enhetsgrupper är även tillgängliga för nya klienter som har skapats efter januari 2017. Om klienten skapades före det datumet och du inte har tillgång till alternativet för att tilldela VPP-appar till enhetsgrupper kan du kontakta Intunes support.
5. När du är klar väljer du **Spara**.

>[!NOTE]
>Listan över appar som visas är associerad med en token. Om du har en app som är associerad med flera VPP-token kan du se samma app visas flera gånger, en gång för varje token.

Du hittar mer information i [Hur du övervakar appar](apps-monitor.md) som hjälper dig att övervaka apptilldelningar.

## <a name="further-information"></a>Ytterligare information

När du tilldelar appar som en **Krävd** installation använder alla användare som installerar appen en licens.

Om du vill frisläppa en licens måste du ändra tilldelningsåtgärden till **Avinstallera**. Licensen frisläpps när appen avinstalleras.

När en användare med en kvalificerande enhet försöker installera en VPP-app ombeds användaren att gå med i Apples volyminköpsprogram. Användaren måste gå med innan appinstallationen fortsätter. Inbjudan att gå med i Apples program för volyminköp kräver att användaren kan använda appen iTunes på iOS-enheten. Om du har angett en princip för inaktivering av iTunes Store-appen kommer den användarbaserade licensieringen för VPP-appar inte att fungera. Lösningen är att antingen tillåta iTunes-appen genom att ta bort principen eller använda enhetsbaserad licensiering.

När du tilldelar en VPP-app som Tillgänglig har appinnehåll och licens tilldelats direkt från appbutiken.
