---
title: Felsöka appinstallationsproblem
titlesuffix: Microsoft Intune
description: Använd felsökningsfönstret i Microsoft Intune om du vill felsöka appinstallationsproblem.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138687"
---
# <a name="troubleshoot-app-installation-issues"></a>Felsöka appinstallationsproblem

På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Microsoft Intune tillhandahåller information om appinstallationsfel som tillåter supportansvariga och Intune-administratörer att visa information som underlättar användarnas begäran om hjälp. Felsökningsfönstret i Intune ger information om felet, inklusive information om hanterade appar på en användares enhet. Information om en apps livscykel från början till slut ges under varje enskild enhet i fönstret **Hanterade appar**. Du kan visa installationsrelaterad information, t.ex. när appen har skapats, ändrats, inriktats och levereras till en enhet. 

## <a name="to-review-app-troubleshooting-details"></a>Granska information om appfelsökning

Intune tillhandahåller appfelsökningsinformation baserad på de appar som installerats på en viss användares enhet.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Felsök** i fönstret **Intune**.
4. Klicka på **Välj användare** om du vill välja en användare att felsöka. Fönstret **Välj användare** visas.
5. Välj en användare genom att skriva namnet eller e-postadressen. Klicka på **Nästa** längst ner i fönstret. Felsökningsinformationen för användaren visas i fönstret **Felsökning**. 
6. Välj den enhet som du vill felsöka i listan **Enheter**.
    ![Felsökningsfönstret i Intune.](media/troubleshoot-app-install-01.png)
7. Välj **Hanterade appar** i det valda enhetsfönstret. En lista över hanterade appar visas.
    ![Information om en specifik enhet som hanteras av Intune.](media/troubleshoot-app-install-02.png)
8. Välj en app i listan där **Installationsstatus** indikerar ett fel.
    ![En vald app som visar information om installationsfel.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > Samma app kan tilldelas till flera grupper, men med olika avsedda åtgärder (avsikter) för appen. En löst avsikt för en app kan t.ex. visa **Exkluderad** om appen har exkluderats för en användare under apptilldelningen. Mer information finns i [Lösa konflikter mellan appavsikter](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Intune filtrerar för närvarande inte ut appar baserat på OS-plattform.

Problemet indikeras i informationen om appinstallationsfel. Du kan använda den här informationen för att komma fram till vilket som är det bästa sättet att lösa problemet på. Läs mer om hur du felsöker appinstallationsproblem i [Felkoder för felsökning av appinstallationsproblem](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues).

> [!Note]  
> Du kan också få åtkomst till **felsökningsfönstret** genom att gå till: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="next-steps"></a>Nästa steg

- Ytterligare information om felsökning av Intune information finns i [Använd felsökningsportalen för att hjälpa företagets användare](help-desk-operators.md). 
- Lär dig om kända problem i Microsoft Intune. Mer information finns i [Kända problem i Microsoft Intune](known-issues.md).
- Behöver du mer hjälp? Se [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).
