---
title: Efterlevnadsprincip för Jamf-enheter
titlesuffix: Microsoft Intune
description: Använd Microsoft Intunes efterlevnadsprinciper med Azure Active Directorys villkorliga åtkomst för att skydda Jamf-hanterade enheter.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 990c17dcb7a25e5ea6676326f785d49ac6ca3320
ms.sourcegitcommit: 07528df71460589522a2e1b3e5f9ed63eb773eea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34482343"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Tvinga fram efterlevnad på Mac-datorer som hanteras med Jamf Pro

|Gäller för: Intune på Azure Portal |
|--|
|Letar du efter dokumentation om Intune på den klassiska portalen? [Gå hit](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

Du kan använda Azure Active Directory och Microsoft Intunes principer för villkorlig åtkomst för att tillse att dina slutanvändare efterlever organisationens krav. Du kan tillämpa de här principerna på Mac-datorer som är [hanterade med Jamf Pro](conditional-access-integrate-jamf.md). Detta kräver tillgång till både Intune- och Jamf Pro-konsolerna.

## <a name="set-up-device-compliance-policies-in-intune"></a>Ställ in efterlevnadsprinciper för enheter i Intune

1. Öppna Microsoft Azure och gå till **Intune** > **enhetsefterlevnad** > **principer**. Du kan skapa principer för macOS, inklusive att välja en serie åtgärder (t.ex. skicka varnings-e-post) till icke-kompatibla användare och grupper.
2. Sök efter önskade grupper och tillämpa principer för dem.

> [!Note]
> Intune kräver fullständig diskkryptering för att vara kompatibelt.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Distribuera företagsportalappen för macOS i Jamf Pro

Du bör distribuera företagsportalappen för macOS i Jamf Pro som en bakgrundsinstallation genom att följa anvisningarna nedan:

1. På en macOS-enhet laddar du ned den aktuella versionen av [företagsportalappen för macOS](https://go.microsoft.com/fwlink/?linkid=862280). Installera den inte. Du behöver en kopia av att appen som du kan ladda upp till Jamf Pro.
2. Öppna Jamf Pro och gå till **datorhantering** > **paket**.
3. Skapa ett nytt paket med företagsportalappen för macOS och klicka sedan på **spara**.
4. Öppna **datorer** > **principer** och välj **ny**.
5. Använd nyttolasten **Allmänt** för att konfigurera inställningar för principen. Inställningarna bör vara:
   - Utlösare: välj **Registreringen är klar** och **Återkommande incheckning**
   - Körningsfrekvens: välj **En gång per dator**
6. Välj nyttolasten **paket** och klicka på **konfigurera**.
7. Klicka på **lägg till** för att välja paketet med företagsportalappen.
8. Välj **installera** från popup-menyn **åtgärd**.
9. Konfigurera inställningarna för paketet.
10. Klicka på fliken **omfång** för att ange vilka datorer företagsportalappen ska installeras på. Klicka på **Spara**. Principen kommer att köra begränsade enheter nästa gång den markerade utlösaren inträffar på datorn och uppfyller villkoren i nyttolasten **allmänt**.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Skapa en princip i Jamf Pro för att få användarna att registrera sina enheter med Azure Active Directory

> [!NOTE]
> Du behöver [distribuera företagsportalen](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) för macOS innan du går igenom nästa steg.  

Slutanvändare behöver starta företagsportalappen via Jamf Self Service att registrera enheten med Azure AD som en enhet som hanteras av Jamf Pro. Detta kräver att slutanvändarna vidtar åtgärder. Vi rekommenderar att du [kontaktar användaren](end-user-educate.md) via e-post, Jamf Pro-meddelanden eller på andra sätt för att be dem att klicka på knappen i Jamf Self Service.

> [!WARNING]
> Företagsportalappen måste startas från Jamf Self Service för att påbörja enhetsregistrering. <br><br>Om du startar företagsportalappen manuellt (t.ex. från Program eller mappen Nedladdningar) registreras inte enheten. Om en slutanvändare startar företagsportalen manuellt visas varningen "AccountNotOnboarded".

1. I Jamf Pro, går du till **datorer** > **principer** och skapar en ny princip för enhetsregistrering.
2. Konfigurera nyttolasten **Microsoft Intune-integrering**, inklusive utlösare och körningsfrekvens.
3. Klicka på fliken **omfång** och begränsa principen till alla målriktade enheter.
4. Klicka på fliken **självbetjäning** för att göra principen tillgänglig i Jamf Self Service. Inkludera principen i kategorin **enhetsefterlevnad**. Klicka på **Spara**.

## <a name="removing-a-jamf-managed-device-from-intune"></a>Ta bort en Jamf-hanterad enhet från Intune

Du kan inte ta bort en Jamf-hanterad enhet från Intune. Du måste ta bort Jamf-hanterade enheter från Jamf Pro. Då tas de även bort från Intune. 

Lär dig hur du [tar bort en Jamf-hanterad enhet i Jamf Pro-dokumenten](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Du kan även skicka in ett supportärende med [Jamf-support](https://www.jamf.com/support/) för ytterligare hjälp. 

## <a name="next-steps"></a>Nästa steg

- [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Kom igång med villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
