---
title: "Anpassa konsolvyer för administratörsroller | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 52a77e50b3dde24ba270766d4472bdd6176cc415


---

# Anpassa Intune-konsolvyer i enlighet med administratörsroller
Du kan filtrera konsolvyn för administratörer i Microsoft Intune så att administratörerna endast ser de poster de behöver för sin roll. Du kan till exempel tillåta att operatörer för administratörskonsolen kan uppdatera definitioner för skadlig kod eller återställa lösenordet på enheter. Det gör du med hjälp av förinställda **beteckningar** som du tilldelar specifika användare. När dessa användare kommer åt administrationskonsolen, ser de bara poster specifika för deras beteckning.

## Skapa en anpassad vy

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Admin** &gt; **Tjänstadministratörer**.

2.  I listan över tjänstadministratörer väljer du den användare vars benämning du vill ändra och klickar sedan på **Hantera åtkomst**.

3.  I dialogrutan **Hantera åtkomst** , välj den åtkomstnivå som du vill ge den valda användaren. Du kan välja mellan:

    -   **Fullständig åtkomst:**
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

        -   Fjärrlås på en enhet

        -   Återställning av lösenord

När administratören som du har konfigurerat öppnar Intune-administratörskonsolen nästa gång får personen den åtkomstnivå som du tilldelat.



<!--HONumber=Jun16_HO4-->


