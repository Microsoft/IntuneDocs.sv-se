---
title: Inaktivera en Windows-dator
description: Hur du inaktiverar en Intune-hanterad Windows-dator.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 09bba1ea199b51fdd1503cb1f0a3beeb97b6aa47
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="retire-a-windows-pc"></a>Inaktivera en Windows-dator

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd följande steg för att inaktivera datorer som hanteras som datorer genom att köra Intune-programvaruklienten på dem. När du inaktiverar en dator tas den bort från Intune-hanteringen. Det går inte att fabriksåterställa en dator från Intune så att den återgår till de ursprungliga fabriksinställningarna.

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator du vill inaktivera).

2.  Markera de enheter som du vill dra tillbaka och välj sedan **Dra tillbaka/Rensa**.

Om du vill återregistrera en dator i Intune installerar du om klientprogrammet på datorn enligt anvisningarna i avsnittet [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Om en dator inte kan ansluta till Intune visas ett meddelande i arbetsytan **Instrumentpanel**.

När du drar tillbaka en dator:

-   Tas den bort från hanteringen och inventeringen i Intune, och licensen som är kopplad till datorn görs tillgänglig så att den kan användas igen. Ta ur bruk/Rensa tar bort Intune-programvaruklienten, men tar inte bort appar eller data från datorn. Det görs ingen fullständig rensning på datorn.

-   Visas dess status inte längre i Intune-konsolen.

-   Tar Intune bort klientprogrammet från datorn. Om datorn inte är ansluten till Intune-tjänsten tas klientprogrammet bort nästa gång datorn ansluts.

-   Microsoft Endpoint Protection tas bort från datorn. Om datorn har ett annat slutpunktsprogram installerat och det inaktiveras kan programmet aktiveras igen efter att Microsoft Intune Endpoint Protection har tagits bort, så att datorn skyddas.

-   Eventuella principer tas bort från datorn och de värden som angavs av principen kommer att ändras.

-   Datorn kommer inte längre att ta emot programuppdateringar eller uppdaterade definitioner för skadlig programvara från Intune-tjänsten.

-   Beroende på datorernas konfiguration kan de eventuellt fortfarande kan ta emot uppdateringar via Windows Server Update Services, Windows Update eller Microsoft Update.

    > [!IMPORTANT]
    > Om klientprogrammet har installerats med en hjälp av ett grupprincipobjekt (GPO), måste du ta bort grupprincipobjektet innan du kan ta bort klientprogrammet, för att förhindra att programvaran installeras på nytt.

    Om det inte går att avinstallera Endpoint Protection-klienten läser du [Felsöka Endpoint Protection](/intune-classic/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) om du behöver mer hjälp.

### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
