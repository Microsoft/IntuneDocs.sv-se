---
title: Inaktivera en Windows-dator
titlesuffix: Microsoft Intune
description: Hur du inaktiverar en Intune-hanterad Windows-dator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 607a80f88fa9f8631766c871478d6321b954fbb2
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233958"
---
# <a name="retire-a-windows-pc"></a>Inaktivera en Windows-dator

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Använd följande steg för att inaktivera datorer som hanteras som datorer genom att köra Intune-programvaruklienten på dem. När du inaktiverar en dator tas den bort från Intune-hanteringen. Det går inte att rensa en dator från Intune så att den återgår till de ursprungliga fabriksinställningarna.

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

    Om det inte går att avinstallera Endpoint Protection-klienten läser du [Felsöka Endpoint Protection](/intune/troubleshoot-endpoint-protection-in-microsoft-intune) om du behöver mer hjälp.

### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
