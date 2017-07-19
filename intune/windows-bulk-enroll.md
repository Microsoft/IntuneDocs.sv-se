---
title: "Massregistrering för Windows 10"
titleSuffix: Intune on Azure
description: "Skapa ett massregistreringspaket för Microsoft Intune"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: damionw
ms.custom: intune-azure
ms.openlocfilehash: 4e9dae27b981533dfff2080a5b7f9ca961509cd8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="bulk-enrollment-for-windows-devices"></a>Massregistrering för Windows-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som administratör kan du ansluta ett stort antal nya Windows-enheter till Azure Active Directory och Intune. Du massregistrerar enheter för Azure AD-klienten genom att skapa ett konfigurationspaket med hjälp av appen Windows Configuration Designer (WCD). När du tillämpar konfigurationspaketet på företagsägda enheter ansluts de till Azure AD-klienten och registreras för Intune-hantering. När paketet har tillämpats kan dina Azure AD-användare logga in.

Azure AD-användare är standardanvändare på enheterna och kan ta emot de tilldelade Intune-principer och appar som krävs. Självbetjäning och företagsportalscenarier stöds inte för närvarande.

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Krav för massregistrering av Windows-enheter

Massregistrering av Windows-enheter kräver följande:

- Enheter som kör Windows 10 Creator-uppdateringen eller senare
- [Automatisk registrering i Windows](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Skapa ett konfigurationspaket

1. Hämta [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) från Windows Store.
![Skärmbild av appen Windows Configuration Designer, Store-skärmbilder och beskrivning](media/bulk-enroll-store.png)

2. Öppna appen **Windows Configuration Designer** och välj **Konfigurera skrivbordsenheter**.
![Skärmbild över att välja Konfigurera skrivbordsenheter i Windows Configuration Designer-appen](media/bulk-enroll-select.png)

3. Fönstret **Nytt projekt** öppnas, där du anger följande:
  - **Namn** – Namnet på ditt projekt
  - **Projektmapp** – Där projektet ska sparas
  - **Beskrivning** – En valfri beskrivning av projektet ![Skärmbild över att ange namn, projektmapp och beskrivning i Windows Configuration Designer-appen](media/bulk-enroll-name.png)

4.  Ange ett unikt namn för dina enheter. Namnen kan innehålla ett serienummer (%%SERIAL%%) eller en slumpmässig uppsättning tecken. Du kan också ange en produktnyckel om du uppgraderar Windows, konfigurerar enheten för delad användning och tar bort det tidigare installerade programmet.
![Skärmbild över att ange namn, projektmapp och beskrivning i Windows Configuration Designer-appen](media/bulk-enroll-device.png)

5.  Du kan också konfigurera de Wi-Fi-nätverksenheter som ska anslutas när de startar första gången.  Om detta inte är konfigurerat krävs en anslutning till ett kabelanslutet nätverk när enheten startas första gången.
![Skärmbild över att aktivera Wi-Fi, inklusive nätverks-SSID och nätverkstyper i Windows Configuration Designer-appen](media/bulk-enroll-network.png)

6.  Välj **Registrera i Azure AD**, ange ett datum i **Förfallodatum för masstoken** och välj sedan **Hämta masstoken**.
![Skärmbild över att ange namn, projektmapp och beskrivning i Windows Configuration Designer-appen](media/bulk-enroll-account.png)

7. Ange dina Azure AD-autentiseringsuppgifter för att kunna hämta en masstoken.
![Skärmbild över att ange namn, projektmapp och beskrivning i Windows Configuration Designer-appen](media/bulk-enroll-cred.png)

8.  Klicka på **Nästa** när **Masstoken** har hämtats.

9. Du kan också **Lägga till program** och **Lägga till certifikat**. Dessa appar och certifikat är konfigurerade på enheten.

10. Du kan också lösenordsskydda ditt konfigurationspaket.  Klicka på **Skapa**.
![Skärmbild över att ange namn, projektmapp och beskrivning i Windows Configuration Designer-appen](media/bulk-enroll-create.png)

## <a name="provision-devices"></a>Konfigurera enheter

1. Få åtkomst till konfigurationspaketet på den plats som anges i **Projektmapp** i appen.

2. Välj hur du ska tillämpa konfigurationspaketet på enheten.  Ett konfigurationspaket kan tillämpas på en enhet på följande sätt:
 - Placera konfigurationspaketet på en USB-enhet, sätt i USB-enheten i den enhet som du vill massregistrera och tillämpa den under den första installationen
 - Placera konfigurationspaketet i en nätverksmapp och infoga den på den enhet som du vill massregistrera efter den första installationen

 Stegvisa anvisningar för att använda ett konfigurationspaket finns i [Tillämpa ett konfigurationspaket](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package).

3. När du har tillämpat paketet startas enheten automatiskt om efter 1 minut.
 ![Skärmbild över att ange namn, projektmapp och beskrivning i Windows Configuration Designer-appen](media/bulk-enroll-add.png)

4. När enheten startas om, ansluter den till Azure Active Directory och registreras i Microsoft Intune.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Felsökning av massregistrering i Windows

### <a name="provisioning-issues"></a>Konfigurationsproblem
Konfigurationen är avsedd att användas på nya Windows-enheter. Konfigurationsfel kan kräva en fabriksåterställning av enheten eller en enhetsåterställning från en startavbildning. I nedanstående exempel beskrivs några orsaker till konfigurationsfel:

- Ett konfigurationspaket som försöker ansluta till en Active Directory-domän eller Azure Active Directory-klient som inte skapar ett lokalt konto, kan innebära att enheten inte kan nås om domänanslutningen misslyckas på grund av bristande nätverksanslutning.
- Skript som körs av konfigurationspaketet körs i systemkontexten, och kan komma att ändra enhetens filsystem och konfigurationer. Ett skadligt eller felaktigt skript kan placera enheten i ett tillstånd som bara kan återställas av en återställning av avbildningen eller en fabriksåterställning av enheten.

### <a name="problems-with-bulk-enrollment-and-company-portal"></a>Problem med massregistrering och företagsportalen
Om en användare försöker registrera en tidigare massregistrerad enhet med hjälp av företagsportalen, visas en varning om att deras enheter behöver ytterligare åtgärder, antingen installation eller registrering. Enheten är registrerad, men registreringen kan inte identifieras av företagsportalappen eller webbplatsen.

### <a name="conditional-access"></a>Villkorlig åtkomst
Villkorlig åtkomst är inte tillgänglig för Windows-enheter som registreras med massregistrering.
