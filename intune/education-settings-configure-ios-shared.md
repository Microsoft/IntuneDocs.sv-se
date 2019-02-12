---
title: Intune-inställningar för delade enheter och iOS-appen Classroom
titleSuffix: Microsoft Intune
description: Läs om vilka Intune-inställningar du kan använda för att styra inställningarna för Classroom-appen på iOS-enheter.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 558f55d1d809fe634f7b48a91962644fe0d97232
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842889"
---
# <a name="configure-intune-education-settings-for-shared-ipad-devices"></a>Konfigurera Intune-utbildningsinställningar för delade iPad-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> Intune-inställningar för Classroom-appen är inaktuella i Intune. Den här artikeln gäller endast för användare med befintliga utbildningsprofiler i Intune.

Intune stöder iOS-appen Classroom. Det är en app som hjälper lärare att stödja utbildning och hantera elevenheter i klassrummet. Utöver appen Classroom stöder Apple möjligheten att konfigurera elevernas iPad-enheter så att flera elever kan dela på en enhet. Det här dokumentet hjälper dig att uppnå det här målet med Intune.

Information om hur du konfigurerar personliga (1:1) iPad-enheter för användning med appen Classroom finns i [Så här konfigurerar du inställningar för iOS-appen Klassrum för Intune](education-settings-configure-ios.md).

## <a name="before-you-start"></a>Innan du börjar

Följande är de förutsättningar som uppfyllas innan du kan använda funktionerna för delade iPad-enheter:

- Konfigurera [Apple School Manager](apple-school-manager-set-up-ios.md) och [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617).
- Som en del av konfigureringen av Apple School Manager konfigurerar du [hanterade Apple-ID:n](http://help.apple.com/schoolmanager/#/tes78b477c81) för eleverna. [Läs mer om hanterade Apple-ID:n](https://support.apple.com/HT205918).
- Skapa en registreringsprofil för enhetsserienumren som synkroniseras från Apple School Manager.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Steg 1 – Importera din skolinformation till Azure Active Directory

Använd Microsoft SDS (School Data Sync) för att importera skolinformation från ett befintligt elevinformationssystem (SIS) till Azure Active Directory (Azure AD).
SDS synkroniserar information från din SIS och lagrar den i Azure AD. Azure AD är ett Microsoft-hanteringssystem som hjälper dig att organisera användare och enheter. Du kan sedan använda dessa data för att hantera dina elever och klasser. [Läs mer om att distribuera SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Importera data med SDS

Du kan importera information till SDS på något av följande sätt:

- [CSV-filer](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) – Exportera manuellt och kompilera (.csv-) filer med kommaseparerade värden
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) – En SIS-provider som förenklar synkronisering med Azure AD
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
5. I profilfönstret väljer du **Skapa profil**.
6. Ange **Namn** och **Beskrivning** för iOS-utbildningsprofilen i fönstret **Skapa profil**.
7. Välj **iOS** i listrutan **Plattform**.
8. Välj **Utbildning** i listrutan **Profiltyp**.
9. Välj **Inställningar** > **Konfigurera**.

Du behöver sedan certifikat för att upprätta en förtroenderelation mellan lärarens och elevernas iPad-enheter. Certifikat används för att smidigt och tyst autentisera anslutningar mellan enheter utan att behöva ange användarnamn och lösenord.

>[!Important]
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
- **Certifikatets giltighetsperiod** – Ange hur lång tid som återstår innan certifikatet upphör att gälla. Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.

När du har konfigurerat lärarcertifikaten klickar du på **OK**.

### <a name="configure-student-certificates"></a>Konfigurera elevcertifikat

1. Välj **Elevcertifikat** i **fönstret Utbildning**.
2. Välj **Delad iPad** i fönstret **Elevcertifikat** i listan **Typ av elevcertifikat**.

#### <a name="configure-student-root-certificate"></a>Konfigurera rotcertifikat för elev

Klicka på bläddringsknappen under **Enhetens rotcertifikat** för att välja elevens rotcertifikat med tillägget .cer (DER eller Base64-kodad), eller. P7b (med eller utan fullständig kedja).

#### <a name="configure-device-pkcs12-certificate"></a>Konfigurera PKCS#12-certifikat för enhet

Konfigurera följande värden under **PKCS #12-certifikat för elev**:

- **Format för namn på certifikatmottagare** – Intune lägger automatiskt till prefixet ledare till certifikatets unika namn för lärarcertifikat och prefixet medlem för enhetscertifikat.
- **Certifikatutfärdare** – En utfärdare av företagscertifikat som körs på en Enterprise Edition av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte.
- **Namn på certifikatutfärdare** – Ange namnet på certifikatutfärdaren.
- **Certifikatmallens namn** – Ange namnet på en certifikatmall som har lagts till i en certifikatutfärdare.
- **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
- **Certifikatets giltighetsperiod** – Ange hur lång tid som återstår innan certifikatet upphör att gälla. Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.

När du har konfigurerat certifikaten klickar du på **OK**.

### <a name="complete-certificate-setup"></a>Slutför certifikatkonfigureringen

1. Klicka på **OK** i fönstret **Utbildning**.
2. Välj **Skapa** i fönstret **Skapa profil**.

Profilen skapas och visas i fönstret med profillistan.

## <a name="step-3---create-a-device-category"></a>Steg 3 – Skapa en enhetskategori

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enhetsregistrering** i fönstret **Intune**.
4. I fönstret **Enhetsregistrering – Översikt** väljer du **Enhetskategorier**.
5. Välj **Skapa** i fönstret **Enhetsregistrering – Enhetskategorier**.
6. Ange ett **Namn** och en **Beskrivning** av kategorin i fönstret **Skapa enhetskategori**.
7. Välj **Skapa** i fönstret **Skapa enhetskategori**.

Enhetskategorin skapas i fönstret **Registrering – Enhetskategorier**.

## <a name="step-4--create-a-dynamic-group"></a>Steg 4 – Skapa en dynamisk grupp

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Grupper**.
4. Välj **Ny grupp** i fönstret **Användare och grupper – Alla grupper**.
5. I fönstret **Grupp** väljer du en **Grupptyp** och anger sedan **Namn** och **Beskrivning** för gruppen.
6. Välj **Dynamisk enhet** i listrutan **Medlemskapstyp**.
7. Välj **Dynamiska enhetsmedlemmar** för att skapa regler för medlemskap.
8. Gör följande i fönstret **Regler för dynamiskt medlemskap**:
1. Välj **deviceCategory** i listrutan **Lägg till enheter där**.
2. Välj **Är lika med**.
3. Ange den enhetskategori som du skapade i den tomma textrutan.
9. Välj **Lägg till fråga** i fönstret **Regler för dynamiskt medlemskap**.
10. Välj **Skapa** i fönstret **Grupp**.

Den dynamiska gruppen skapas i fönstret **Användare och grupper – Alla grupper**.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>Steg 5 – Tilldela en enhet till en kategori (kundvagnar)

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enheter**.
4. I fönstret **Enheter** väljer du **Alla enheter**.
5. Välj en enhet i fönstret **Enheter – Alla enheter**.
6. I enhetsfönstret väljer du **Egenskaper**.
7. Ange enhetskategorin i textrutan **Enhetskategori** i enhetens egenskapsfönster.
8. Välj **Spara** i enhetsfönstret.

Enheten är nu associerad med enhetskategorin. Upprepa proceduren för alla enheter som du vill associera med den enhetskategori du skapade.

## <a name="step-6--create-classroom-profiles"></a>Steg 6 – Skapa klassrumsprofiler

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
4. Välj **Hantera** > **Kundvagnsprofiler** i fönstret **Enhetskonfiguration**.
5. I profilfönstret väljer du **Skapa profil**.
6. Ange ett **Namn** och en **Beskrivning** i fönstret **Skapa association**.
7. Välj **Välj klasser** > **Konfigurera** för att associera grupper med kundvagnsprofilen.
8. Välj de klasser du vill inkludera i kundvagnsprofilen och välj sedan **Välj**. 
9. Välj **Välj kundvagnar** > **Konfigurera** för att associera grupper med kundvagnsprofilen.
10. Välj de grupper du vill inkludera i kundvagnsprofilen och välj sedan **Välj**.
11. Välj **Spara** i fönstret **Skapa association** för att spara kundvagnsprofilen.

Profilen skapas och visas i fönstret med profillistan.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>Steg 7 – Tilldela kundvagnsprofilen till klasser

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du **Enhetskonfiguration**.
4. Välj **Övervaka** > **Tilldelningsstatus** i fönstret **Enhetskonfiguration**.
5. Välj den **Kundvagnsprofil** du skapade i fönstret **Tilldelningsstatus**.
6. Välj **Tilldelningar** i fönstret **Kundvagnsprofil** och välj **Välj grupper att ta med** under **Inkludera**.
7. Välj de klasser du vill ange som mål kundvagnsprofilen (välj inte en grupp) och välj sedan **Välj**. 
8. Välj **Spara** när du är klar.

Tilldelningen slutförs och Intune distribuerar klassrumsprofilen till målenheterna baserat på klassrumstilldelningen.

## <a name="next-steps"></a>Nästa steg

Eleverna kan nu dela enheter och en elev kan hämta valfri iPad i ett klassrum, logga in med en PIN-kod och på så sätt få en anpassad iPad-enhet med sitt innehåll. Mer information om delade iPad-enheter finns på [Apples webbplats](https://www.apple.com/education/it/).
