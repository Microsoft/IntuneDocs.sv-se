---
title: Tilldela appar till grupper i Microsoft Intune
titlesuffix: ''
description: Lär dig att tilldela en Intune-app till användargrupper eller enheter med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b0c2bff4051a1adba1a68f38d8f0a9b80b914b4
ms.sourcegitcommit: 5708ec1d7ae50494be44ed5064f150b636188c84
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56240069"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Tilldela appar till grupper med Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

När du har [lagt till en app](apps-add.md) till Microsoft Intune kan du tilldela appen till användare och enheter. Lägg märke till att du kan tilldela en app till en enhet oavsett om enheten hanteras av Intune eller inte.

> [!NOTE]
> Tillgänglig distributionsavsikt stöds inte för enhetsgrupper – det är bara användargrupper som stöds.

I följande tabell visas de olika alternativen för att tilldela appar till användare och enheter:

|   | Enheter registrerade med Intune | Enheter ej registrerade med Intune |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Tilldela till användare | Ja | Ja |
| Tilldela till enheter | Ja | Nej |
| Tilldela omslutna appar eller appar med Intune SDK (för skydd av apprinciper) | Ja | Ja |
| Tilldela appar som är tillgängliga | Ja | Ja |
| Tilldela appar vid behov | Ja | Nej |
| Avinstallera appar | Ja | Nej |
| Ta emot appuppdateringar från Intune | Ja | Nej |
| Slutanvändare installerar tillgängliga appar från företagsportalappen | Ja | Nej |
| Slutanvändare installerar tillgängliga appar från den webbaserade företagsportal | Ja | Ja |

> [!NOTE]
> För närvarande kan du tilldela iOS- och Android-appar (verksamhetsspecifika och butiksköpta appar) till enheter som inte är registrerade med Intune.
>
> För att ta emot app-uppdateringar på enheter som inte är registrerade med Intune, måste enhetsanvändare gå till sin organisations företagsportal och manuellt installera app-uppdateringarna.

## <a name="assign-an-app"></a>Tilldela en app

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** på **Intune**-menyn.
4. I avsnittet**Hantera** på menyn, väljer du **Appar**.
5. I fönstret **Appar** välj den app som du vill tilldela.
6. I avsnittet**Hantera** på menyn, väljer du **Tilldelningar**.
7. Välj **Lägg till grupp** för att öppna fönstret **Lägg till grupp** som är relaterat till appen.
8. Välj en **Tilldelningstyp** för den specifika appen:
   - **Tillgänglig för registrerade enheter**: Tilldela appen till användargrupper som kan installera appen från företagsportalappen eller webbplatsen.
   - **Tillgänglig med eller utan registrering**: Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune. Användarna måste tilldelas en Intune-licens, se [Intune-licenser](licenses.md).
   - **Obligatoriskt**: Appen installeras på enheter i valda grupper. Vissa plattformar kan ha ytterligare uppmaningar som användaren ska bekräfta innan appinstallationen påbörjas.
   - **Avinstallera**: Appen avinstalleras från enheter i valda grupper om Intune tidigare har installerat programmet på enheten via tilldelningen ”Tillgänglig för registrerade enheter” eller ”Obligatorisk” med hjälp av samma distribution. Webblänkar kan inte tas bort efter distributionen.

     > [!NOTE]
     > **Endast för iOS-appar**: Om du har skapat en iOS VPN-profil som innehåller VPN-inställningar per app, kan du välja VPN-profilen under **VPN**. VPN-anslutningen öppnas när appen körs. Mer information finns i [VPN-inställningar för iOS-enheter](vpn-settings-ios.md).
     >
     > **Endast för Android-appar**: Om du distribuerar en Android-app som **Tillgänglig med eller utan registrering**, blir den rapporterade statusen endast tillgänglig på registrerade enheter.

9. Välj **Inkluderade grupper** för att välja vilka grupper av användare som ska påverkas av den här apptilldelningen.
10. Klicka på **Välj** när du har valt en eller flera grupper som ska inkluderas.
11. Klicka på **OK** i fönstret **Tilldela** för att slutföra valet av inkluderade grupper.
12. Välj **Exkludera grupper** om du vill undanta grupper av användare så att de inte påverkas av den här apptilldelningen.
13. Om du har valt att undanta grupper i **Välj grupper**, klicka på **Välj**.
14. I fönstret **Lägg till grupp** väljer du **OK**.
15. I appfönstret **Tilldelningar** väljer du **Spara**.

Appen har nu tilldelats till de grupper du valde. Mer information om hur du inkluderar och exkluderar apptilldelningar finns i [Inkludera och exkludera apptilldelningar](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Lösa konflikter mellan appavsikter

Ibland har samma app tilldelats flera grupper, men med olika avsikter. Informationen i tabellen nedan kan hjälpa dig att förstå resulterande avsikt när detta inträffar:

| Avsikt för grupp 1 | Avsikt för grupp 2 | Resulterande avsikt |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Nödvändig för användare|Tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig för användare|Inte tillgänglig för användare|Obligatoriskt|
|Nödvändig för användare|Avinstalleras för användare|Obligatoriskt|
|Tillgänglig för användare|Inte tillgänglig för användare|Inte tillgängligt|
|Tillgänglig för användare|Avinstallation av användare|Avinstallera|
|Inte tillgänglig för användare|Avinstalleras för användare|Avinstallera
|Nödvändig för användare|Nödvändig för enhet|Båda finns, hanteras som nödvändig av Intune
|Nödvändig för användare|Avinstalleras för enhet|Båda finns, löses som nödvändig av Intune
|Tillgänglig för användare|Nödvändig för enhet|Båda finns, matchas som nödvändig av Intune (nödvändig och tillgänglig)
|Tillgänglig för användare|Avinstalleras för enhet|Båda finns, löses som tillgänglig av Intune.<br><br>Appen visas i företagsportalen.<br><br>Appen avinstalleras om den redan har installerats (som nödvändig app med föregående avsikt).<br><br>Om användaren väljer **Installera i företagsportalen** installeras appen och avinstallationen åsidosätts.|
|Inte tillgänglig för användare|Nödvändig för enhet|Obligatoriskt|
|Inte tillgänglig för användare|Avinstalleras för enhet|Avinstallera|
|Avinstalleras för användare|Nödvändig för enhet|Båda finns, löses som nödvändig av Intune|
|Avinstalleras för användare|Avinstalleras för enhet|Båda finns, löses som tillgänglig av Intune|
|Nödvändig för enhet|Avinstalleras för enhet|Obligatoriskt|
|Nödvändig och tillgänglig för användare|Tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Avinstalleras för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Inte tillgänglig för användare|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Nödvändig för enhet|Båda finns, nödvändig och tillgänglig
|Nödvändig och tillgänglig för användare|Inte tillgänglig för enhet|Nödvändig och Tillgänglig|
|Nödvändig och tillgänglig för användare|Avinstalleras för enhet|Båda finns, matchas som nödvändig av Intune (nödvändig och tillgänglig)
|Inte tillgänglig för användare|Inte tillgänglig för enhet|Inte tillgängligt|
|Tillgänglig för användare|Inte tillgänglig för enhet|Tillgänglig|
|Nödvändig för användare|Inte tillgänglig för enhet|Obligatoriskt|
|Tillgänglig för användare utan registrering|Nödvändig och tillgänglig för användare|Nödvändig och Tillgänglig
|Tillgänglig för användare utan registrering|Nödvändig för användare|Obligatoriskt
|Tillgänglig för användare utan registrering|Inte tillgänglig för användare|Inte tillgängligt
|Tillgänglig för användare utan registrering|Tillgänglig för användare|Tillgänglig|
|Tillgänglig för användare utan registrering|Nödvändig för enhet|Nödvändig och tillgänglig utan registrering|
|Tillgänglig för användare utan registrering|Inte tillgänglig för enhet|Tillgänglig utan registrering|
|Tillgänglig för användare utan registrering|Avinstalleras för enhet|Avinstalleras och tillgänglig utan registrering.<br><br>Avinstallationsavsikten åsidosätts inte om användaren inte har installerat appen från företagsportalen.<br><br>Om användaren installerar appen från företagsportalen prioriteras installation framför avinstallation.|

> [!NOTE]
> Endast för hanterade iOS Store-appar. När du lägger till dem i Microsoft Intune och tilldelar dem som **Nödvändiga** skapas apparna automatiskt med både avsikten **Nödvändig** och **Tillgänglig**.<br><br>
> iOS Store-appar (inte iOS VPP-appar) som är riktade med nödvändigt syfte tillämpas på enheten vid tidpunkten för incheckning och visas även i företagsportalappen.

## <a name="managed-google-play-app-deployment-to-unmanaged-devices"></a>Hanterad Google Play-appdistribution till ohanterade enheter
Om du har Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE), kan du använda hanterad Google Play till att distribuera Store-appar och verksamhetsspecifika appar (LOB) till användarna. Hanterade Google Play-appar som riktas mot **Tillgängliga med eller utan registrering** visas i Play Store-appen på slutanvändarens enhet och inte i företagsportalappen. Slutanvändaren kan bläddra och installera appar som distribueras på det här sättet från Play-appen. Eftersom apparna installeras från hanterad Google Play, behöver användaren inte ändra sina enhetsinställningar till att tillåta appinstallation från okända källor, vilket innebär att enheterna blir säkrare. Om apputvecklaren publicerar en ny version av en app i Play som har installerats på en användares enhet, kommer appen uppdateras automatiskt av Play. 

Anvisningar för att tilldela en hanterad Google Play-app till ohanterade enheter:

1. Anslut Intune-klientorganisationen till hanterade Google Play. Om du redan har gjort detta för att kunna hantera arbetsprofilen för Android Enterprise, dedikerade eller fullständigt hanterade enheter, behöver du inte göra det igen.
2. Lägg till appar från hanterad Google Play i Intune-konsolen.
3. Rikta hanterade Google Play-appar som **Tillgänglig med eller utan registrering** till önskad användargrupp. Appriktningarna **Obligatorisk** och **Avinstallera** stöds inte för icke-registrerade enheter.
4. Tilldela en appskyddsprincip till användargruppen.
5. Nästa gång slutanvändaren öppnar företagsportalappen visas ett meddelande om att det finns tillgängliga appar i Play Store-appen.  Användaren kan antingen trycka på meddelandet för att komma direkt till Play-appen och se företagets appar, eller navigera till Play Store-appen separat.
6. Slutanvändarna kan expandera snabbmenyn i Play Store-appen och växla mellan sina personliga Google-konton (där de kan se sina privata appar) och sina arbetskonton (där de ser Store- och LOB-appar som är avsedda för dem). Slutanvändarna installerar apparna genom att trycka på Installera i Play Store-appen.

När en selektiv rensning av appskyddsprinciper görs i Intune-konsolen, tas arbetskontot automatiskt bort från Play Store-appen. Slutanvändaren kommer därefter inte längre se några arbetsappar i Play Stores appkatalog. När arbetskontot tas bort från en enhet förblir appar som installerats från Play Store installerade på enheten och kommer inte att avinstalleras. 

## <a name="next-steps"></a>Nästa steg

Mer information om hur du övervakar apptilldelningar finns i [Hur du övervakar appar](apps-monitor.md).
