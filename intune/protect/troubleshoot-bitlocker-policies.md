---
title: Felsökningstips för BitLocker-principer i Microsoft Intune
titleSuffix: Microsoft Intune
description: Beskriver hur du aktiverar BitLocker-kryptering på en enhet med en Intune-princip och hur du verifierar att principen har distribuerats till en enhet.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
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
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556507"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Felsöka BitLocker-principer i Microsoft Intune

Den här artikeln kan hjälpa Intune-administratörer att förstå hur Windows 10-enheter konfigurerar BitLocker baserat på Intune-principer. Den här artikeln innehåller också anvisningar om hur du felsöker problem med BitLocker-inställningar på enheter som du hanterar med Intune.  

## <a name="understanding-bitlocker"></a>Förstå BitLocker

BitLocker-diskkryptering är en tjänst som erbjuds av Microsoft Windows-operativsystem som gör det möjligt för användare att kryptera data på sina hårddiskar. BitLocker stöder kryptering för operativsystemenheter, flyttbara medier och fasta dataenheter. BitLocker stöder också användning av 256-bitars kryptering för bättre skydd av känsliga data.  

Med Microsoft Intune har du följande metoder för att hantera BitLocker på Windows 10-enheter:

- **Principer för enhetskonfiguration** – Vissa inbyggda principalternativ är tillgängliga i Intune när du skapar en enhetskonfigurationsprofil för att hantera slutpunktsskydd. Du hittar dessa alternativ genom att [skapa en enhetsprofil för slutpunktsskydd](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings), välja **Windows 10 och senare** för *Plattform* och sedan välja kategorin **Windows-kryptering** vid *Inställningar*. 

   Du kan läsa om de tillgängliga alternativen och funktionerna här: [Windows-kryptering](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Säkerhetsbaslinjer** - [Säkerhetsbaslinjer](security-baselines.md) är kända grupper av inställningar och standardvärden som rekommenderas av relevanta säkerhetsteam som hjälp att skydda Windows-enheter. Olika baslinjekällor, som *MDM-säkerhetsbaslinje* eller *Microsoft Defender Avancerat skydd-baslinje* kan hantera samma inställningar samt olika inställningar för var och en. De kan också hantera samma inställningar som du hanterar med enhetskonfigurationsprinciper. 

Förutom Intune, för maskinvara som är kompatibel med modernt vänteläge och HSTI, när du använder någon av dessa funktioner aktiveras BitLocker-diskkryptering automatiskt när användaren ansluter en enhet till Azure AD. Azure AD tillhandahåller en portal där återställningsnycklar också säkerhetskopieras så att användarna kan hämta sin egen återställningsnyckel för självbetjäning, om det behövs.

Det är också möjligt att BitLocker-inställningar hanteras på andra sätt, som grupprincip, eller anges manuellt av en enhetsanvändare.

Oavsett hur inställningarna tillämpas på en enhet kan BitLocker-principer använda [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) för att konfigurera kryptering på enheten. BitLocker CSP är inbyggt i Windows och när Intune distribuerar en BitLocker-princip till en tilldelad enhet är det BitLocker CSP på enheten som skriver lämpliga värden till Windows-registret så att inställningarna från principen träder i kraft.

Om du vill veta mer om BitLocker finns följande resurser:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Vanliga frågor och svar om BitLocker – översikt och krav](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Nu när du har en allmän förståelse för vad dessa principer gör och hur de fungerar, kan du titta på hur du kan kontrollera om BitLocker-inställningarna har tillämpats på en Windows-klient.

## <a name="verify-the-source-of-bitlocker-settings"></a>Verifiera källan för BitLocker-inställningar

När du undersöker ett BitLocker-problem på en Windows 10-enhet är det viktigt att först ta reda på om problemet är Intune-relaterat eller Windows-relaterat. När den sannolika källan till felet är känd kan du fokusera på felsökningsåtgärder på rätt plats, och om nödvändigt få support från rätt team.  

Som ett första steg ska du fastställa om Intune-principen har distribuerats till målenheten. I följande exempel har du en princip för enhetskonfigurationsprincip som distribuerar inställningarna för Windows kryptering (BitLocker), som visas här:

![Konfigurationsprincip för Windows-krypterad enhet med inställningarna](./media/troubleshooting-bitlocker-policies/settings.png)

Hur bekräftar du att inställningarna har tillämpats på målenheten? Nedan följer några olika sätt att göra det.

### <a name="device-configuration-policy-device-status"></a>Enhetsstatus för enhetskonfigurationsprincip  

När du använder enhetskonfigurationsprincip för att konfigurera BitLocker kan du kontrollera status för principen i Intune-portalen.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** och välj sedan den profil som innehåller BitLocker-inställningar.

3. När du har valt den profil som du vill visa väljer du **Enhetsstatus**. Enheter som tilldelats profilen visas i listan, och kolumnen *Enhetsstatus* anger om en enhet har distribuerat profilen.

Kom ihåg att det kan vara en fördröjning mellan att enheter tar emot en BitLocker-princip tills enheten är helt krypterad.  

### <a name="use-control-panel-on-the-client"></a>Använda Kontrollpanelen på klienten  

På en enhet som har aktiverat BitLocker och krypterat en enhet kan du visa BitLocker-status från Kontrollpanelen för enheten. Öppna **Kontrollpanelen** > **System och säkerhet** > **BitLocker-diskkryptering** på enheten. Bekräftelse visas på det sätt som visas i följande bild.  

![BitLocker är aktiverat på Kontrollpanelen](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Använda en kommandotolk  

På en enhet som har aktiverat BitLocker och krypterat en enhet startar du kommandotolken med administratörsbehörighet och kör sedan `manage-bde -status`. Resultatet bör likna följande exempel:  
![Ett resultat av statuskommandot](./media/troubleshooting-bitlocker-policies/command.png)

I exemplet:

- **BitLocker-skydd** är **aktiverat**
- **Krypterad andel**  är **100 %**
- **Krypteringsmetod** är **XTS-AES 256**

Du kan också kontrollera **Nyckelskydd** genom att köra följande kommando:

```cmd
Manage-bde -protectors -get c:
```

Eller med PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Granska enhetens registernyckelkonfiguration

När BitLocker-principen har distribuerats till en enhet kan du visa följande registernyckel på enheten där du kan granska konfigurationen av BitLocker-inställningarna:  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Här är ett exempel:

![BitLocker-registernyckel](./media/troubleshooting-bitlocker-policies/registry.png)

Dessa värden konfigureras av BitLocker CSP. Kontrollera att värdena för nycklarna matchar de inställningar som angetts i källan för din Intune-princip för Windows-kryptering. Mer information om var och en av dessa inställningar finns i [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Windows Loggboken innehåller också diverse information som rör BitLocker. Det finns för mycket för att ta upp allt här, men om du söker efter **BitLocker API** hittar du mycket värdefull information.

### <a name="check-the-mdm-diagnostics-report"></a>Läs MDM-diagnostikrapporten

På en enhet som har aktiverat BitLocker kan du generera och visa en MDM-diagnostikrapport från målenheten för att bekräfta att BitLocker-principen är tillgänglig. Om du kan se principinställningarna i rapporten är det också en indikation på att principen har distribuerats. *Microsofts hjälpvideo* som du hittar med följande länk förklarar hur du genererar en MDM-diagnostikrapport från en Windows-enhet.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

När du analyserar MDM-diagnostikrapporten kan innehållet verka lite förvirrande först. Följande är ett exempel som visar hur du korrelerar vad som finns i rapporten med inställningarna i en princip:

![Exempel på MDM-diagnostikrapport](./media/troubleshooting-bitlocker-policies/report.png)

Utdataresultatet visar de värden som motsvarar värdena från BitLocker-principen:

![Utdata visar värdena ](./media/troubleshooting-bitlocker-policies/output.png)

Utdata från MDM-diagnostik:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Du kan läsa i [dokumentationen för BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) för att förstå vad varje värde innebär. I det här exemplet delas ett avsnitt i följande bild.

![Syften för värdena](./media/troubleshooting-bitlocker-policies/shared-example.png)

På samma sätt kan du se alla värden och verifiera dem med BitLocker CSP-länken.

> [!TIP]
> Det primära syftet med MDM-diagnostikrapporten är att hjälpa Microsoft Support vid felsökning av problem. Om du öppnar ett supportärende för Intune och problemet omfattar Windows-klienter, är det alltid en bra idé att sammanställa den här rapporten och inkludera den i din supportbegäran.

## <a name="troubleshooting-bitlocker-policy"></a>Felsöka BitLocker-princip

Du bör nu ha en god förståelse för hur du kontrollerar att BitLocker-principen har distribuerats av Intune, vilket skickar konfigurationen av BitLocker till BitLocker CSP i Windows.

**Principen når inte enheten** – När din Intune-princip inte finns i någon kapacitet:

- **Har enheten registrerats korrekt i Microsoft Intune?** Om inte, måste du åtgärda det innan du felsöker något som rör principen. Hjälp med felsökning av problem med Windows-registrering hittar du [här](../enrollment/troubleshoot-windows-enrollment-errors.md).

- **Finns det en aktiv nätverksanslutning på enheten?** Om enheten är i flygplansläge eller avstängd, eller om användaren har enheten på en plats utan tjänst, kommer principen inte att levereras eller tillämpas förrän nätverksanslutningen har återställts.

- **Distribuerades BitLocker-principen till rätt användar- eller enhetsgrupp?** Kontrollera att rätt användare eller enhet är medlem i de grupper som du riktar in dig på.

**Det finns en princip, men alla inställningar har inte konfigurerats** – När Intune-principen når enheten, men inte alla inställningar har konfigurerats:

- **Misslyckas distributionen av hela principen eller är det bara vissa inställningar som inte tillämpas?** Om du har ett scenario där det bara är vissa principinställningar som inte tillämpas kontrollerar du följande:

  1. **Alla BitLocker-inställningar stöds inte i alla Windows-versioner**.
     Principen kommer till en enhet som en enda enhet, så om vissa inställningar tillämpas och andra inte kan du vara säker på att själva principen tagits emot. I det här scenariot är det möjligt att Windows-versionen på enheten inte stöder de problematiska inställningarna. Se [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) i Windows-dokumentationen för information om versionskrav för varje inställning.

  2. **BitLocker stöds inte på all maskinvara**.
     Även om du har rätt version av Windows är det möjligt att den underliggande enhetsmaskinvaran inte uppfyller kraven för BitLocker-kryptering. Du hittar [systemkraven för BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) i Windows-dokumentationen, men det viktigaste du ska kontrollera är att enheten har ett kompatibelt TPM-chip (1.2 eller senare) och en TCG-kompatibel (Trusted Computing Group) BIOS- eller UEFI-programvara.
     
**BitLocker-kryptering utförs inte tyst** – du har konfigurerat en princip för Endpoint Protection med inställningen "Varning för annan diskkryptering" inställd på blockera och krypteringsguiden visas fortfarande:

- **Bekräfta att Windows-versionen stöder tyst kryptering** Detta kräver minst version 1803. Om användaren inte är administratör på enheten än krävs en lägsta version på 1809. Dessutom har 1809 stöd för enheter som inte stöder modernt vänteläge

**En BitLocker-krypterad enhet visas som ej kompatibel med Intunes efterlevnadsprinciper** – problemet uppstår när BitLocker-krypteringen inte är klar. BitLocker-kryptering kan ta lång tid baserat på faktorer som diskstorlek, antal filer och BitLocker-inställningar. När krypteringen är klar visas enheten som Kompatibel. Enheter kan också vara temporärt inkompatibla direkt efter en nyligen genomförd installation av Windows-uppdateringar.

**Enheter krypteras med en 128-bitars algoritm när principen är unik för 256-bitar** – som standard krypterar Windows 10 en enhet med XTS-AES 128-bitars kryptering. I den här handboken beskrivs [hur du ställer in 256-bitars kryptering för BitLocker under autopilot](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#).


**Exempel på undersökning**

- Du distribuerar en BitLocker-princip till en Windows 10-enhet och inställningen **Kryptera enheter** visar statusen **Fel** i portalen.

- Som namnet antyder tillåter den här inställningen att administratören kan kräva att kryptering aktiveras genom att använda *BitLocker > Enhetskryptering*. Med hjälp av felsökningstipsen som nämnts tidigare tittar du först i MDM-diagnostikrapporten. Rapporten bekräftar att rätt princip har distribuerats på enheten:

  ![Rapporten bekräftar att rätt princip har distribuerats på enheten](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Du verifierar också att registret slutfördes:

  ![Registervärdet RequiredDeviceEncryption visar 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Därefter kontrollerar du status för TPM med hjälp av PowerShell och ser att TPM inte är tillgängligt på enheten:

  ![Kontrollerat TPM-status med hjälp av PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Eftersom BitLocker är beroende av TPM kan du anta att BitLocker inte misslyckas på grund av ett problem med Intune eller principen, utan i stället på grund av att själva enheten inte har något TPM-chip eller att TPM är inaktiverat i BIOS.

  Som ett ytterligare tips kan du kontrollera samma sak i Windows Loggboken under **Program- och tjänsteloggar** > **Microsoft** > **Windows** > **BitLocker API**. I händelseloggen för **BitLocker-API** hittar du händelse-ID 853 som innebär att TPM inte är tillgängligt:

  ![Händelse-ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Du kan också kontrollera TPM-statusen genom att köra **tpm.msc** på enheten.

## <a name="summary"></a>Sammanfattning

När du felsöker problem med BitLocker-principer med Intune och kan bekräfta att principen når den avsedda enheten, är det säkert att anta att problemet inte är direkt relaterat till Intune. Problemet är mer troligt ett problem med Windows OS eller maskinvaran. I det här fallet börjar du titta på andra områden, t.ex. TPM-konfigurationen eller UEFI och säker start).

## <a name="next-steps"></a>Nästa steg  

Följande är fler resurser som kan vara till hjälp när du arbetar med BitLocker:

- [Produktdokumentation för BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Systemkrav för BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Vanliga och frågor svar om BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Dokumentation för BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Principinställningar för Windows-kryptering i Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Maskinvaruoberoende automatisk BitLocker-kryptering med AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [CSP-princip för BitLocker-kryptering på AutoPilot-enheter](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Genomgång för att skapa och distribuera en BitLocker-princip med Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
