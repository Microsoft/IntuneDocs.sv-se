---
title: Registrera Android-enheter automatiskt med hjälp av Samsung Knox Mobile-registrering
titleSuffix: Microsoft Intune
description: Lär dig att registrera Android-enheter med hjälp av Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a637ae12f3a2ee395503bedd595c490579fdb43c
ms.sourcegitcommit: db68056e2db17dfdeaa216c684302567742e6416
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68993555"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering

Det här avsnittet hjälper dig att konfigurera Intune för att registrera stödda Android-enheter med Samsung Knox Mobile-registrering (KME). Genom att använda Intune med Samsung KME kan du registrera ett stort antal företagsägda Android-enheter när slutanvändare sätter på sina enheter för första gången och ansluter till Wi-Fi eller mobilnätet. När du använder Knox-distributionsprogrammet kan enheter också registreras med hjälp av Bluetooth eller NFC.

Om du vill aktivera registrering av Intune med hjälp av Samsung KME använder du både Intune- och Samsung Knox-portalen i den här ordningen:

1. I Knox-portalen:
    1. [Skapa en MDM-profil](#create-mdm-profile)
    2. [Lägg till enheter](#add-devices)
    3. [Tilldela en MDM-profil till enheterna](#assign-an-mdm-profile-to-devices)
2. I Knox-portalen [konfigurera slutanvändarinloggning](#configure-how-end-users-sign-in).
3. [Distribuera enheterna](#distribute-devices).


En lista över enhetsidentifierare (serienummer och IMEI:er) läggs automatiskt till i Knox-portalen när du köper enheter från auktoriserade återförsäljare som deltar i Knox Deployment Program.


## <a name="prerequisites"></a>Krav

För att registrera dig till Intune med KME måste du först registrera ditt företag på Samsung Knox-portalen genom att följa dessa steg:
1. [Kontrollera att KME är tillgängligt i ditt land/din region](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME är tillgängligt i över 55 länder/regioner. Kontrollera att ditt land/din region för distribution stöds.

2. [Enheter som stöds](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME är tillgängligt på alla Samsung-enheter med minst Knox 2.4 för Android-registrering och minst Knox 2.8 för Android Enterprise-registrering.

3. [Nätverkskrav](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Kontrollera att nödvändiga åtkomstregler för brandvägg och nätverk tillåts i nätverket.

4. [Registrera ett Samsung-konto](https://www2.samsungknox.com/en/user/register): Ett Samsung-konto krävs för att registrera och aktivera KME, samt hantera alla Knox Enterprise-rättigheter på en enda plats.

5. Registreringsgranskning: När din profil har slutförts och skickats, granskar Samsung ditt program och antingen godkänner det direkt eller placerar det i en väntande granskningsstatus för ytterligare uppföljning. När ditt konto har godkänts, kan du fortsätta med ytterligare steg.

## <a name="create-mdm-profile"></a>Skapa MDM-profil

När ditt företag har registrerats kan du skapa din MDM-profil för Microsoft Intune på Knox-portalen med hjälp av informationen nedan. Du kan skapa MDM-profiler både för Android och Android Enterprise på Knox-portalen. 

### <a name="for-android-enterprise"></a>För Android Enterprise

| Fält för MDM-profil| Obligatoriskt? | Värden | 
|-------------------|-----------|-------| 
|URI för MDM-server     | Nej        |Lämna tomt. 
|Profilnamn       | Ja       |Ange ett önskat profilnamn. 
|Beskrivning        | Nej        |Ange text som beskriver profilen. 
|APK för MDM-agenten      | Ja       |https://aka.ms/intune_kme_deviceowner 
|Aktivera den här appen som en Google-enhetsägare | Ja | Välj det här alternativet för registrering i Android Enterprise. 
|MDM-stöd      | Ja       |Microsoft Intune 
|Lämna alla systemappar aktiverade | Nej | Välj det här alternativet för att se till att alla appar är aktiverade och tillgängliga för profilen. Om det här alternativet inte är markerat visas endast en begränsad uppsättning systemappar i enhetens appfält. Appar som exempelvis e-postappen förblir dolda. 
|Anpassad JSON        | Nej        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Enter Intune enrollment token string"}. Lär dig [hur du skapar en registreringsprofil](android-kiosk-enroll.md). 
| Lägga till juridiska avtal | Nej | Lämna tomt. 

### <a name="for-android"></a>För Android

Detaljerade anvisningar finns i [Installationsguiden för Samsung Knox-profil](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm).

| Fält för MDM-profil| Obligatoriskt? | Värden |
|-------------------|-----------|-------|
|URI för MDM-server     | Nej        |Lämna tomt.
|Profilnamn       | Ja       |Ange ett önskat profilnamn.
|description        | Nej        |Ange text som beskriver profilen.
|APK för MDM-agenten      | Ja       |https://aka.ms/intune_kme
|Aktivera den här appen som en Google-enhetsägare | Nej | Lämna det här alternativet omarkerat för Android. Detta alternativ gäller endast för Android Enterprise.
|Hoppa över installationsguiden  | Nej        |Välj det här alternativet för att hoppa över standardenhetens installationsuppmaning för slutanvändarens räkning.
|Tillåt slutanvändaren att avbryta registreringen | Nej | Välj det här alternativet om du vill tillåta användare att avbryta KME.
|Anpassad JSON        | Nej        |Lämna tomt.
| Lägga till juridiska avtal | Nej | Lämna tomt.
Associera en Knox-licens med den här profilen | Nej | Låt alternativet vara omarkerat. Registrering på Intune med KME kräver inte en Knox-licens.

## <a name="add-devices"></a>Lägg till enheter

Om du vill tilldela MDM-profiler till enheter måste stödda Samsung Knox-enheter läggas till på Knox-portalen med någon av följande metoder:
- **Använda Samsung-godkänd(a) återförsäljare:** Använd den här metoden om du köper enheter från en Samsung-godkänd återförsäljare. Återförsäljare kan automatiskt ladda upp enheter åt dig när de har godkänts. [Besök användarhandboken för Samsung Knox-registrering för att lära dig hur du lägger till återförsäljare](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Använda Knox Deployment App (KDA):** Använd den här metoden om du har befintliga enheter som behöver registreras med hjälp av KME. Du kan antingen använda Bluetooth eller NFC för att lägga till enheter till Knox-portalen med den här metoden. [Besök användarhandboken för Samsung Knox-registrering för att lära dig hur du använder KDA](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Tilldela en MDM-profil till enheter
Du måste tilldela en MDM-profil till enheter som lagts till i Knox-portalen innan de kan registreras. [Besök användarhandboken för Samsung Knox-registrering för att lära dig hur du konfigurerar enheter](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Konfigurera hur användarna loggar in

För enheter som registrerats i Intune med KME för Android kan du konfigurera hur en användare loggar in på följande sätt:

- **Utan association till användarnamnet:** I Knox-portalen under **Enhetsinformation** lämnar du fältet **Användar-ID** och **Lösenord** tomt för de enheter som har lagts till. Detta alternativ kräver att användaren måste ange både användarnamn och lösenord vid registrering i Intune.

- **Med association till användarnamnet:** I Knox-portalen under **Enhetsinformation** anger du ett **Användar-ID** (till exempel ett användarnamn för den tilldelade användaren eller ett konto för [Enhetsregistreringshanteraren](https://docs.microsoft.com/intune/device-enrollment-manager-enroll)) för de enheter som har lagts till. Detta alternativ fyller i användarnamnet i förväg och kräver att användaren måste ange ett lösenord vid registrering i Intune.

> [!NOTE]
>
>Användarassociation gäller endast för Android-registrering. När användarassociationen definieras kan bara associerad användare registrera enheten med KME. Detta gäller även efter en fabriksåterställning på enheten. Om ingen användarassociation har definierats på Knox-portalen kan alla användare med en giltig licens för Intune registrera enheten med KME.
>

## <a name="distribute-devices"></a>Distribuera enheter

När du har skapat och tilldelat en MDM-profil, kopplat ett användarnamn och identifierat enheterna som företagsägda i Intune, kan du distribuera enheter till användare.

Behöver du fortfarande hjälp? Kolla in den kompletta [KME-användarguiden](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

- **Support för enhetsägare:**  - **Support för enhetsägare:** Intune stöder registrering av dedikerade och fullständigt hanterade enheter med hjälp av KME-portalen. Stöd för andra Android Enterprise-enhetsägarlägen implementeras allt eftersom de blir tillgängliga i Intune.

- **Inget stöd för arbetsprofiler:** KME är en metod för registrering av företagets enheter och enheter som registreras i Android-arbetsprofiler som säkerställer att arbetsrelaterade och personliga data separeras på de privata enheterna. Registrering av enheter till arbetsprofilen med KME är därför inte ett scenario som stöds i Intune.

- **Fabriksåterställning vid registrering i Android Enterprise:** Om syftet för redan konfigurerade enheter ändras, måste enheterna fabriksåterställas när de registreras i Android Enterprise.

- **Uppdateringar med hjälp av Google Play-konto:** Ett Google Play-konto är inte nödvändigt för att registrera enheten till Microsoft Intune. Men framtida uppdateringar till företagsportalappen kan kräva ett Google Play-konto på enheten. Inget Google Play-konto krävs vid registrering i Google-enhetsägarläge.

- **Fältet ”Lösenord” ignoreras:** Om fältet **Lösenord** fylls i vid **Enhetsinformation** i Knox-portalen, ignoreras det av Intune-företagsportalappen under Android-registreringen. Användaren måste ange ett lösenord på enheten för att slutföra enhetsregistreringen.


## <a name="getting-support"></a>Få support
Lär dig mer om att [få support för Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


