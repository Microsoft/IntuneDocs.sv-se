---
title: "Intune-inställningar för iOS Klassrum-appen"
titlesuffix: Azure portal
description: "Läs om vilka Intune-inställningar du kan använda för att kontrollera inställningarna för klassrum-appen på iOS-enheter.”"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d9b2e6df6c40ec142554db22a64d362e02884c1d
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>Så här konfigurerar du inställningar för iOS-appen Klassrum för Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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
- Kontrollera att du har installerat appen [Apple Klassrum](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) på lärarens enhet. Du kan antingen installera appen manuellt eller använda [Intune-apphantering](app-management.md).
- Du måste konfigurera certifikat för att autentisera anslutningar mellan lärarens och elevernas enheter (se steg 2)
- Lärarens och elevernas iPad-enheter måste finnas i samma Wi-Fi-nätverk och även ha Bluetooth aktiverat
- Appen Klassrum appen körs på övervakade iPad-enheter som kör iOS 9.3 eller senare
- I den här versionen stöder Intune hantering av ett 1:1-scenario, där varje elev har sin egen iPad


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Steg 1 – Importera din skolinformation till Azure Active Directory

Använd Microsoft SDS (School Data Sync) för att importera skolinformation från ett befintligt elevinformationssystem (SIS) till Azure Active Directory (Azure AD).
SDS synkroniserar information från din SIS och lagrar den i Azure AD. Azure AD är ett Microsoft-hanteringssystem som hjälper dig att organisera användare och enheter. Du kan sedan använda dessa data för att hantera dina elever och klasser. [Läs mer om att distribuera SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Importera data med SDS

Du kan importera information till SDS på något av följande sätt:

- [CSV-filer](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) – Exportera manuellt och kompilera (.csv-) filer med kommaseparerade värden
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) – En SIS-provider som förenklar synkronisering med Azure AD
- [Clever API](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) – En lösning för identitetshantering som synkroniserar direkt med Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) – Ett CSV-format som du kan exportera och konvertera för synkronisering med Azure AD

### <a name="find-out-more"></a>Läs mer

- [Läs mer om hur du kan synkronisera lokal skolinformation till Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Läs mer om Microsofts synkronisering av skolinformation](https://sds.microsoft.com/)
- [Läs mer om licensiering i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Steg 2 – Skapa och tilldela en iOS-utbildningsprofil i Intune

### <a name="configure-general-settings"></a>Konfigurera allmänna inställningar

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
2. I fönstret **Enhetskonfiguration** under avsnittet **Hantera** väljer du **Profiler**.
5.  I profilfönstret väljer du **Skapa profil**.
6.  Ange **Namn** och **Beskrivning** för iOS-utbildningsprofilen i fönstret **Skapa profil**.
7.  Välj **iOS** i listrutan **Plattform**.
8.  Välj **Utbildning** i listrutan **Profiltyp**.
9.  Välj **Inställningar** > **Konfigurera**.


Du behöver sedan certifikat för att upprätta en förtroenderelation mellan lärarens och elevernas iPad-enheter. Certifikat används för att smidigt och tyst autentisera anslutningar mellan enheter utan att behöva ange användarnamn och lösenord.

>[!IMPORTANT]
>De lärar- och elevcertifikat som du använder måste utfärdas av olika certifikatutfärdare (CA). Du måste skapa två nya underordnade certifikatutfärdare som är anslutna till din befintliga infrastruktur för certifikat; en för lärare och en för elever.

Profiler för iOS-utbildning stöder endast PFX-certifikat. SCEP-certifikat stöds inte.

Certifikat som du skapar måste ha stöd för serverautentisering förutom användarautentisering.

### <a name="configure-teacher-certificates"></a>Konfigurera lärarcertifikat

Välj **Lärarcertifikat** i fönstret **Utbildning**.

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

1.  Välj **Elevcertifikat** i fönstret **Utbildning**.
2.  Välj **1:1** i fönstret **Elevcertifikat** i typlistan för **Elevcertifikat**.

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

1.  Välj OK i fönstret **Utbildning**.
2.  Välj **Skapa** i fönstret **Skapa profil**.
    
Profilen skapas och visas i fönstret med profillistan.

Tilldela profilen till elevenheter i de klassrumsgrupper som skapades när du synkroniserade skolinformationen med Azure AD (se [Så här tilldelar du enhetsprofiler](device-profile-assign.md)).

## <a name="next-steps"></a>Nästa steg

När en lärare nu använder Klassrum-appen kommer hen att ha full kontroll över elevenheterna.

Mer information om Klassrum-appen finns i [Hjälp om Klassrum](https://help.apple.com/classroom/ipad/2.0/) på Apples webbplats.

Om du vill konfigurera delade iPad-enheter för elever läser du [How to configure Intune education settings for shared iPad devices](education-settings-configure-ios-shared.md) (konfigurera Intune-utbildningsinställningar för delade iPad-enheter).
