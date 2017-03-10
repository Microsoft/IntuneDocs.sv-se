---
title: Hantera enheter med Intune
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur du visar de enheter som du hanterar med Intune och utför olika åtgärder på dem."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d5d7b87f58604b93ba3b65d5d264a0a5e3743d45
ms.lasthandoff: 02/18/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune? 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Arbetsbelastningen **Enheter och grupper** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. På **Intune**-bladet väljer du **Enheter och grupper**.

    ![Arbetsbelastningen Enheter och grupper](./media/devices-and-groups-workload.png)

Välj nu något av följande:

- **Översikt** – Hämta information om enheter som du har registrerat och operativsystemen som körs för varje enhet.
- **Hantera** – Välj **Alla enheter** för att visa en lista över alla enheter som du hanterar.
    Välj en av enheterna i listan för att öppna bladet <*enhetsnamn*> **Översikt** där du kan välja:
    - **Översikt** – Visa allmän information om enheten inklusive information om dess namn, ägare, om det är en BYOD-enhet, när den senast var incheckad, med mera. Dessutom kan du utföra följande fjärråtgärder på enheten (alla åtgärderna stöds inte av alla enhetsplattformar):
        - **Ta bort företagsdata** – Tar endast bort företagsdata som hanteras av Intune. Personliga data tas inte bort från enheten. Enheten kommer inte längre att hanteras av Intune och kommer inte längre att kunna komma åt företagets resurser (stöds inte för Windows-enheter som är anslutna till Azure Active Directory).
        - **Fabriksåterställning** – Återställer enheten till standardinställningarna. Enheten kommer inte längre att hanteras av Intune och både företagsdata och personliga data tas bort. Du kan inte ångra den här åtgärden.
        - **Fjärrlåsning** – Låser enheten. Enhetens ägare måste använda sitt lösenord för att låsa upp den. Du kan endast fjärrlåsa en enhet som har en PIN-kod eller angett lösenord.
        - **Återställ lösenord** – Genererar ett nytt lösenord för enheten som visas på bladet <*enhetsnamn*> **Översikt**.
        - **Kringgå aktiveringslås** – Tar bort aktiveringslås från en iOS-enhet utan användarens Apple-ID och lösenord. När du har kringgått aktiveringslåset aktiverar enheten aktiveringslåset igen när appen Hitta Min iPhone startar. Kringgå bara aktiveringslåset om du har fysisk åtkomst till enheten.
        - **Borttappat läge** – Om en enhet har blivit stulen kan du aktivera borttappat läge. Det gör att du kan ange ett meddelande och ett telefonnummer som ska visas på enhetens låsskärm.
        - **Starta om** – Gör så att enheten startas om. Enhetens ägare meddelas inte automatiskt om omstarten, och kan därför förlora arbete.
        ![Enhetsöversikt](http://i.imgur.com/4Rx4VXm.png)
        
    - **Maskinvara** – Visa mer detaljerad information om enheten, inklusive dess lediga lagringsutrymme, modell, tillverkare och mycket annat.
    ![Maskinvaruinventering för hanterade enheter](./media/hardware-inventory.png)
    - **Identifierade program** – Visar en lista över alla appar som Intune hittar installerade på enheten.
    ![Identifierad programnod](./media/detected-applications.png)
- **Övervaka** Välj **Enhetsåtgärder ** för att se en lista över enhetsåtgärder som har utförts på enheter som du hanterar och det aktuella tillståndet för dessa åtgärder.
![Övervaka enhetsåtgärder](./media/monitor-device-actions.png)

