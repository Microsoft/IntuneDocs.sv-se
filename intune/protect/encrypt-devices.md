---
title: Kryptera enheter med den krypteringsmetod som stöds av plattformarna
titleSuffix: Microsoft Intune
description: Kryptera enheter med inbyggda krypteringsmetoder som BitLocker eller FileVault och hantera återställningsnycklarna för de krypterade enheterna på Intune-portalen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a5c844377dcd69b6caf5ef9f72fcb8dbb4ef8bd0
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609309"
---
# <a name="use-device-encryption-with-intune"></a>Använda enhetskryptering med Intune

Skydda data på dina enheter genom att använda Intune för att hantera inbyggd disk- eller enhetskryptering för enheter.

Konfigurera diskkryptering som en del av en enhetskonfigurationsprofil för Endpoint Protection. Följande plattformar och krypteringstekniker stöds av Intune:

- macOS: FileVault
- Windows 10 och senare: BitLocker

Intune tillhandahåller också en inbyggd [krypteringsrapport](encryption-monitor.md) som visar information om krypteringsstatusen för enheter, för alla dina hanterade enheter.

## <a name="filevault-encryption-for-macos"></a>FileVault-kryptering för macOS

Använd Intune för att konfigurera FileVault-diskkryptering på enheter som kör macOS. Använd sedan Intunes krypteringsrapport för att visa krypteringsinformation för de enheterna och för att hantera återställningsnycklar för FileVault-krypterade enheter.

Användargodkänd enhetsregistrering krävs för att FileVault ska fungera på enheten. Användaren måste godkänna hanteringsprofilen manuellt i systeminställningarna för att registreringen ska betraktas som användargodkänd.

FileVault är ett program för kryptering av hela diskar som ingår i macOS. Du kan använda Intune för att konfigurera FileVault på enheter som kör **MacOS 10.13 eller senare**.

Om du vill konfigurera FileVault skapar du en [enhetskonfigurationsprofil](../configuration/device-profile-create.md) för slutpunktsskydd för macOS-plattformen. FileVault-inställningar är en av de tillgängliga inställningskategorierna för macOS-slutpunktsskydd.

När du har skapat en princip för att kryptera enheter med FileVault tillämpas principen på enheter i två steg. Först förbereds enheten så att Intune kan hämta och säkerhetskopiera återställningsnyckeln. Den här åtgärden kallas deponering eller deposition. När nyckeln har deponerats kan diskkrypteringen starta.

![FileVault-inställningar](./media/encrypt-devices/filevault-settings.png)

Mer information om FileVault-inställningen som du kan hantera med Intune finns i [FileVault](endpoint-protection-macos.md#filevault) i Intune-artikeln om inställningar för slutpunktsskydd i macOS.

### <a name="permissions-to-manage-filevault"></a>Behörighet att hantera FileVault

För att kunna hantera FileVault i Intune måste ditt konto ha rätt behörigheter för [rollbaserad åtkomstkontroll](../fundamentals/role-based-access-control.md) (RBAC) i Intune.

Nedan visas de FileVault-behörigheter som ingår i kategorin **Fjärruppgifter** och de inbyggda RBAC-roller som ger behörigheten:
 
- **Hämta FileVault-nyckel**:
  - Supportavdelningen
  - Slutpunktssäkerhetshanteraren

- **Rotera FileVault-nyckel**
  - Supportavdelningen

### <a name="how-to-configure-macos-filevault"></a>Så här konfigurerar du FileVault för macOS

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

3. Ange följande alternativ:

   - Plattform: macOS
   - Profiltyp: Endpoint Protection

4. Välj **Inställningar** > **FileVault**.

5. För *FileVault* väljer du **Aktivera**.

6. För *Typ av återställningsnyckel* stöds endast **Privat nyckel**.

   Överväg att lägga till ett meddelande som hjälper slutanvändarna att hämta återställningsnyckeln för deras enheter. Den här informationen kan vara användbar för dina slutanvändare när du använder inställningen för rotation av personliga återställningsnycklar, som automatiskt kan generera en ny återställningsnyckel för en enhet med jämna mellanrum.

   Exempel: Om du vill hämta en förlorad eller nyligen roterad återställningsnyckel loggar du in på webbplatsen för Intune-företagsportalen från valfri enhet. På portalen går du till *Enheter* och väljer den enhet där FileVault är aktiverat och väljer sedan *Hämta återställningsnyckel*. Den aktuella återställningsnyckeln visas.

7. Konfigurera de återstående [FileVault](endpoint-protection-macos.md#filevault)inställningarna efter dina affärsbehov och välj **OK**.

  8. Slutför konfigurationen av ytterligare inställningar och spara sedan profilen.  

### <a name="manage-filevault"></a>Hantera FileVault

När Intune har krypterat en macOS-enhet med FileVault kan du visa och hantera FileVault-återställningsnycklarna när du visar [Intunes krypteringsrapport](encryption-monitor.md).

När Intune har krypterat en macOS-enhet med FileVault kan du visa enhetens personliga återställningsnyckel från företagsportalen på webben på vilken enhet som helst. När du är i Intune-företagsportalen väljer du den krypterade macOS-enheten och väljer sedan Hämta återställningsnyckel som en fjärrenhetsåtgärd.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>Hämta personlig återställningsnyckel från MEM-krypterade macOS-enheter

Slutanvändarna hämtar sin personliga återställningsnyckel (FileVault Key) med hjälp av iOS-företagsportalappen. Den enhet som har den personliga återställningsnyckeln måste registreras med Intune och krypteras med FileVault via Intune. Med hjälp av iOS-företagsportalappen kan slutanvändaren öppna en webbsida som innehåller den personliga återställningsnyckeln för FileVault. Du kan också hämta återställningsnyckeln från Intune genom att välja **Enheter** > *den krypterade och registrerade macOS-enheten* > **Hämta återställningsnyckel**. 

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker-kryptering för Windows 10

Använd Intune för att konfigurera BitLocker-diskkryptering på enheter som kör Windows 10. Använd sedan Intunes krypteringsrapport för att visa krypteringsinformation för de enheterna. Du kan också komma åt viktig information för BitLocker från dina enheter, som du hittar i Azure Active Directory (Azure AD).

BitLocker är tillgängligt på enheter som kör **Windows 10 eller senare**.

Konfigurera BitLocker när du skapar en [enhetskonfigurationsprofil](../configuration/device-profile-create.md) för slutpunktsskydd för Windows 10-plattformen eller senare. BitLocker-inställningarna finns i kategorin med inställningar för Windows-kryptering för Windows 10-slutpunktsskydd.

![BitLocker-inställningar](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Så här konfigurerar du BitLocker i Windows 10

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

3. Ange följande alternativ:

   - Plattform: Windows 10 och senare
   - Profiltyp: Endpoint Protection

4. Välj **Inställningar** > **Windows-kryptering**.

5. Konfigurera inställningarna för BitLocker efter dina affärsbehov och välj **OK**.

6. Slutför konfigurationen av ytterligare inställningar och spara sedan profilen.

### <a name="manage-bitlocker"></a>Hantera BitLocker

När Intune har krypterat en Windows 10-enhet med BitLocker kan du visa och hämta BitLocker-återställningsnycklar när du visar [Intunes krypteringsrapport](encryption-monitor.md).

### <a name="rotate-bitlocker-recovery-keys"></a>Rotera BitLocker-återställningsnycklar

Du kan använda en enhetsåtgärd i Intune för att fjärrrotera BitLocker-återställningsnyckeln på en enhet som kör Windows 10 version 1909 eller senare.

#### <a name="prerequisites"></a>Krav

Enheter måste uppfylla följande krav för att stödja rotation av BitLocker-återställningsnyckel:

- Enheterna måste köra Windows 10 version 1909 eller senare

- Azure Active Directory-anslutna och hybridanslutna enheter måste ha stöd för nyckelrotation aktiverat:

  - **Klientbaserad rotering av återställningslösenord**

  Den här inställningen finns under *Windows-kryptering* som en del av en enhetskonfigurationsprincip för Windows 10 slutpunktsskydd.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>Så här roterar du BitLocker-återställningsnycklar

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Alla enheter**.

3. I listan över enheter som du hanterar väljer du en enhet, väljer **Mer** och sedan fjärråtgärden **BitLocker-nyckelrotering**.

## <a name="next-steps"></a>Nästa steg

Skapa [en enhetsefterlevnadsprincip](compliance-policy-create-windows.md).

Använd krypteringsrapporten för att hantera:

- [BitLocker-återställningsnycklar](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault-återställningsnycklar](encryption-monitor.md#filevault-recovery-keys)

Granska de krypteringsinställningar som du kan konfigurera med Intune för:

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
