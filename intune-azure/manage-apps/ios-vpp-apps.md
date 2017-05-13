---
title: "Hantera volyminköpta iOS-appar | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversionen av Intune Azure: Lär dig mer om hur du kan synkronisera appar som du har köpt i volym från iOS Store i Intune och sedan hantera och spåra deras användning."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: f9e8a5deb17ebb77d480213567e5ccf6550e3493
ms.openlocfilehash: 1909549b321f51069bb6ad83f2f245afbf60b7dd
ms.contentlocale: sv-se
ms.lasthandoff: 05/03/2017

---

# <a name="how-to-manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Så här hanterar du iOS-appar som du har köpt via ett volymköpsprogram med Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I iOS App Store kan du köpa flera licenser för en app som du vill använda i företaget. Det hjälper dig att minska det administrativa arbetet med att spåra flera köpta kopior av appar.

Microsoft Intune hjälper dig att hantera appar som du har köpt via det här programmet genom att importera licensinformationen från App Store, spåra hur många licenser som du har använt och hindra dig från att installera fler kopior av appen än du äger.

Du kan dessutom synkronisera, hantera och tilldela böcker som du har köpt från Apples butik för volymköpsprogram med Intune och tilldela dem till användarna. Använd arbetsbelastningen **Böcker** i Intune-portalen för att hantera böcker. Metoden för att hantera böcker är samma som du använder när du hanterar appar.
Du måste ha laddat ner en token för Apples volymköpsprogram för att kunna göra detta. För närvarande kan du endast tilldela böcker som en **obligatorisk** installation.
När du tilldelar en bok till en enhet måste enheten ha den inbyggda iBooks-appen installerad. Om den inte finns måste användaren installera appen på nytt för att kunna läsa boken. Du kan för närvarande inte använda Intune för att återställa borttagna inbyggda appar.


## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Hantera appar som köpts genom volyminköpsprogrammet för iOS-enheter
Du köper flera licenser för iOS-appar via [Apples volymköpsprogram för företag](http://www.apple.com/business/vpp/) eller [Apples volymköpsprogram för utbildning](http://volume.itunes.apple.com/us/store). När du gör det måste du bland annat skapa ett Apple VPP-konto från Apples webbplats och ladda upp din Apple VPP-token till Intune.  Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet.

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar måste du skaffa en VPP-token från Apple och ladda upp den till ditt Intune-konto. Du bör också känna till följande:

* Du kan associera flera token för volymköpsprogram till Intune-kontot.
* Om du tidigare har använt en VPP-token med en annan produkt måste du generera en ny som ska användas med Intune.
* Varje token är giltig i ett år.
* Som standard synkroniserar Intune med Apple VPP-tjänsten två gånger om dagen. Du kan starta en manuell synkronisering när som helst.
* När du har importerat VPP-token i Intune ska du inte importera samma token till andra enhetshanteringslösningar. Om du gör det kan licenstilldelningen och användarposter gå förlorade.
* Innan du börjar använda iOS VPP med Intune tar du bort alla befintliga VPP-användarkonton som skapats med andra MDM-leverantörer (hantering av mobila enheter). Intune synkroniserar inte de användarkontona till Intune som en säkerhetsåtgärd. Intune synkroniserar endast data från den Apple VPP-tjänst som skapades av Intune.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Så här skaffar du och laddar upp en Apple VPP-token

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
1.  I arbetsbelastningen **Mobilappar** väljer du **Installationsprogrammet** > **iOS VPP-token**.
2.  På listan över VPP-tokenblad, väljer du **Lägg till**.
3.  Ange följande information på bladet för ny VPP-token:
    - **VPP-tokenfil** – Om du inte redan gjort det, registrerar du dig för volymköpsprogram för företaget eller volymköpsprogram för utbildning. När du har registrerat dig laddar du ned Apple VPP-token för ditt konto och väljer det här.
    - **Apple-ID** – Ange Apple-ID för det konto som är associerat med inköpsprogrammet för volymen.
    - **Typ av VPP-konto** – Välj mellan **Företag** eller **Utbildning**.
4. När du är klar klickar du på **Ladda upp**.

Token visas i listan över tokenblad.


Du kan synkronisera data från Apple med Intune när som helst genom att välja **Synkronisera nu**.

## <a name="to-assign-a-volume-purchased-app"></a>Tilldela en volyminköpt app

1. I arbetsbelastningen **Hantera appar**, väljer du **Hantera** > **Licensierade appar**.
2. I listan över appblad, väljer du den app du vill tilldela och väljer sedan **...**  > **Tilldela grupper**.
3. På bladet <*appnamn*> - **Tilldelade grupper**, väljer du **hantera** > **Tilldelade grupper**.
4. Välj **Tilldela grupper**, klicka sedan på bladet **Välj grupper**, välj de Azure AD-användare eller enhetsgrupper som du vill tilldela appen.
Du måste välja en tilldelningsåtgärd för **Krävd**. Tilldelningar till enhetsgrupper är även tillgängliga för nya klienter som har skapats efter januari 2017. Om klienten har skapats före detta och du inte har tillgång till alternativet för att tilldela VPP-appar till enhetsgrupper kan du kontakta Intunes support.
5. När du är klar väljer du **Spara**.

Du hittar mer information i [Hur du övervakar appar](monitor-apps.md) som hjälper dig att övervaka apptilldelningar.

## <a name="further-information"></a>Ytterligare information

När du tilldelar appar som en **Krävd** installation använder alla användare som installerar appen en licens.

Om du vill frisläppa en licens måste du ändra tilldelningsåtgärden till **Avinstallera**. Licensen frisläpps när appen avinstalleras.

När användare med kvalificerande enheter försöker installera en VPP-app ombeds de att gå med i Apples volyminköpsprogram. De måste göra detta innan appinstallationen fortsätter.

När du tilldelar en VPP-app som Tillgänglig har appinnehåll och licens tilldelats direkt från appbutiken.

