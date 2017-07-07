---
title: Dra tillbaka enheter
description: "Du kan använda en selektiv eller fullständig rensning för att ta bort enheten från Intune-hanteringen genom att ta bort enhetens princip och företagsportalen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3dbec400-5d8a-47be-b892-7745811d9de2
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 493b5bfce7ab9b78f5f7c48d0d18524d1b191f1f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="retire-devices-from-intune-management"></a>Dra tillbaka enheter från Intune-hanteringen

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Beroende på om enheter är företags- eller privatägda kanske en hanterad enhet måste tas bort från Intune-hanteringen.

Enheter tas aldrig bort från Intune utan att du gör något, även om enheterna inte har anslutit till Intune-tjänsten under en längre tid.

Du kan behöva dra tillbaka en enhet av flera olika skäl:

-   Användaren lämnar företaget på ett planerat sätt ("hanterad" avgång)
-   Användaren lämnar tvärt (får sparken, säger upp sig, etc.).
-   Enheten går förlorad
-   Enheten får ett nytt syfte (övertas av en annan användare, återanvänds för ett annat ändamål osv.)

Du kan göra en selektiv rensning eller en fullständig rensning av en enhet som hanteras som en mobil enhet, eller så kan du låsa en enhet och återställa dess lösenord. Genom att rensa en enhet frigör du användarens prenumeration så att en annan enhet kan läggas till. Du kan också dra tillbaka datorer som hanteras med Intune-klientprogrammet.

## <a name="wipe-data-and-apps-from-devices"></a>Rensa data och appar från enheter
Enheten tas bort från Intune-hanteringen både vid en selektiv och vid en fullständig rensning genom att dess princip och företagsportalen tas bort. Det betyder att enheten inte längre har nödvändiga autentiseringsuppgifter för att logga in till företagsresurser som Microsoft SharePoint, e-post eller Office 365.

[Selektiv rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) är det bästa alternativet för medarbetare som registrerat sin egen enhet i Intune eftersom det inte påverkar personlig information på enheten. Endast företagsdata tas bort.

För enheter som ska användas i ett nytt syfte kan du också göra en [fullständig rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) för att återställa enheten till fabriksinställningarna.

### <a name="removing-user-licenses-and-managed-devices"></a>Ta bort användarlicenser och hanterade enheter
När du tar bort en användarlicens avregistreras användarens registrerade enheter. Vi rekommenderar att du använder selektiv rensning för att ta bort företagsdata från hanterade enheter innan du tar bort Intune-licensen för en användare. När du tar bort användarlicensen kan du inte längre köra fjärråtgärder mot enheten.

## <a name="to-delete-devices-in-the-azure-active-directory-portal"></a>Ta bort enheter i Azure Active Directory-portalen

1.  Logga in på [http://aka.ms/accessaad](http://aka.ms/accessaad) eller [https://portal.office.com](https://portal.office.com) med inloggningsuppgifterna för organisationen och välj sedan **Administratörscentra** &gt; **Azure AD**.

2.  Skapa en Azure-prenumeration om du inte redan har en. Detta kräver normalt inget kreditkort eller betalning om du har ett betalt konto. Välj länken för att **registrera en kostnadsfri Azure Active Directory-prenumeration**.

4.  Välj **Active Directory** och välj sedan din organisation.

5.  Välj fliken **Användare**.

6.  Välj den användare vars enheter du vill ta bort.

7.  Välj **Enheter**.

8.  Välj lämpliga enheter och välj sedan **Ta bort enhet**. Enheten tas bort nästa gång den synkroniseras med Active Directory. Normalt sker detta inom fyra timmar. Efter synkroniseringen tas enheten bort från hanteringen. Därmed tas en enhet bort från användarens enhetsgräns.

## <a name="retire-managed-computers"></a>Dra tillbaka hanterade datorer
Datorer som Intune-klientprogrammet hanterar kan tas bort från hanteringen i Intune-administratörskonsolen. Detta gör också att klientprogramvaran avinstalleras och att Intune-principen tas bort från datorn. Läs mer om att [dra tillbaka datorer som hanteras av Intune-klientprogramvaran](retire-a-windows-pc-with-microsoft-intune.md).

## <a name="block-access-a-device"></a>Blockera åtkomst till en enhet
Om en enhet tappas bort eller om du måste dra tillbaka en enhet på grund av att en anställd har lämnat företaget utan att lämna tillbaka maskinvara som ägs av företaget kan du också [återställa lösenordet och fjärrlåsa](use-remote-lock-and-passcode-reset-in-microsoft-intune.md) enheten. På så sätt kan du förhindra att obehöriga använder företagets information, även om du kanske blir tvungen att skriva av enheten som en förlust.

Du bör också återkalla licensen för medarbetarens Intunekonto. Detta frigör licensen och du kan tilldela den till ett nytt användarkonto.

## <a name="retire-hardware"></a>Göra sig av med maskinvara
Ibland är det själva enheten som blivit för gammal. I sådana fall tar en [återställning till fabriksinställningarna](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) med en fullständig rensning bort alla data och tar bort enheten från Intune. Sedan kan du göra dig av med maskinvaran i enlighet med företagets policy.

### <a name="see-also"></a>Se även
[Skydda dina data med en fullständig eller selektiv rensning](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md)
