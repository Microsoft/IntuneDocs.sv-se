---
title: "Intune-inställningar för iOS-appen Klassrum | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar i Klassrum-appen på iOS-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: f9e8a5deb17ebb77d480213567e5ccf6550e3493
ms.openlocfilehash: 3c7ab3e33f7a1a97cd8048be059cf2f74deb00c1
ms.contentlocale: sv-se
ms.lasthandoff: 05/03/2017


---


# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>Så här konfigurerar du inställningar för iOS-appen Klassrum för Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="introduction"></a>Introduktion
[Klassrum](https://itunes.apple.com/app/id1085319084) är en app som hjälper lärare att styra undervisningen och kontrollera elevenheterna i klassrummet. Med hjälp av appen kan läraren till exempel:

- Öppna appar på elevenheter
- Låsa och låsa upp iPad-skärmen
- Visa skärmen på en elev-iPad
- Navigera elevers iPad-enheter till ett bokmärke eller ett kapitel i en bok
- Visa skärmen från en elevs iPad på en Apple TV

Använda Intunes enhetsprofil för iOS **Utbildning** och informationen i det här avsnittet för att konfigurera appen Klassrum och de enheter som du använder den på.

## <a name="before-you-start"></a>Innan du börjar

Tänk på följande innan du börjar konfigurera inställningarna:

- Både lärarens och elevernas iPad-enheter måste registreras i Intune
- Kontrollera att du har installerat appen [Apple Klassrum](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) på lärarens enhet. Du kan göra detta manuellt eller använda [Intune apphantering](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management).
- Du måste konfigurera certifikat för att autentisera anslutningar mellan lärarens och elevernas enheter (se steg 2)
- Lärarens och elevernas iPad-enheter måste finnas i samma Wi-Fi-nätverk och även ha Bluetooth aktiverat
- Appen Klassrum appen körs på övervakade iPad-enheter som kör iOS 9.3 eller senare
- I den här versionen stöder Intune hantering av ett 1:1-scenario, där varje elev har sin egen iPad


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Steg 1 – Importera din skolinformation till Azure Active Directory

Använd Microsoft SDS (School Data Sync) för att importera skolinformation från ett befintligt elevinformationssystem (SIS) till Azure Active Directory (Azure AD).
SDS synkroniserar information från din SIS och lagrar den i Azure AD. Azure AD är ett Microsoft-hanteringssystem som hjälper dig att organisera användare och enheter. Du kan sedan använda dessa data för att hantera dina elever och klasser. [Läs mer om att distribuera SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Hur importerar jag data med SDS?

Du kan importera information till SDS på något av följande sätt:

- [CSV-filer](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) – Exportera manuellt och kompilera (.csv-) filer med kommaseparerade värden
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) – En SIS-provider som förenklar synkronisering med Azure AD
- [Clever API](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) – En lösning för identitetshantering som synkroniserar direkt med Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) – Ett CSV-format som du kan exportera och konvertera för synkronisering med Azure AD

### <a name="find-out-more"></a>Läs mer

- [Läs mer om hur du kan synkronisera lokal skolinformation till Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Läs mer om Microsofts synkronisering av skolinformation](https://sds.microsoft.com/)
- [Läs mer om licensiering i Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Steg 2 – Skapa och tilldela en iOS-utbildningsprofil i Intune

### <a name="configure-general-settings"></a>Konfigurera allmänna inställningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3.    Välj **Konfigurera enheter** på **Intune**-bladet.
4.    Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
5.    Välj **Skapa profil** på profilbladet.
6.    Ange **Namn** och **Beskrivning** för iOS-utbildningsprofilen på bladet **Skapa profil**.
7.    Välj **iOS** i listrutan **Plattform**.
8.    Välj **Utbildning** i listrutan **Profiltyp**.
9.    Välj **Inställningar** > **Konfigurera**.


Du behöver sedan certifikat för att upprätta en förtroenderelation mellan lärarens och elevernas iPad-enheter. Certifikat används för att smidigt och tyst autentisera anslutningar mellan enheter utan att behöva ange användarnamn och lösenord.

>[!IMPORTANT]
>De lärar- och elevcertifikat som du använder måste utfärdas av olika certifikatutfärdare (CA). Du måste skapa två nya underordnade certifikatutfärdare som är anslutna till din befintliga infrastruktur för certifikat; en för lärare och en för elever.

iOS-utbildningsprofiler stöder endast PFX-certifikat, SCEP-certifikat stöds inte.

Certifikat som du skapar måste ha stöd för serverautentisering förutom användarautentisering.

### <a name="configure-teacher-certificates"></a>Konfigurera lärarcertifikat

Välj **Lärarcertifikat** på bladet **Utbildning**.

#### <a name="configure-teacher-root-certificate"></a>Konfigurera rotcertifikat för lärare

Klicka på bläddringsknappen under **Rotcertifikat för lärare** för att välja lärarens rotcertifikat med tillägget .cer (DER eller Base64-kodad), eller. P7b (med eller utan fullständig kedja).

#### <a name="configure-teacher-pkcs12-certificate"></a>Konfigurera PKCS#12-certifikat för lärare

Konfigurera följande värden under **PKCS #12-certifikat för lärare**:

- **Format för namn på certifikatmottagare** –Intune lägger automatiskt till prefixet **ledare** till certifikatets unika namn för lärarcertifikat och **medlem** för elevcertifikat.
- **Certifikatutfärdare** – En utfärdare av företagscertifikat som körs på en Enterprise Edition av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. 
- **Namn på certifikatutfärdare** – Ange namnet på certifikatutfärdaren.
- **Certifikatmallens namn** – Ange namnet på en certifikatmall som har lagts till i en certifikatutfärdare. 
- **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
- **Certifikatets giltighetsperiod** – Ange hur lång tid som återstår innan certifikatet upphör att gälla.
Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.

När du har konfigurerat certifikaten klickar du på **OK**.

### <a name="configure-student-certificates"></a>Konfigurera elevcertifikat

1.    Välj **Elevcertifikat** på bladet **Utbildning**.
2.    Välj **1:1** på bladet **Elevcertifikat** i typlistan **Elevcertifikat**.

#### <a name="configure-student-root-certificate"></a>Konfigurera rotcertifikat för elev

Klicka på bläddringsknappen under **Rotcertifikat för elev** för att välja elevens rotcertifikat med tillägget .cer (DER eller Base64-kodad), eller. P7b (med eller utan fullständig kedja).

#### <a name="configure-student-pkcs12-certificate"></a>Konfigurera PKCS#12-certifikat för elev

Konfigurera följande värden under **PKCS #12-certifikat för elev**:

- **Format för namn på certifikatmottagare** –Intune lägger automatiskt till prefixet **ledare** till certifikatets unika namn för lärarcertifikat och **medlem** för elevcertifikat.
- **Certifikatutfärdare** – En utfärdare av företagscertifikat som körs på en Enterprise Edition av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. 
- **Namn på certifikatutfärdare** – Ange namnet på certifikatutfärdaren.
- **Certifikatmallens namn** – Ange namnet på en certifikatmall som har lagts till i en certifikatutfärdare. 
- **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
- **Certifikatets giltighetsperiod** – Ange hur lång tid som återstår innan certifikatet upphör att gälla.
Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.

När du har konfigurerat certifikaten klickar du på **OK**.

## <a name="finish-up"></a>Slutför

1.    Klicka på OK på bladet **Utbildning**.
2.    Välj **Skapa** på bladet **Skapa profil**.
    
Profilen skapas och visas på bladet med profillistan.

Tilldela profilen till elevenheter i de klassrumsgrupper som skapades när du synkroniserade skolinformationen med Azure AD (se [Så tilldelar du enhetsprofiler](/intune-azure/configure-devices/how-to-assign-device-profiles)).

## <a name="next-steps"></a>Nästa steg

När en lärare nu använder Klassrum-appen kommer hen att ha full kontroll över elevenheterna.

Mer information om Klassrum-appen finns i [Hjälp om Klassrum](https://help.apple.com/classroom/ipad/2.0/) på Apples webbplats.

