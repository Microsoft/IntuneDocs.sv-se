---
title: Krypteringsrapport och BitLocker-nycklar i Microsoft Intune
titleSuffix: Microsoft Intune
description: Visa en rapport om din enhetskrypteringsstatus och kom åt BitLocker-återställningsnycklar från Microsoft Intune-portalen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 52b92483ddafadf460911caaa472825a0bc0a20f
ms.sourcegitcommit: b4483c8476a209de83102e8993d8074dbb323493
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527224"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>Övervaka BitLocker och enhetskryptering  
Intune ger en central plats för att identifiera krypteringsstatus för dina Windows 10-enheter och hjälper dig att komma åt viktig information för BitLocker från dina enheter som finns i Azure Active Directory (AD Azure).  

- [Krypteringsrapporten (i allmänt tillgänglig förhandsversion)](#encryption-report) innehåller information om en enhets krypteringsstatus och beredskap. Rapportinformationen kan hjälpa dig att identifiera problem som förhindrar lyckad kryptering av enheter som du vill skydda.  
- [Visa BitLocker-information (i allmänt tillgänglig förhandsversion)](#bitlocker-recovery-keys) såsom nyckel-ID och återställningsnycklar för dina enheter från Intune-portalen.  

## <a name="encryption-report"></a>Krypteringsrapport
Du kan använda krypteringsrapporten (i allmänt tillgänglig förhandsversion) till att visa information om krypteringsstatusen för dina Windows 10-enheter.  

Du hittar rapporten genom att logga in på [Intune](https://aka.ms/intuneportal), gå till **Enhetskonfiguration** följt av *Övervakare*, där du väljer **Krypteringsrapport (förhandsversion)**.  

### <a name="prerequisites"></a>Krav:
För att en enhet ska visas i krypteringsrapporten måste den köra Windows-version 1607 eller senare.  

### <a name="report-details"></a>Rapportinformation
Rapporten visar **enhetsnamnet** för dina Windows 10-enheter och övergripande information om varje enhet, däribland:  
- **OS-version** – version av Windows.  
- **TPM-version** – versionen av Trusted Platform Module-chipet (TPM) på enheten.  
- **Krypteringsberedskap** – en utvärdering av enhetens beredskap att stödja BitLocker-kryptering. Enheter kan identifieras som:
  - **Redo**: Enheten kan krypteras med hjälp av MDM-princip, vilket kräver att enheten har en TPM och uppfyller följande krav gällande Windows 10-version och SKU:
    - Version 1703 av Business, Enterprise, Education eller senare
    - Version 1809 av Pro eller senare  
  
    Mer information finns i [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) i Windows-dokumentationen.  

  - **Ej redo**: Enheten har inte fullständiga krypteringsfunktioner, men har fortfarande stöd för kryptering. Exempelvis kan vara enheten vara manuellt krypterad av en användare eller via en grupprincip som kan anges till att tillåta kryptering utan en TMP.
  - **Ej tillämpligt**: Det finns inte tillräckligt med information för att klassificera den här enheten.  

- **Krypteringsstatus** – avser huruvida OS-enheten är krypterad.  


### <a name="device-encryption-status"></a>Enhetskrypteringsstatus
När du väljer en enhet visar Intune fönstret **Enhetskrypteringsstatus**.

Det här fönstret innehåller följande information:  
- **Enhetsnamn** – namnet på den enhet som du visar.  
- **Krypteringsberedskap** – en utvärdering av enhetens beredskap att stödja BitLocker-kryptering. En enhet kan ha krypteringsstatusen *Krypterad* även om dess krypteringsberedskap är *Ej redo* eftersom den saknar en TPM. (Mer information finns i Krypteringsberedskap i föregående avsnitt.)
- **Krypteringsstatus** – avser huruvida OS-enheten är krypterad.  
- **Profiler** – en lista över de profiler för *enhetskonfiguration* som gäller för den här enheten, däribland följande profiltyp och inställningar:  
  - Profiltyp = *Slutpunktsskydd*  
  - Inställningar > Windows-kryptering > Kryptera enheter = *Krävs*  

  Den här listan kan vara användbar för att hitta enskilda principer för granskning om sammanfattningen av profiltillstånd visar på problem.  

- **Sammanfattning av profiltillstånd** – en sammanfattning av de profiler som gäller för den här enheten. Sammanfattningen representerar det minst fördelaktiga villkoret över alla tillämpliga profiler. Om en profil till exempel resulterar i ett fel visar sammanfattningen av profiltillstånd *Fel*.  
- **Statusinformation** – avancerad information om enhetens krypteringstillstånd. 
  > [!NOTE]  
  > Intune visar endast *statusinformation* för enheter som kör *Windows-uppdateringen från 10 april 2019* eller senare.
  
  Det här fältet visar information för varje tillämpligt fel som kan identifieras. Du kan använda den här informationen för att förstå varför en enhet kanske inte är redo för kryptering.  

  Följande är några exempel på den statusinformation som Intune kan rapportera:  

   - BitLocker-principen kräver användarens medgivande för att starta guiden för BitLocker-diskkryptering för att starta kryptering av OS-volymen, men användare gav inte sitt medgivande.  
   - OS-volymens krypteringsmetod matchar inte BitLocker-principen.  
   - BitLocker-principen kräver ett TPM-skydd för att skydda OS-volymen, men TPM används inte.  
   - BitLocker-principen kräver ett skydd som endast använder TPM för OS-volymen, men TPM-skydd används inte.  
   - BitLocker-principen kräver skydd med TPM och PIN-kod för OS-volymen, men skydd med TPM och PIN-kod används inte.  
   - BitLocker-principen kräver skydd med TPM och startnyckel för OS-volymen, men skydd med TPM och startnyckel används inte.  
   - BitLocker-principen kräver skydd med TPM, PIN-kod och startnyckel för OS-volymen, men skydd med TPM, PIN-kod och startnyckel används inte.  
   - OS-volymen är inte skyddad.  
   - Säkerhetskopiering av återställningsnyckel misslyckades.  
   - En fast enhet är oskyddad.  
   - Den fasta enhetens krypteringsmetod matchar inte BitLocker-principen.  
   - För att kryptera enheter kräver BitLocker-principen antingen att användaren loggar in som administratör eller, om enheterna är ansluten till Azure AD, att principen AllowStandardUserEncryption anges till 1.  
   - Windows Recovery Environment (WinRE) är inte konfigurerat.  
   - Det finns ingen TPM tillgängligt för BitLocker, antingen eftersom den inte finns eller har gjorts otillgänglig i registret eller att operativsystemet är på en löstagbar enhet.  
   - TPM:en är inte redo för BitLocker.  
   - Nätverket är inte tillgängligt, vilket krävs för säkerhetskopiering av återställningsnyckel.  

## <a name="bitlocker-recovery-keys"></a>BitLocker-återställningsnycklar
Som allmänt tillgänglig förhandsversion ger Intune åtkomst till Azure AD-bladet för BitLocker så att du kan visa BitLocker-nyckel-ID:n och återställningsnycklar för dina Windows 10-enheter från Intune-portalen.  För att enheten ska vara nåbar måste dess nycklar vara deponerade till Azure AD. 
1. Logga in på [Intune](https://aka.ms/intuneportal), gå till **Enheter** följt av *Hantera* och välj **Alla enheter**.
2. Välj en enhet i listan. Under *Övervaka* väljer du sedan **Återställningsnycklar – förhandsversion**.  
  
När nycklar är tillgängliga i Azure AD finns följande information tillgänglig:
- BitLocker-nyckel-ID
- BitLocker-återställningsnyckel
- Enhetstyp  

När nycklar inte finns i Azure AD visar Intune *Det gick inte att hitta någon BitLocker-nyckel för den här enheten*.  

Information för BitLocker hämtas med hjälp av den [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). BitLocker-CSP stöds på Windows 10 version 1703 och senare samt för Windows 10 Pro version 1809 och senare. 

## <a name="next-steps"></a>Nästa steg
Skapa en [enhetsefterlevnadsprincip](compliance-policy-create-windows.md) för Windows 10-enheter för att konfigurera BitLocker och kryptering.
