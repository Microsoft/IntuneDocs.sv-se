---
title: Fel söknings tips för BitLocker-principer i Microsoft Intune
titleSuffix: Microsoft Intune
description: Beskriver hur du aktiverar BitLocker-kryptering på en enhet med Intune-princip och hur du verifierar att principen har distribuerats till en enhet.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 440eb2d457783ac71b905d064a6d83abaa966cfe
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503894"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Felsöka BitLocker-principer i Microsoft Intune

Den här artikeln kan hjälpa Intune-administratörer att förstå hur Windows 10-enheter konfigurerar BitLocker baserat på Intune-principer. Den här artikeln innehåller också anvisningar om hur du felsöker problem med BitLocker-inställningar på enheter som du hanterar med Intune.  

## <a name="understanding-bitlocker"></a>Förstå BitLocker

BitLocker-diskkryptering är en tjänst som erbjuds av Microsoft Windows-operativsystem som gör det möjligt för användare att kryptera data på sina hård diskar. BitLocker stöder kryptering för operativ system enheter, flyttbara medie enheter och fasta data enheter. BitLocker stöder också användning av 256-bitars kryptering för bättre skydd av känsliga data.  

Med Microsoft Intune har du följande metoder för att hantera BitLocker på Windows 10-enheter:

- Princip för **enhets konfiguration** – vissa inbyggda princip alternativ är tillgängliga i Intune-administratörskonsolen i **enhets konfiguration**  > **Endpoint Protection**  > **Windows-krypterings princip**. Du kan hitta alla tillgängliga växlar och funktioner här: [Windows-kryptering](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Säkerhets bas linjer**  - [säkerhets bas linjer](security-baselines.md) är kända grupper av inställningar och standardvärden som rekommenderas av relevant säkerhets team för att skydda Windows-enheter. Olika bas linje källor, som *säkerhets bas linjen för MDM* eller *Microsoft Defender ATP-bas linje* kan hantera samma inställningar och andra inställningar än varandra. De kan också hantera samma inställningar som du hanterar med enhets konfigurations principer. 

Förutom Intune är det möjligt att BitLocker-inställningar hanteras av andra sätt som grupprincip eller manuellt anges av en enhets användare.

Oavsett hur inställningarna tillämpas på en enhet kan BitLocker-principer använda BitLocker-CSP: [n](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) för att konfigurera kryptering på enheten. BitLocker CSP är inbyggt i Windows och när Intune distribuerar en BitLocker-princip till en tilldelad enhet är det BitLocker CSP på enheten som skriver lämpliga värden till Windows-registret så att inställningarna från principen träder i kraft.

Om du vill veta mer om BitLocker kan du läsa resurserna nedan.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Vanliga frågor och svar om BitLocker – krav](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Nu när du har en allmän förståelse för vad dessa principer gör och hur de fungerar, tittar du på hur du kan kontrol lera om BitLocker-inställningarna har tillämpats på en Windows-klient.

## <a name="verify-the-source-of-bitlocker-settings"></a>Verifiera källan för BitLocker-inställningar

När du undersöker ett BitLocker-problem på en Windows 10-enhet är det viktigt att först ta reda på om problemet är Intune-relaterat eller Windows-relaterat. När den sannolika källan till felet är känd kan du sedan fokusera på fel söknings åtgärder på rätt plats och om nödvändigt få support från rätt team.  

Som ett första steg bestämmer du om Intune-principen har distribuerats till mål enheten. I följande exempel har du en princip för enhets konfiguration som distribuerar Windows krypterings inställningar (BitLocker), som visas: 

![Konfigurations princip för Windows-krypterad enhet med inställningarna](./media/troubleshooting-bitlocker-policies/settings.png)

Hur bekräftar du att inställningarna har tillämpats på mål enheten? Nedan följer några olika sätt att göra det.

### <a name="device-configuration-policy-device-status"></a>Enhets konfigurations princip enhets status  

När du använder enhets konfigurations principer för att konfigurera BitLocker kan du kontrol lera status för principen i Intune-portalen. I portalen går du till **enhets konfiguration**  > **profiler** > väljer du den profil som innehåller BitLocker-inställningar och väljer sedan **enhets status**. Enheter som tilldelats profilen visas i listan och kolumnen *enhets status* anger om en enhet har distribuerat profilen. 

Kom ihåg att det kan finnas en fördröjning mellan en enhet som tar emot en BitLocker-princip och att enheten är helt krypterad.  

 
### <a name="use-control-panel-on-the-client"></a>Använda kontroll panelen på klienten  

På en enhet som har aktiverat BitLocker och krypterat en enhet kan du Visa BitLocker-status från en kontroll panel för enheter. Öppna **kontroll panelen**  > **system-och säkerhets**  > **BitLocker-diskkryptering**på enheten. Bekräftelse visas på det sätt som visas i följande bild.  

![BitLocker är aktiverat på kontroll panelen](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Använda en kommandotolk  

På en enhet som har aktiverat BitLocker och krypterat en enhet startar du kommando tolken med administratörs behörighet och kör sedan `manage-bde -status`. Resultaten bör likna följande exempel:  
![A resultatet av kommandot status ](./media/troubleshooting-bitlocker-policies/command.png)

I exemplet: 
- **BitLocker-skydd** är **aktiverat**,  
- **Procent andelen krypterad** är **100%**  
- **Krypterings metoden** är **XTS-AES 256**.  

Du kan också kontrol lera **nyckel skydd** genom att köra följande kommando:

```cmd
Manage-bde -protectors -get c:
```

Eller med PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Granska enhetens register nyckel konfiguration   

När BitLocker-principen har distribuerats till en enhet kan du visa följande register nyckel på enheten där du kan granska konfigurationen av BitLocker-inställningar: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . Här är ett exempel:

![BitLocker register nyckel](./media/troubleshooting-bitlocker-policies/registry.png)

Dessa värden konfigureras av BitLocker CSP. Kontrol lera att värdena för nycklarna matchar de inställningar som anges i källan för din Intune-princip för Windows-kryptering. Mer information om var och en av dessa inställningar finns i [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Windows Loggboken innehåller också olika information som rör BitLocker. Det finns för många att lista här, men om du söker efter **BITLOCKER API** får du mycket värdefull information.

### <a name="check-the-mdm-diagnostics-report"></a>Kontrol lera rapporten för MDM-diagnostik  

På en enhet som har aktiverat BitLocker kan du generera och visa en MDM-diagnostisk rapport från mål enheten för att bekräfta att BitLocker-principen är tillgänglig. Om du kan se princip inställningarna i rapporten, är det en annan indikation på att principen har distribuerats. *Microsoft hjälper dig* att skapa en MDM-diagnostisk rapport från en Windows-enhet i följande länk. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

När du analyserar rapporten MDM-diagnostik kan innehållet verka lite förvirrande först. Följande är ett exempel som visar hur du korrelerar vad som finns i rapporten med inställningarna i en princip:

![Exempel på MDM-diagnostik](./media/troubleshooting-bitlocker-policies/report.png)

Resultatet av utdata visar de värden som motsvarar värdena från BitLocker-principen:

![Resultatet visar värdena ](./media/troubleshooting-bitlocker-policies/output.png)

Utdata från MDM-diagnostik:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Du kan referera till [dokumentationen för BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) för att se vad varje värde innebär. I det här exemplet delas ett kodfragment i följande bild.

![Syfte med värden](./media/troubleshooting-bitlocker-policies/shared-example.png)

 På samma sätt kan du se alla värden och verifiera dem från BitLocker CSP-länken.

> [!TIP]
> Det primära syftet med MDM-Diagnostikrapporten är att hjälpa Microsoft Support vid fel sökning av problem. Om du öppnar ett support ärende för Intune och problemet omfattar Windows-klienter, är det alltid en bra idé att samla in rapporten och ta med den i din support förfrågan.

## <a name="troubleshooting-bitlocker-policy"></a>Felsöka BitLocker-princip

Du bör nu ha en bra idé att kontrol lera att BitLocker-principen har distribuerats av Intune, som tar bort konfigurationen av BitLocker till BitLocker CSP i WIndows.  

**Principen kan inte komma åt enheten** – när din Intune-princip inte finns i någon kapacitet:  
- **Är enheten korrekt registrerad i Microsoft Intune?** Om inte, måste du åtgärda det innan du felsöker vad som är möjligt för principen. Hjälp med fel sökning av problem med Windows-registrering hittar du [här](../enrollment/troubleshoot-windows-enrollment-errors.md).  
- **Finns det en aktiv nätverks anslutning på enheten?** Om enheten är i flyg Plans läge eller stängs av, eller om användaren har enheten på en plats utan tjänst, kommer principen inte att levereras eller tillämpas förrän nätverks anslutningen har återställts.  
- **Distribuerade BitLocker-principen till rätt användare eller enhets grupp?** Kontrol lera att rätt användare eller enhet är medlem i de grupper som du riktar in dig på.  

Det finns en **princip, men alla inställningar har inte kon figurer ATS** – när Intune-principen når enheten, men inte alla konfigurationer är inställda:  
- **Miss söker distributionen av hela principen eller är det bara vissa inställningar som inte gäller?** Om du har hittat ett scenario där endast vissa princip inställningar inte gäller kontrollerar du följande:

  1. Alla **BitLocker-inställningar stöds inte i alla Windows-versioner**.  
  Principen kommer ned till en enhet som en enda enhet, så om vissa inställningar gäller och andra inte kan du vara säker på att själva principen tas emot. I det här scenariot är det möjligt att Windows-versionen på enheten inte stöder de problematiska inställningarna. Se [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) i Windows-dokumentationen för information om versions krav för varje inställning.  

  1. **BitLocker stöds inte på all maskin vara**.  
  Även om du har rätt version av Windows, är det möjligt att den underliggande enhetens maskin vara inte uppfyller kraven för BitLocker-kryptering. Du hittar [system kraven för BitLocker (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) i Windows-dokumentationen, men de viktigaste sakerna att kontrol lera är att enheten har ett kompatibelt TPM-chip (1,2 eller senare) och en Trusted Computing Group (TCG)-kompatibel BIOS eller UEFI-programvara.

**Exempel på undersökning** – du distribuerar en BitLocker-princip till en Windows 10-enhet och inställningen för att **kryptera enheter** visar statusen **fel** i portalen.

- Som namnet antyder kan en administratör kräva att kryptering aktive ras genom att använda *BitLocker-> enhets kryptering*. Med hjälp av de fel söknings tips som nämnts tidigare, kontrollerar du först rapporten MDM-diagnostik. Rapporten bekräftar att rätt princip har distribuerats på enheten:

  ![Rapporten bekräftar att rätt princip har distribuerats på enheten](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Du verifierar också att det lyckades i registret:

  ![Register värde för RequiredDeviceEncryption Visar 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Sedan kan du kontrol lera status för TPM med PowerShell och se att TPM inte är tillgänglig på enheten:

  ![Kontrollerad TPM-status med PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Eftersom BitLocker är beroende av TPM kan du sluta att BitLocker inte fungerar på grund av ett problem med Intune eller principen, utan i stället eftersom själva enheten inte har något TPM-chip eller om TPM är inaktive rad i BIOS.

  Som ett ytterligare tips kan du kontrol lera att det är samma i Windows Loggboken under **program-och tjänst loggar**  > **Windows**  > **BitLocker-API**. I händelse loggen för **BitLocker-API** hittar du en händelse-ID 853 som innebär att TPM inte är tillgänglig:

  ![Händelse-ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Du kan också kontrol lera TPM-statusen genom att köra **TPM. msc** på enheten.



## <a name="summary"></a>Sammanfattning

När du felsöker problem med BitLocker-principer med Intune och kan bekräfta att principen når den avsedda enheten, är det säkert att anta att problemet inte är direkt relaterat till Intune. Problemet är troligt vis ett problem med Windows OS eller maskin varan. I det här fallet börjar du titta på andra områden, t. ex. TPM-konfigurationen eller UEFI och säker start).

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>Nästa steg  

Följande är fler resurser som kan vara till hjälp när du arbetar med BitLocker:

- [Produkt dokumentation för BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [System krav för BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Vanliga och frågor svar om BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Dokumentation om BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Princip inställningar för Windows-kryptering i Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Maskin vara oberoende automatisk BitLocker-kryptering med AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [CSP-princip för BitLocker-kryptering på enheter för automatisk pilot](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Genom gång för att skapa och distribuera en BitLocker-princip med Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)