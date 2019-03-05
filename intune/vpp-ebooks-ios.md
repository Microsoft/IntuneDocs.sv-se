---
title: Hantera volyminköpta e-böcker i iOS
titlesuffix: Microsoft Intune
description: Läs mer om hur du kan synkronisera böcker som du har köpt i volym från iOS Store till Intune och hur du sedan hanterar och spårar deras användning.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5617074-2384-4812-b913-dc94f64c0818
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: daed0da10a31d3429cf44bda8829369c741ba71a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57235556"
---
# <a name="how-to-manage-ios-ebooks-you-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Så här hanterar du e-böcker i iOS som du har köpt via ett volymköpsprogram med Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med Apples volymköpsprogram kan du köpa flera licenser för en bok som du vill distribuera till användare i ditt företag. Du kan distribuera böcker från Business- eller Education-butikerna.

Med Microsoft Intune kan du synkronisera, hantera och tilldela böcker som du köpt med detta program. Du kan importera licensinformation från butiken och spåra hur många licenser du har använt.

Procedurerna för att hantera böcker liknar att [hantera VPP-appar](vpp-apps-ios.md).

## <a name="manage-volume-purchased-books-for-ios-devices"></a>Hantera böcker som köpts genom volyminköpsprogrammet för iOS-enheter
Du köper flera licenser för e-böcker i iOS via [Apples volymköpsprogram för företag](https://www.apple.com/business/vpp/) eller [Apples volymköpsprogram för utbildning](https://volume.itunes.apple.com/us/store). Processen innebär bland annat att skapa ett Apple VPP-konto från Apples webbplats och ladda upp en Apple VPP-token till Intune.  Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av böcker som du köpt med volyminköpsprogrammet.

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar hämtar du en VPP-token från Apple och laddar upp den till ditt Intune-konto. Dessutom:

* Du kan associera upp till 256 VPP-tokens med ditt Intune-konto.
* Om du tidigare har använt en VPP-token med en annan produkt måste du generera en ny som ska användas med Intune.
* Varje token är giltig i ett år.
* Som standard synkroniserar Intune med Apple VPP-tjänsten två gånger om dagen. Du kan starta en manuell synkronisering när som helst.
* När du har importerat VPP-token i Intune ska du inte importera samma token till andra enhetshanteringslösningar. Om du gör det kan licenstilldelningen och användarposter gå förlorade.
* Innan du börjar använda iOS-böcker med Intune tar du bort alla befintliga VPP-användarkonton som skapats med andra MDM-leverantörer (hantering av mobilenheter). Av säkerhetsskäl synkroniserar Intune inte dessa användarkonton till Intune. Intune synkroniserar endast data från den Apple VPP-tjänst som skapades av Intune.
* När du tilldelar en bok till en enhet måste enheten ha den inbyggda iBooks-appen installerad. Om den inte finns måste slutanvändaren installera appen på nytt för att kunna läsa boken. Du kan för närvarande inte använda Intune för att återställa borttagna inbyggda appar.
* Du kan bara tilldela böcker från webbplatsen för Apples volymköpsprogram. Du kan inte ladda upp och sedan tilldela böcker som du skapat internt.
* Du kan för närvarande inte tilldela böcker till slutanvändarkategorier på samma sätt som du gör med appar.
* Du kan inte frigöra en licens när boken blivit tilldelad.
* När användare med en användbar enhet ska installera en VPP-bok, måste de ansluta till Apples volyminköpsprogram först. Du kan också tilldela licenser till säkerhetsgrupper med hanterade Apple-ID:n. Om du gör detta kommer användaren inte tillfrågas om sitt Apple-ID när en bok installeras.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Så här skaffar du och laddar upp en Apple VPP-token

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
1.  I arbetsbelastningen **Klientappar** väljer du **Installation** > **iOS VPP-token**.
2.  I listan med VPP-tokens klickar du på **Skapa**.
3.  I fönstret **Ny VPP-token** anger du följande information:
    - **VPP-tokenfil** – Kontrollera att du har registrerat dig för volyminköpsprogrammet för företag eller volymköpsprogrammet för utbildning. Därefter laddar du ned Apples VPP-token för ditt konto och markerar den.
    - **Apple-ID** – Ange Apple-ID för det konto som är associerat med inköpsprogrammet för volymen.
    - **Typ av VPP-konto** – Välj mellan **Företag** eller **Utbildning**.
4. Klicka på **Skapa** när du är klar.

Den token du önskar visas i fönstret med tokenlistan.


Du kan synkronisera data från Apple med Intune när som helst genom att välja **Synkronisera nu**.

## <a name="to-assign-a-volume-purchased-app"></a>Tilldela en volyminköpt app

3. I fönstret **Intune** väljer du **E-böcker**.
1. I arbetsbelastningen **E-böcker** väljer du **Hantera** > **Alla e-böcker**.
2. I listan med böcker väljer du den bok du vill tilldela och sedan ”**...**” > **Tilldela grupper**.
3. I fönstret <*boknamn*> – **Tilldelade grupper** väljer du **Hantera** > **Tilldelade grupper**.
4. Välj **Tilldela grupper** och i fönstret **Välj grupper** väljer du sedan de Azure AD-användargrupper som du vill tilldela boken till. Enhetsgrupper stöds inte för närvarande.
Du måste välja tilldelningsåtgärden **Tillgänglig** eller **Obligatorisk**. 
5. När du är klar väljer du **Spara**.

## <a name="next-steps"></a>Nästa steg

Se [Så här övervakar du appar ](apps-monitor.md) för information som hjälper dig övervaka boktilldelningar.






