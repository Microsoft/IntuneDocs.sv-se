---
title: "Intune Endpoint Protection-inställningar för Windows 10"
titleSuffix: Intune on Azure
description: "Läs om Intune-inställningarna du kan använda för att konfigurera Endpoint Protection-inställningar, för exempelvis BitLocker, på Windows 10-enheter.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f38320ca84a734f645c3d8554c5aef53836fd1be
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2017
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Endpoint Protection-inställningar för Windows 10 och senare i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med en Endpoint Protection-profil kan du konfigurera säkerhetsfunktioner, t.ex. BitLocker och Windows Defender för Windows 10-enheter.

Använd informationen i det här avsnittet för att lära dig skapa Endpoint Protection-profiler.

## <a name="create-an-endpoint-protection-profile"></a>Skapa en Endpoint Protection-profil

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för enhetens funktionsprofil.
5. I listrutan **Plattform** väljer du **Windows 10 och senare**.
6. Välj **Endpoint Protection** i listrutan **Profiltyp**.
7. Konfigurera önskade inställningar på bladet **Windows-kryptering**. Informationen i det här avsnittet hjälper dig förstå vad varje inställning gör. Välj **OK** när du är klar.
8. Gå tillbaka till bladet **Skapa profil** och välj **Skapa**.

Profilen skapas och visas på bladet med profillistan.

## <a name="windows-defender-smartscreen-settings"></a>Inställningar för Windows Defender SmartScreen

- **SmartScreen för appar och filer** – Aktivera Windows SmartScreen för körning av filer och program som körs.
- **Körning av overifierade filer** – Blockera användaren från att köra filer som inte har verifierats av Windows SmartScreen.

## <a name="windows-encryption-settings"></a>Krypteringsinställningar för Windows

### <a name="windows-settings"></a>Windows-inställningar

- **Kräv att enheter ska krypteras (endast skrivbord)** – Om den här inställningen är aktiverad, uppmanas användarna att aktivera kryptering för enheten. Dessutom uppmanas de att bekräfta att kryptering från en annan provider inte har aktiverats. Om Windows-kryptering aktiveras samtidigt som en annan krypteringsmetod är aktiv, kan enheten bli instabil.
- **Kräv att minneskort ska krypteras (endast mobil)** – Aktivera den här inställningen för att kryptera flyttbara minneskort som används av enheten.


### <a name="bitlocker-base-settings"></a>Grundläggande BitLocker-inställningar

- **Konfigurera krypteringsmetoder** – Aktivera den här inställningen för att konfigurera krypteringsalgoritmer för operativsystem, data och flyttbara enheter.
    - **Kryptering för operativsystemenheter** – Välj krypteringsmetod för operativsystemenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
    - **Kryptering för fasta dataenheter** – Välj krypteringsmetod för fasta (inbyggda) dataenheter. Vi rekommenderar att du använder XTS AES-algoritmen.
    - **Kryptering för flyttbara dataenheter** – Välj krypteringsmetod för flyttbara dataenheter. Om den flyttbara enheten används med enheter som inte kör Windows 10, rekommenderar vi att du använder AES-CBC-algoritmen.


### <a name="bitlocker-os-drive-settings"></a>BitLocker-inställningar för operativsystemenheten

- **Ytterligare autentisering krävs vid start** -
    - **BitLocker med icke kompatibelt TPM-chip** -
    - **TPM-start** – Konfigurera huruvida TPM-kretsen tillåts, inte tillåts eller krävs.
    - **Start-PIN för betrodd plattformsmodul** – Konfigurera om en start-PIN-kod tillåts, inte tillåts eller måste användas med TPM-kretsen.
    - **Startnyckel för betrodd plattformsmodul** – Konfigurera om en startnyckel tillåts, inte tillåts eller måste användas med TPM-kretsen.
    - **Startnyckel och PIN-kod för betrodd plattformsmodul** – Konfigurera om en startnyckel och start-PIN-kod tillåts, inte tillåts eller måste användas med TPM-kretsen.
- **Minsta PIN-kodslängd** – Aktivera den här inställningen för att konfigurera en minsta längd för start-PIN-koden för TPM.
    - **Minsta tecken** – Ange antalet tecken som krävs för start-PIN-koden för TPM, **4**-**20** tecken.
- **Aktivera återställning av operativsystemenhet** – Aktivera den här inställningen för att ange hur BitLocker-skyddade operativsystemenheter återställs när nödvändig startinformation saknas.
    - **Certifikatbaserad dataåterställningsagent** – Aktivera den här inställningen om du vill att dataåterställningsagenter ska kunna användas med BitLocker-skyddade operativsystemenheter.
    - **Återställningslösenord skapat av användare** – Konfigurera huruvida användare får, måste eller inte får generera ett 48-siffrigt återställningslösenord.
    - **Återställningsnyckel skapad av användare** – Konfigurera huruvida användare får, måste eller inte får skapa en 256-bitars återställningsnyckel.
    - **Dölj återställningsalternativ i BitLocker-installationsguiden** – Aktivera den här inställningen om du vill hindra användare från att se och ändra återställningsalternativ när de aktiverar BitLocker.
    - **Spara BitLocker-återställningsinformation i AD DS** – Aktivera lagring av BitLocker-återställningsinformation i Active Directory.
    - **Ställ in lagring av BitLocker-återställningsinformation till AD DS** – Konfigurera vilka delar av BitLocker-återställningsinformation lagras i Active Directory. Välj mellan:
        - **Säkerhetskopiera återställningslösenord och nyckelpaket**
        - **Säkerhetskopiera endast återställningslösenord**
    - **Kräv att återställningsinformation ska lagras i AD DS innan BitLocker aktiveras** – Aktivera den här inställningen för att hindra användare från att aktivera BitLocker om enheten är ansluten till domänen och BitLocker-återställningsinformation har lagrats i Active Directory.
- **Aktivera återställningsmeddelande och webbadress i förstartsmiljö** – Aktivera den här inställningen för att konfigurera meddelandet och URL:en som visas på förstartsskärmen för nyckelåterställning.
    - **Återställningsmeddelande i förstartsmiljö** – Konfigurera hur återställningsmeddelande i förstartsmiljö visas för användarna. Välj mellan:
        - **Använd standardvärde för återställningsmeddelande och webbadress**
        - **Använd tomt återställningsmeddelande och webbadress**
        - **Använd anpassat återställningsmeddelande**
        - **Använd anpassad återställningswebbadress**


### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker-inställningar för fasta dataenheter

- **Neka skrivåtkomst till fast dataenhet som inte skyddas av BitLocker** – Om den här inställningen aktiveras måste BitLocker-skyddet aktiveras på alla fasta eller inbyggda dataenheter för att det ska gå att skriva till dem.
- **Aktivera återställning av fast enhet** – Aktivera den här inställningen för att ange hur BitLocker-skyddade fasta enheter återställs när nödvändig startinformation saknas.
    - **Dataåterställningsagent** – Aktivera den här inställningen om du vill att dataåterställningsagenter som ska användas med BitLocker-skyddade fasta enheter.
    - **Återställningslösenord skapat av användare** – Konfigurera huruvida användare får, måste eller inte får generera ett 48-siffrigt återställningslösenord.  
    - **Återställningsnyckel skapad av användare** – Konfigurera huruvida användare får, måste eller inte får skapa en 256-bitars återställningsnyckel.
    - **Dölj återställningsalternativ i BitLocker-installationsguiden** – Aktivera den här inställningen om du vill hindra användare från att se och ändra återställningsalternativ när de aktiverar BitLocker.
    - **Spara BitLocker-återställningsinformation i AD DS** – Aktivera lagring av BitLocker-återställningsinformation i Active Directory.
    - **Ställ in lagring av BitLocker-återställningsinformation till AD DS** – Konfigurera vilka delar av BitLocker-återställningsinformation lagras i Active Directory. Välj mellan:
        - **Säkerhetskopiera återställningslösenord och nyckelpaket**
        - **Säkerhetskopiera endast återställningslösenord**
    - **Kräv att återställningsinformation ska lagras i AD DS innan BitLocker aktiveras** – Aktivera den här inställningen för att hindra användare från att aktivera BitLocker om enheten är ansluten till domänen och BitLocker-återställningsinformation har lagrats i Active Directory.


### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker-inställningar för flyttbara dataenheter

- **Neka skrivåtkomst till flyttbar dataenhet som inte skyddas av BitLocker** – Ange om BitLocker-kryptering krävs för flyttbara lagringsenheter.
    - **Blockera skrivåtkomst till enheter som har ställts in i en annan organisation** – Ange om det går att skriva till flyttbara enheter som tillhör en annan organisation.



## <a name="next-steps"></a>Nästa steg

Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).
