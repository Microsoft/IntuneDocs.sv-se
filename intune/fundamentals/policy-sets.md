---
title: Principuppsättningar
titleSuffix: Microsoft Intune
description: Använd principuppsättningar för att gruppera samlingar av hanteringsobjekt i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e539f44fc9c9b4e7382368c0f3ad9f79bb1c98b1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585663"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>Använda principuppsättningar för att gruppera samlingar av hanteringsobjekt

Med principuppsättningar kan du skapa ett paket med referenser till redan befintliga hanteringsenheter som behöver identifieras, riktas och övervakas som en enda begreppsmässig enhet. En principuppsättning är en tilldelningsbar samling av appar, principer och andra hanteringsobjekt som du har skapat. Genom att skapa en principuppsättning kan du välja många olika objekt samtidigt och tilldela dem från en och samma plats. När din organisation ändras kan du gå tillbaka till en principuppsättning och lägga till eller ta bort objekt och tilldelningar. Du kan använda en principuppsättning för att associera och tilldela befintliga objekt såsom appar, principer och VPN i ett enda paket. 

> [!IMPORTANT]
> En lista över kända problem som rör principuppsättningar finns i [Kända problem med principuppsättningar](~/fundamentals/policy-sets.md#policy-sets-known-issues).

Principuppsättningar ersätter inte befintliga begrepp eller objekt. Du kan fortsätta att tilldela enskilda objekt, och du kan även referera till enskilda objekt som en del av en principuppsättning. Det innebär att alla ändringar av de enskilda objekten avspeglas i principuppsättningen. 

Du kan använda principuppsättningar för att:

- Gruppera objekt som behöver tilldelas tillsammans
- Tilldela din organisations minimikrav för konfiguration på alla hanterade enheter
- Tilldela appar som används ofta eller är relevanta till alla användare

Du kan inkludera följande hanteringsobjekt i en principuppsättning:
- Appar
- Konfigurationsprinciper för appar
- Appskyddsprinciper
- Enhetens konfigurationsprofiler
- Efterlevnadsprinciper för enheter
- Begränsningar för enhetstyp
- Windows Autopilot-distributionsprofiler
- Registreringsstatussida

När du skapar en principuppsättning skapar du en enskild tilldelningsenhet och hanterar associationer mellan olika objekt. En principuppsättning är en referens till objekt som är externa för den. Ändringar i de inkluderade objekten påverkar även principuppsättningen. När du har skapat en principuppsättning kan du visa och redigera objekt och tilldelningar flera gånger. 

> [!NOTE]
> Principuppsättningar stöder inställningar för Windows, Android, macOS och iOS, och de kan tilldelas plattformsoberoende.

## <a name="how-to-create-a-policy-set"></a>Så här skapar du en principuppsättning

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. På bladet **Intune** väljer du **Principuppsättningar** > **Principuppsättningar** > **Skapa**.
3. På sidan **Grundläggande** lägger du till följande värden:
    - **Namn på principuppsättning** – ange ett namn för den här principuppsättningen.
    - **Beskrivning** – om du vill kan du ange en beskrivning av principuppsättningen.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. Klicka på **Nästa: Programhantering**.<br>
   På sidan **Programhantering** kan du välja att [lägga till appar](~/apps/apps-add.md), [appkonfigurationsprinciper](~/apps/app-configuration-policies-overview.md) och [appskyddsprinciper](~/apps/app-protection-policy.md) till principuppsättningen. Information om apphantering finns i [Vad är apphantering i Microsoft Intune?](~/apps/app-management.md). 
5. Klicka på **Nästa: Enhetshantering**.<br>
   På sidan **Enhetshantering** kan du lägga till enhetshanteringsobjekt i principuppsättningen, till exempel [enhetskonfigurationsprofiler](~/configuration/device-profiles.md) och [principer för enhetsefterlevnad](~/protect/device-compliance-get-started.md). Se till att inkludera alla associerade objekt, till exempel andra principer, certifikat och profiler för säkerhetsbaslinje.
6. Klicka på **Nästa: Enhetsregistrering**.<br>
   På sidan **Enhetsregistrering** kan du lägga till enhetsregistreringsobjekt i principuppsättningen, till exempel [begränsningar för enhetstyp](~/enrollment/enrollment-restrictions-set.md), [Windows Autopilot-distributionsprofiler](~/enrollment/enrollment-autopilot.md) och [profiler för registreringsstatussida](~/enrollment/windows-enrollment-status.md).
7. Klicka på **Nästa: Tilldelningar**.<br>
   På sidan **Tilldelningar** kan du tilldela principuppsättningen till användare och enheter. Lägg märke till att du kan tilldela en principuppsättning till en enhet oavsett om enheten hanteras av Intune eller inte.
8. Klicka på **Nästa: Granska och skapa** för att granska de värden som du har angett för profilen.
9. När du är klar klickar du på **Skapa** för att skapa principuppsättningen i Intune. 

## <a name="policy-sets-known-issues"></a>Kända problem med principuppsättningar

Principuppsättningar är en ny funktion i version 1910 och har följande kända problem.

- När en principuppsättning skapas gäller att om en omfångsbegränsad administratör försöker skapa en principuppsättning utan att välja några omfångstaggar, så misslyckas valideringen när sidan **Granska och skapa** visas, och ett fel visas i statusfältet. Administratören måste växla till en annan sida i processen och sedan gå tillbaka till sidan **Granska och skapa**. Då aktiveras alternativet **Skapa**.  
 
- Följande typer av appar stöds för närvarande av principuppsättningar:
    - iOS Store-app
    - Verksamhetsspecifik iOS-app
    - Hanterad verksamhetsspecifik iOS-app
    - Android Store-app
    - Verksamhetsspecifik Android-app
    - Hanterad verksamhetsspecifik Android-app
    - Office 365 ProPlus Suite (Windows 10)
    - Webblänk
    - Inbyggd iOS-app
    - Inbyggd Android-app

- Det finns inte stöd för att ange en tilldelning av principuppsättning för **Alla användare** till **Autopilot-profil**.

- Principuppsättningar har följande problem med registreringsbegränsningar och sidan för registreringsstatus (ESP, Enrollment Status Page):
    - Begränsningar och ESP stöder inte tilldelningar av virtuella grupper.
    - Begränsningar och ESP har inte fullständigt stöd för tilldelning av uteslutningsgrupper. 
    - Begränsningar och ESP använder prioritetsbaserad konfliktlösning. Begränsningar och ESP tillämpas kanske inte på samma användare som resten av en principuppsättnings nyttolaster om begränsningarna och ESP också är mål för begränsningar och ESP med högre prioritet.
    - Standardmässiga begränsningar och ESP kan inte läggas till i en principuppsättning.

- MAM-principtyper som stöder principuppsättningar omfattar följande: 
    - MAM WIP (Windows) MDM-riktat skydd för hanterad app 
    - MAM iOS-riktat skydd för hanterad app
    - MAM Android-riktat skydd för hanterad app
    - MAM iOS-riktad konfiguration av hanterad app
    - MAM Android-riktad konfiguration av hanterad app

- MAM-principtyper som inte stöder principuppsättningar omfattar följande: 
    - MAM WIP (Windows)-riktat skydd för hanterad app

- MAM bearbetar tilldelningar av principuppsättning som direkta tilldelningar för följande principtyper:
    - MAM iOS-riktat skydd för hanterad app
    - MAM Android-riktat skydd för hanterad app
    - MAM iOS-riktad konfiguration av hanterad app
    - MAM Android-riktad konfiguration av hanterad app

    Om en princip läggs till i en principuppsättning som distribueras till en grupp visas gruppen som direkt tilldelad i arbetsbelastningen, inte ”tilldelad via principuppsättningen”. Resultatet av detta är att MAM inte bearbetar borttagningar av grupptilldelningar som kommer från principuppsättningar.

- MAM stöder inte distribution till virtuella grupper för **Alla användare** och **Alla enheter** för några principtyper alls.

## <a name="next-steps"></a>Nästa steg

- [Registrera enheter i Microsoft Intune](~/enrollment/index.yml).