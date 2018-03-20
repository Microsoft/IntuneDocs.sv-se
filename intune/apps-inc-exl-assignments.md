---
title: Inkludera och exkludera apptilldelningar i Microsoft Intune
titlesuffix: 
description: "Läs om hur du kan använda Microsoft Intune till att inkludera och exkludera apptilldelningar."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dbe8669dc2bf448e0738147758d90ba6d2d69b06
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Inkludera och exkludera apptilldelningar i Microsoft Intune

Med hjälp av Intune kan du se vem som har åtkomst till en app genom att tilldela grupper för att inkludera och exkludera. Innan du tilldelar grupper till appen måste du dock ange tilldelningstyp för den. Tilldelningstypen gör appen tillgänglig, obligatorisk eller avinstallerar appen. 

När du fokuserar på tillgängligheten för en app inkluderar och exkluderar du apptilldelningar till en grupp med användare eller enheter genom att använda en kombination av grupptilldelningar som inkluderar och exkluderar. Den här funktionen kan vara användbar när du gör appen tillgänglig genom att inkludera en stor grupp och sedan begränsar valda användare genom att även exkludera en mindre grupp. Den mindre gruppen kan vara en testgrupp eller en exekutiv grupp. 

När du exkluderar grupper från en apptilldelning kan du endast exkludera användargrupper eller enhetsgrupper – du kan inte blanda grupperna. Intune tar inte hänsyn till några kopplingar mellan användare och specifika enheter vid exkludering av grupper. Om du väljer att inkludera användargrupper och samtidigt exkludera enhetsgrupper så kommer du aldrig att få önskat resultat eftersom inkludering har företräde över exkludering. Om du till exempel riktar en iOS-app till **Alla användare** och exkluderar **Alla iPad-enheter** blir resultatet att alla användare som använder en iPad fortfarande får appen. Om däremot du riktar iOS-appen till **Alla enheter** och exkluderar **Alla iPad-enheter** så lyckas distributionen.  

>[!NOTE]
>När du ställer in en grupptilldelning för en app blir typen **Ej tillämpligt** inaktuell och ersätts med gruppfunktioner för att exkludera. 
>
>Intune tillhandahåller de i förväg skapade grupperna **Alla användare** och **Alla enheter** i konsolen med inbyggda optimeringar för att förenkla för dig. Vi rekommenderar starkt att du använder de här grupperna för att ange alla användare och alla enheter som mål i stället för grupperna för ”Alla användare” eller ”Alla enheter” som du själv har skapat.  

## <a name="including-and-excluding-groups-when-assigning-apps"></a>Inkludera och exkludera grupper när du tilldelar appar 
Tilldela en app till grupper med hjälp av en tilldelning för att inkludera eller exkludera:
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** på bladet Microsoft Intune.
4. Välj **Appar** på bladet **Mobilappar**. Listan över tillagda appar visas.
5. Markera appen som du vill tilldela. En instrumentpanel som hör till appen visas. 
6. Välj **Tilldelningar** under avsnittet **Hantera**. 

    ![Apptilldelningar i Intune](./media/apps-inc-exl-01.png)
7. Välj **Lägg till grupp** för att lägga till grupper av användare som har tilldelats appen. 
8. Välj en **Tilldelningstyp** bland de tillgängliga tilldelningstyperna i fönstret **Lägg till grupp**.
9. Välj **Tillgänglig med eller utan registrering** som tilldelningstyp.

    ![Apptilldelningar i Intune – Lägg till grupp](./media/apps-inc-exl-02.png)
10. Välj **Inkluderade grupper** för att välja grupper av användare som du vill göra appen tillgänglig för.

    >[!NOTE]
    >Om någon annan grupp redan har inkluderats för en viss tilldelning när du lägger till en grupp så blir den förvald och kan inte ändras för andra tilldelningstyper för inkludering. Gruppen som har använts kan därför inte användas som en inkluderad grupp.

11. Välj **Ja** för att göra appen tillgänglig för alla användare.

    ![Apptilldelningar i Intune – Inkludera grupper](./media/apps-inc-exl-03.png)
12. Klicka på **OK** för att ställa in så att gruppen inkluderar.
13. Välj **Exkluderade grupper** för att välja grupper av användare som du vill göra appen otillgänglig för. 
14. Välj grupperna som ska exkluderas, vilket gör att den här appen blir otillgänglig för dem.

    ![Apptilldelningar i Intune – Exkludera grupper](./media/apps-inc-exl-04.png)
15. Klicka på **Välj** för att slutföra valet av grupper.
16. Klicka på **OK** på bladet **Lägg till grupp**. Listan över **Apptilldelningar** visas.
17. Klicka på **Spara** för att aktivera grupptilldelningar för appen.

När du gör grupptilldelningar inaktiveras grupper som redan har tilldelats eller valts. Om du vill välja en grupp som för närvarande är inaktiverad tar du bort den från appens lista över tilldelningar. Du kan redigera tilldelningar från listan **apptilldelningar** genom att markera raden som innehåller den specifika tilldelningen som du vill ändra. Dessutom kan du ta bort en tilldelning genom att klicka på ellipsen (...) i slutet av en rad och välja **Ta bort**. Du kan även ändra vyn för listan **Tilldelningar** genom att välja att gruppera efter **Tilldelningstyp** eller **Inkluderade/Exkluderade**.

![Apptilldelningar i Intune – Slutförda](./media/apps-inc-exl-05.png)

## <a name="next-steps"></a>Nästa steg

- Mer information om att inkludera och exkludera grupptilldelningar för appar finns på [Microsoft Intune-bloggen](https://aka.ms/new_app_assignment_process).
- [Övervaka appinformation och tilldelningar](apps-monitor.md)