---
title: Komma igång med appar i Microsoft Intune
titlesuffix: ''
description: Hitta och lägg till appar på enheter så att personalen kan arbeta effektivt.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b69934edc70e10ee01394cf5b6a4fed75334660
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330066"
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Komma igång med att lägga till appar i Microsoft Intune

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. Intune stöder flera olika apptyper. De tillgängliga alternativen skiljer sig åt för varje apptyp.

I Intune kan du lägga till och tilldela följande apptyper i företagsenheter:
- **Appar från Store**: För enheter i vilka ytterligare mobilapphantering ska tillämpas på appar som är tillgängliga i App Store.
- **Appar som skrivits internt (verksamhetsspecifika)**: För att ladda upp en fil som sedan laddas ned till användarnas enheter.
- **Inbyggda appar**: För att tilldela granskade och hanterade appar som till exempel Office 365-appar till iOS- och Android-enheter.
- **Appar på webben**: Intune skapar en genväg till webbappen på enhetens startskärm.

> [!NOTE]
> Nya principer som tillämpas på en dynamisk enhetsgrupp kan ta upp till åtta timmar att spridas till alla enheter i gruppen.

## <a name="how-do-i-assign-a-public-store-app"></a>Hur gör jag för att tilldela en offentlig butiksapp?

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** och välj sedan **Appar**.
4. Välj **Lägg till** och sedan **iOS** som **Apptyp**.
5. Välj **Välj app** för att visa fönstret **Sök i App Store**.
6. Sök efter en app att tilldela till enheten i textrutan. Välj appen och klicka sedan på **Välj**.
7. Välj **Appinformation** i fönstret **Lägg till app**. Kontrollera sedan att all information om appen är ifylld. Du kan lägga till ytterligare information som hjälp vid organisation av den här appen, t.ex. **Ägare**, **Anteckningar**, **Utvecklare** och en **sekretesswebbadress** till företagets sekretesspolicy.
8. Kontrollera att du har markerat **Ja** för att **visa appen som en aktuell app i företagsportalen** och klicka sedan på **OK**.
9. Välj **Lägg till** i fönstret **Lägg till app** för att lägga till appen. Åtgärden tar dig till appens **översikt**. Välj **Tilldelningar** och klicka sedan på **Lägg till grupp** för att tilldela appen till din testgrupp. Gör appen **tillgänglig** för nedladdning. Appen ska nu visas som en **aktuell App** på testenheten.


- [Så här tilldelar du appar till grupper](apps-deploy.md)

## <a name="learn-more"></a>Läs mer

* [Vad är apphantering med Intune?](app-management.md)
* [Översikt över appens livscykel](app-lifecycle.md)
* [Vad är appskyddsprinciper?](app-protection-policy.md)
