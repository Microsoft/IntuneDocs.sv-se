---
title: Kryptera enheter i Microsoft Intune med hjälp av kompatibla krypteringsmetoder
titleSuffix: Microsoft Intune
description: Kryptera enheter med inbyggda krypteringsmetoder som BitLocker eller FileVault och hantera återställningsnycklarna för de krypterade enheterna på Intune-portalen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 3f37b9b0bc16572cc86cbf79be616c7f395aa784
ms.sourcegitcommit: 2bce5e43956b6a5244a518caa618f97f93b4f727
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68467443"
---
# <a name="use-device-encryption-with-intune"></a>Använda enhetskryptering med Intune  

Skydda data på dina enheter genom att använda Intune för att hantera inbyggd disk- eller enhetskryptering för enheter.  

Konfigurera diskkryptering som en del av en enhetskonfigurationsprofil för Endpoint Protection. Följande plattformar och krypteringstekniker stöds av Intune:  
- macOS: FileVault   
- Windows 10 och senare: BitLocker  

Intune tillhandahåller också en inbyggd [krypteringsrapport](encryption-monitor.md) som visar information om krypteringsstatusen för enheter, för alla dina hanterade enheter.  

## <a name="filevault-encryption-for-macos"></a>FileVault-kryptering för macOS  

Använd Intune för att konfigurera FileVault-diskkryptering på enheter som kör macOS. Använd sedan Intunes krypteringsrapport för att visa krypteringsinformation för de enheterna och för att hantera återställningsnycklar för FileVault-krypterade enheter.  

FileVault är ett program för kryptering av hela diskar som ingår i macOS. Du kan använda Intune för att konfigurera FileVault på enheter som kör **MacOS 10.13 eller senare**.  

Om du vill konfigurera FileVault skapar du en [enhetskonfigurationsprofil](device-profile-create.md) för slutpunktsskydd för macOS-plattformen. FileVault-inställningar är en av de tillgängliga inställningskategorierna för macOS-slutpunktsskydd.  

När du har skapat en princip för att kryptera enheter med FileVault tillämpas principen på enheter i två steg. Först förbereds enheten så att Intune kan hämta och säkerhetskopiera återställningsnyckeln. Detta kallas deponering eller deposition. När nyckeln har deponerats kan diskkrypteringen starta.

![FileVault-inställningar](./media/encrypt-devices/filevault-settings.png)

Mer information om FileVault-inställningen som du kan hantera med Intune finns i [FileVault](endpoint-protection-macos.md#filevault) i Intune-artikeln om inställningar för slutpunktsskydd i macOS.  

### <a name="how-to-configure-macos-filevault"></a>Så här konfigurerar du FileVault för macOS 

1. Logga in i [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och gå till **Enhetskonfiguration** > **Profiler** > **Skapa profil**.  

2. Ange följande alternativ:  

   - Plattform: macOS  
   - Profiltyp: Endpoint Protection  

3. Välj **Inställningar** > **FileVault**.  

4. För *FileVault* väljer du **Aktivera**.  

5. För *Typ av återställningsnyckel* stöds endast **Privat nyckel**.  

   Överväg att lägga till ett meddelande som hjälper slutanvändarna att hämta återställningsnyckeln för deras enheter. Den här informationen kan vara användbar för dina slutanvändare när du använder inställningen för rotation av personliga återställningsnycklar, som automatiskt kan generera en ny återställningsnyckel för en enhet med jämna mellanrum.  

   Exempel: Om du vill hämta en förlorad eller nyligen roterad återställningsnyckel loggar du in på webbplatsen för Intune-företagsportalen från valfri enhet. På portalen går du till *Enheter* och väljer den enhet där FileVault är aktiverat och väljer sedan *Hämta återställningsnyckel*. Den aktuella återställningsnyckeln visas.  

6. Konfigurera de återstående [FileVault](endpoint-protection-macos.md#filevault)inställningarna efter dina affärsbehov och välj **OK**.  

7. Slutför konfigurationen av ytterligare inställningar och spara sedan profilen.  

### <a name="manage-filevault"></a>Hantera FileVault  

När Intune har krypterat en macOS-enhet med FileVault kan du visa och hantera FileVault-återställningsnycklarna när du visar [Intunes krypteringsrapport](encryption-monitor.md).  

## <a name="bitlocker-encryption-for-windows-10"></a>BitLocker-kryptering för Windows 10  

Använd Intune för att konfigurera BitLocker-diskkryptering på enheter som kör Windows 10. Använd sedan Intunes krypteringsrapport för att visa krypteringsinformation för de enheterna. Du kan också komma åt viktig information för BitLocker från dina enheter, som du hittar i Azure Active Directory (Azure AD).  

BitLocker är tillgängligt på enheter som kör **Windows 10 eller senare**.  

Konfigurera BitLocker när du skapar en [enhetskonfigurationsprofil](device-profile-create.md) för slutpunktsskydd för Windows 10-plattformen eller senare. BitLocker-inställningarna finns i kategorin med inställningar för Windows-kryptering för Windows 10-slutpunktsskydd.    

![BitLocker-inställningar](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>Så här konfigurerar du BitLocker i Windows 10  

1. Logga in i [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och gå till Enhetskonfiguration > Profiler > Skapa profil.  

2. Ange följande alternativ:  
   - Plattform: Windows 10 och senare  
   - Profiltyp: Endpoint Protection  

3. Välj **Inställningar** > **Windows-kryptering**.

4. Konfigurera inställningarna för BitLocker efter dina affärsbehov och välj **OK**.  

5. Slutför konfigurationen av ytterligare inställningar och spara sedan profilen.  

### <a name="manage-bitlocker"></a>Hantera BitLocker  

När Intune har krypterat en Windows 10-enhet med BitLocker kan du visa och hämta BitLocker-återställningsnycklar när du visar [Intunes krypteringsrapport](encryption-monitor.md).  

## <a name="next-steps"></a>Nästa steg  

Skapa en [efterlevnadsprincip för enheter](compliance-policy-create-windows.md)  

Använd krypteringsrapporten för att hantera:  
- [BitLocker-återställningsnycklar](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault-återställningsnycklar](encryption-monitor.md#filevault-recovery-keys)

Granska de krypteringsinställningar som du kan konfigurera med Intune för:  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
