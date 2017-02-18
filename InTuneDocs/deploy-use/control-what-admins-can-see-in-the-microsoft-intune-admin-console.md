---
title: "Anpassa konsolvyer för administratörsroller | Microsoft Docs"
description: "I det här avsnittet beskrivs hur du kan filtrera visningen i Intune-administratörskonsolen så att administratörer endast ser de objekt som de behöver."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: ee35fb2c8e39af099fb061211ea1fdf767230217


---

# <a name="customize-intune-console-views-according-to-admin-roles"></a>Anpassa Intune-konsolvyer i enlighet med administratörsroller

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan filtrera visningen i Microsoft Intune-administratörskonsolen så att administratörerna endast ser de poster de behöver för sin roll. Du kan till exempel tillåta att operatörer för administratörskonsolen kan uppdatera definitioner för skadlig kod eller återställa lösenordet på enheter. Det gör du med hjälp av förinställda **beteckningar** som du tilldelar specifika användare. När dessa användare kommer åt administratörskonsolen, ser de bara poster specifika för deras beteckning.

## <a name="to-create-a-custom-view"></a>Skapa en anpassad vy

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Admin** &gt; **Tjänstadministratörer**.

2.  I listan över tjänstadministratörer väljer du den användare vars benämning du vill ändra och klickar sedan på **Hantera åtkomst**.

3.  I dialogrutan **Hantera åtkomst** , välj den åtkomstnivå som du vill ge den valda användaren. Du kan välja mellan:

    -   **Fullständig åtkomst**
    -   **Skrivskyddad åtkomst**
    -   **Supportavdelning – Gruppnod**

    Fullständig åtkomst och skrivskyddad åtkomst är självförklarande. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **Supportavdelning – Gruppnod** begränsar vad administratören kan se och göra till följande:

    -   Se listan över användare och enheter. Administratören kan inte använda filter för att ändra vyn. Du kan dock använda gruppfiltrering för att ändra vad administratören kan se. Mer information finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

    -   Skriv ut listan över användare och enheter

    -   Exportera listan över användare och enheter

    -   Visa egenskaperna för en användare eller enhet

    -   Utföra följande fjärruppgifter:

        -   Kör en full skanning för skadlig kod

        -   Köra en snabbskanning av skadlig kod

        -   Starta om en dator

        -   Uppdatera definitioner för skadlig kod

        -   Uppdatera principer

        -   Uppdatera inventering

        -   Fjärrlåsa en enhet

        -   Återställa ett lösenord

När administratören som du har konfigurerat öppnar Intune-administratörskonsolen nästa gång får personen den åtkomstnivå som du tilldelat.



<!--HONumber=Dec16_HO5-->


