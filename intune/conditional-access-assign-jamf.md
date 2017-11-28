---
title: "Tillämpa efterlevnadsprinciper för Jamf-hanterade enheter"
titlesuffix: Azure portal
description: "Använd efterlevnad för att säkra Jamf-hanterade enheter."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dd84812a7e7dcf83f01c8d4d2b613706f7700775
ms.sourcegitcommit: b2a6678a0e9617f94ee8c65e7981211483b30ee7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Tvinga fram efterlevnad på Mac-datorer som hanteras med Jamf Pro

|Gäller för: Intune på Azure Portal |
|--|
|Letar du efter dokumentation om Intune på den klassiska portalen? [Gå hit](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|För tillfället i privat förhandsvisning|
|--|
|De funktioner som beskrivs i det här avsnittet är bara tillgängliga för kunder som är med på den privata förhandsvisningen. Det här meddelandet tas bort när det har släppts för alla kunder.|
| |

Du kan använda Azure Active Directory och Microsoft Intunes principer för villkorlig åtkomst för att tillse att dina slutanvändare efterlever organisationens krav. Du kan tillämpa de här principerna på Mac-datorer som är [hanterade med Jamf Pro](conditional-access-integrate-jamf.md). Detta kräver tillgång till både Intune- och Jamf Pro-konsolerna.

## <a name="set-up-device-compliance-policies-in-intune"></a>Ställ in efterlevnadsprinciper för enheter i Intune

1. Öppna Microsoft Azure och gå till **Intune** > **enhetsefterlevnad** > **principer**. Du kan skapa principer för macOS, inklusive att välja en serie åtgärder (t.ex. skicka varnings-e-post) till icke-kompatibla användare och grupper.
2. Sök efter önskade grupper och tillämpa principer för dem.

## <a name="require-the-company-portal-app-for-macos"></a>Kräv företagsportalappen för macOS

1. På en macOS-enhet går du till https://aka.ms/macoscompanyportal för att hämta den aktuella versionen av företagsportalappen för macOS.
2. Öppna Jamf Pro och gå till **datorhantering** > **paket**.
3. Skapa ett nytt paket med företagsportalappen för macOS och klicka sedan på **spara**.
4. Öppna **datorer** > **principer** och välj **ny**.
5. Använd nyttolasten **allmänt** för att konfigurera inställningar för principen, inklusive utlösare och körningsfrekvens.
6. Välj nyttolasten **paket** och klicka på **konfigurera**.
7. Klicka på **lägg till** för att välja paketet med företagsportalappen.
8. Välj **installera** från popup-menyn **åtgärd**.
9. Konfigurera inställningarna för paketet.
10. Klicka på fliken **omfång** för att ange vilka datorer företagsportalappen ska installeras på. Klicka på **Spara**. Principen kommer att köra begränsade enheter nästa gång den markerade utlösaren inträffar på datorn och uppfyller villkoren i nyttolasten **allmänt**.

## <a name="direct-your-users-to-register-jamf-pro-managed-devices-with-azure-active-directory"></a>Instruera användarna att registrera Jamf Pro-hanterade enheter med Azure Active Directory

> [!NOTE]
> Du behöver [distribuera företagsportalen](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) för macOS innan du går igenom nästa steg.  

Slutanvändare behöver starta företagsportalappen via Jamf Self Service att registrera enheten med Azure AD som en enhet som hanteras av Jamf Pro.

1. I Jamf Pro, går du till **datorer** > **principer** och skapar en ny princip för enhetsregistrering.
2. Konfigurera nyttolasten **villkorlig åtkomst**, inklusive utlösare och körningsfrekvens. Ställ in prioriteten till **efter**.
3. Klicka på fliken **omfång** och begränsa principen till alla målriktade enheter.
4. Klicka på fliken **självbetjäning** för att göra principen tillgänglig i Jamf Self Service. Inkludera principen i kategorin **enhetsefterlevnad**. Klicka på **Spara**.

## <a name="next-steps"></a>Nästa steg

- [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Kom igång med villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
