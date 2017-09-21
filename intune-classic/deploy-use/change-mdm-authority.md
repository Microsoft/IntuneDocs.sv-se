---
title: "Ändra MDM-utfärdare till Configuration Manager (hybrid-MDM)"
description: "Lär dig hur du ändrar MDM-utfärdaren från fristående Intune till Configuration Manager (hybrid-MDM)."
keywords: 
author: dougeby
manager: angrobe
ms.date: 05/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f1b4bce3-7932-4a0d-aa92-6dacc7060f42
ms.reviewer: 
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 816aa3effc8be66844000394f27eacc4215c1bc2
ms.sourcegitcommit: 94177ee8bc9f2fe448738773757e40d799f71c18
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="change-the-mdm-authority"></a>Ändra MDM-utfärdare
Från och med Configuration Manager version 1610 kan du ändra din MDM-utfärdare utan att behöva kontakta Microsoft Support, och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. Det här avsnittet beskriver hur du ändrar en befintlig Microsoft Intune-klient som konfigurerats i Intune med fristående **Microsoft Intune** som MDM-utfärdare till **Configuration Manager** (hybrid-MDM) utan att du behöver avregistrera och omregistrera befintliga hanterade enheter.

> [!Note]    
> Information om hur du ändrar en befintlig Microsoft Intune-klient som konfigurerats i Configuration Manager-konsolen (hybrid) med **Configuration Manager** (hybrid) som MDM-utfärdare till fristående **Microsoft Intune** finns i avsnittet om [hur du ändrar MDM-utfärdare från Configuration Manager (hybrid-MDM) till fristående Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority). 


### <a name="key-considerations"></a>Viktigt att tänka på
När du har bytt till den nya MDM-utfärdaren kan det ta upp till åtta timmar innan enheten ansluter till och synkroniserar med tjänsten. Du måste konfigurera inställningar i den nya MDM-utfärdaren (hybrid) så att registrerade enheter fortsätter att hanteras och skyddas efter ändringen. Tänk på följande:
- Enheter måste ansluta till tjänsten efter ändringen så att inställningarna från den nya MDM-utfärdaren (fristående Intune) ersätter de befintliga inställningarna på enheten.
- När du har ändrat MDM-utfärdaren finns några av de grundläggande inställningarna (t.ex. profiler) från den tidigare MDM-utfärdaren (fristående Intune) kvar på enheten i upp till sju dagar, eller tills enheten ansluter till tjänsten för första gången. Vi rekommenderar att du konfigurerar appar och inställningar (principer, profiler, appar osv.) i den nya MDM-utfärdaren (hybrid) så snart som möjligt och distribuerar inställningarna till användargrupperna som innehåller användare som har befintliga registrerade enheter. Så fort en enhet ansluter till tjänsten efter ändringen av MDM-utfärdare tar den emot de nya inställningarna från den nya MDM-utfärdaren, vilket förhindrar avbrott i hanteringen och skyddet av enheten.
- Enheter som inte har associerade användare (vanligt om du har iOS-programmet för enhetsregistrering eller vid massregistreringsscenarier) migreras inte till den nya MDM-utfärdaren. För dessa enheter måste du ringa supporten och få hjälp med att flytta dem till den nya MDM-utfärdaren.

### <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>Förbereda ändringen av MDM-utfärdare till Configuration Manager (hybrid)
Läs följande information som beskriver hur du förbereder övergången till MDM-utfärdaren:
- Du måste ha Configuration Manager version 1610 eller senare för att alternativet att byta MDM-utfärdare ska vara tillgängligt.
- Det kan ta upp till åtta timmar innan en enhet ansluter till tjänsten efter att du har bytt till den nya MDM-utfärdaren.
- Skapa en Configuration Manager-användarsamling med alla användare som för närvarande hanteras av fristående Intune, som du sedan ska använda när du konfigurerar Intune-prenumerationen i Configuration Manager-konsolen. Genom att göra det kan du vara säker på att användarna och deras enheter har en tilldelad Configuration Manager-licens och att de hanteras i hybridmiljön efter ändringen av MDM-utfärdaren.
- Se till att IT-administratörsanvändaren ingår i den här användarsamlingen.  
- Innan ändringen visas MDM-utfärdaren som **Ställ in på Microsoft Intune** (fristående) i Intune-administrationskonsolen.
- MDM-utfärdaren bör visas som **Ställ in på Microsoft Intune** (fristående klient) i Microsoft Intune-administrationskonsolen före ändringen av MDM-utfärdare.
    > [!NOTE]    
    > Om MDM-utfärdaren visas som **Hanteras av Intune och Office 365** kommer dina Office 365-hanterade MDM-enheter inte längre att hanteras när du ändrar MDM-utfärdaren till **Configuration Manager** (hybrid). Vi rekommenderar att du licensierar dessa användare för Intune eller Enterprise Mobility Suite innan du ändrar MDM-utfärdare.   

- Ta bort rollen Enhetsregistreringshanterare i [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com). Mer information finns i [Ta bort en enhetsregistreringshanterare från Intune](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune).
- Inaktivera alla konfigurerade enhetsgruppmappningar. Mer information finns i avsnittet [Kategorisera enheter med enhetsgruppmappning i Microsoft Intune](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).
- Slutanvändarna bör inte påverkas nämnvärt under övergången till den nya MDM-utfärdaren. Det kan dock vara bra att informera användarna om ändringen så att de har sina enheter påslagna och ansluter till tjänsten så snart som möjligt efter ändringen. På så sätt säkerställer du att så många enheter som möjligt ansluter till och registreras med tjänsten via den nya utfärdaren så fort som möjligt.
- Om du använder fristående Intune för att hantera iOS-enheter före ändringen av MDM-utfärdare måste du se till att samma APNs-certifikat (Apple Push Notification service) som användes tidigare i Intune förnyas och används för att konfigurera klienten igen i Configuration Manager (hybrid).    

    > [!IMPORTANT]  
    > Om ett annat APNs-certifikat används för hybridversionen avregistreras ALLA tidigare registrerade iOS-enheter och du måste registrera dem på nytt. Kontrollera exakt vilket APNs-certifikat som användes för att hantera iOS-enheter i Intune innan du ändrar MDM-utfärdaren. Leta upp samma certifikat på Apple Push Certificates-portalen (https://identity.apple.com) och kontrollera att den användare vars Apple-ID användes för att skapa det ursprungliga APNs-certifikatet identifieras och är tillgänglig, så att samma APNs-certifikat kan förnyas i samband med att den nya MDM-utfärdaren ändras.  

### <a name="change-the-mdm-authority-to-configuration-manager"></a>Ändra MDM-utfärdaren till Configuration Manager
När du ändrar MDM-utfärdaren till Configuration Manager (hybrid) följer du dessa generella steg:  
- Lägg till Microsoft Intune-prenumerationen i Configuration Manager-konsolen.
- Konfigurera Apple APNs-certifikatet genom att använda samma APNs-certifikat som du förnyade.
- Konfigurera och distribuera nya inställningar och appar från den nya MDM-utfärdaren (hybrid) i Configuration Manager-konsolen.
- Nästa gång enheterna ansluter till tjänsten synkroniseras de och tar emot de nya inställningarna från den nya MDM-utfärdaren.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>Så här ändrar du MDM-utfärdaren till Configuration Manager
1. Gå till **Administration** &gt; **Översikt** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumeration** i Configuration Manager-konsolen och välj att lägga till en Intune-prenumeration.
2. Logga in till den Intune-klient som du ursprungligen använde när du konfigurerade MDM-utfärdaren i Intune och klicka på **Nästa**.
3. Välj **Ändra utfärdare för hantering av mobila enheter till Configuration Manager** och klicka på **Nästa**.
4. Välj användarsamlingen med alla användare som ska hanteras av den nya hybrid-MDM-utfärdaren.
5. Klicka på **Nästa** och slutför guiden. Nu ändras MDM-utfärdaren till **Configuration Manager**.
6. Logga in i [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) med samma Intune-klient och bekräfta att MDM-utfärdaren har ändrats till **Ställ in Konfigurationshanteraren**.


### <a name="enable-ios-enrollment"></a>Aktivera iOS-registrering
Om du har iOS-enheter måste du konfigurera APNs-certifikatet i Configuration Manager.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>Så här aktiverar du iOS-registrering och konfigurerar APNs-certifikatet

1. **Ladda ned en certifikatsigneringsförfrågan**

    1. Gå till **Administration** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumerationer** i Configuration Manager-konsolen och välj **Skapa APNs-certifikatförfrågan** för att öppna dialogrutan **Certifikatsigneringsförfrågan för Apple Push-aviseringstjänst**.  
    2. **Bläddra** till sökvägen för att spara den nya filen för certifikatsigneringsförfrågan (.csr). Spara begäran om certifikatsignering (.csr) lokalt.  
    3. Klicka på **Ladda ned**. Den nya CSR-filen för Microsoft Intune hämtas och sparas av Configuration Manager.   

    > [!IMPORTANT]
    > Du måste ladda ned en ny certifikatsigneringsförfrågan. Du kan inte använda en befintlig fil.  

2.  Gå till [Apple Push Certificates-portalen](http://go.microsoft.com/fwlink/?LinkId=269844) och logga in med **samma** Apple-ID som användes tidigare för att skapa och förnya det APNs-certifikat som du använde i fristående Intune.

    ![Inloggningssida för Apple Push Certificates-portalen](../media/mdm-change-apns-portal.png)

3. Välj det APNs-certifikat som du använde i fristående Intune och klicka sedan på **Förnya**.

    ![Dialogrutan för att förnya APNs](../media/mdm-change-renew-apns.png)

4. Välj filen för APNs-certifikatsigneringsförfrågan (.csr) som du laddade ned lokalt och klicka sedan på **Ladda upp**.

    ![Inloggningssida för Apple Push Certificates-portalen](../media/mdm-change-renew-apns-upload.png)
 
5. Välj samma APNs och klicka på **Ladda ned**. Hämta APN-certifikatet (.pem) och spara filen lokalt.  

    ![Inloggningssida för Apple Push Certificates-portalen](../media/mdm-change-renew-apns-download.png)

6. Använd samma Apple-ID som förut och ladda upp det förnyade APNs-certifikatet till hybridklienten.

    1.  Gå till **Administration** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumeration** i Configuration Manager-konsolen och välj **Konfigurera plattformar** &gt; **iOS**.  
    2.  Välj fliken **APNs-certifikat** i dialogrutan **Egenskaper för Microsoft Intune-prenumeration** och markera kryssrutan **Aktivera iOS- och Mac OS X (MDM)-registrering**.  
    3.  Klicka på **Bläddra**och gå till APNs-certifikatfilen (.cer) som laddats ned från Apple. Configuration Manager visar APNs-certifikatinformationen. Klicka på **OK** för att spara APNs-certifikatet till Intune.  

        ![Egenskapssida för Intune-prenumeration – iOS](../media/mdm-change-subscription-properties-ios.png)

### <a name="enable-android-enrollment"></a>Aktivera Android-registrering
1. Gå till **Administration** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumeration** i Configuration Manager-konsolen och välj **Konfigurera plattformar** &gt; **Android**.  
2. Välj **Aktivera Android-registrering** och klicka på **OK**.

### <a name="enable-windows-enrollment"></a>Aktivera Windows-registrering
1. Gå till **Administration** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumeration** i Configuration Manager-konsolen och välj **Konfigurera plattformar** &gt; **Windows**.  
2. Välj **Aktivera Windows-registrering** och klicka på **OK**.

### <a name="enable-windows-phone-enrollment"></a>Aktivera Windows Phone-registrering
1. Gå till **Administration** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumeration** i Configuration Manager-konsolen och välj **Konfigurera plattformar** &gt; **Windows Phone**.  
2. Välj den plattform som du vill aktivera och klicka på **OK**.


### <a name="next-steps"></a>Nästa steg
Gå igenom följande steg när ändringen av MDM-utfärdaren har slutförts:
- När Intune-tjänsten upptäcker ett en klients MDM-utfärdare har ändrats skickar den ett aviseringsmeddelande till alla registrerade enheter som uppmanar dem att ansluta till och synkronisera med tjänsten (detta sker utanför den normala schemalagda anslutningen och kontrollen). När MDM-utfärdaren för klienten har ändrats från fristående Intune till hybridversionen kommer därför alla enheter som är påslagna och online att ansluta till tjänsten, ta emot inställningarna från den nya MDM-utfärdaren och börja hanteras av hybridversionen. Det sker inget avbrott i hanteringen och skyddet av dessa enheter.
- Även för enheter som är påslagna och online under (eller strax efter) ändringen av MDM-utfärdaren uppstår det en fördröjning på upp till åtta timmar (beroende på tidpunkten för nästa normala schemalagda anslutning och kontroll) innan enheterna registreras med tjänsten med den nya MDM-utfärdaren.    

  > [!IMPORTANT]    
  > Under perioden från det att du ändrar MDM-utfärdaren tills det förnyade APNs-certifikatet laddas upp till den nya utfärdaren kommer nya enhetsregistreringar och enhetskontroller på iOS-enheter att misslyckas. Därför är det viktigt att du granskar och laddar upp APNs-certifikatet till den nya utfärdaren så snart som möjligt efter ändringen av MDM-utfärdare.

- Användarna kan snabbt gå över till den nya MDM-utfärdaren genom att manuellt starta en kontroll från enheten till tjänsten. Användarna kan enkelt göra det genom att initiera en enhetskompatibilitetskontroll från företagsportalappen.
- Du kan kontrollera att allt fungerar korrekt när enheterna har anslutit till och synkroniserat med tjänsten efter ändringen av MDM-utfärdaren genom att granska enheterna i Configuration Manager-konsolen. Enheterna som tidigare hanterades av Intune visas nu som hanterade enheter i Configuration Manager-konsolen.    
- Det uppstår en övergångsperiod om en enhet är frånkopplad under ändringen av MDM-utfärdaren tills dess enheten ansluter till tjänsten. För att säkerställa att enheten fortfarande är skyddad och fungerar under den här övergångsperioden finns följande kvar på enheten i upp till sju dagar (eller tills enheten ansluter till den nya MDM-utfärdaren och tar emot nya inställningar som skriver över de befintliga):
    - E-postprofil
    - VPN-profil
    - Certifikatprofil
    - Wi-Fi-profil
    - Konfigurationsprofiler
- När du har bytt till den nya MDM-utfärdaren kan det ta upp till en vecka innan kompatibilitetsinformationen i Microsoft Intune-administrationskonsolen visar korrekta data. Kompatibilitetsstatusen i Azure Active Directory och på enheten är dock korrekt, så enheten är fortfarande skyddad.
- Kontrollera att de nya inställningarna som ska skriva över befintliga inställningar har samma namn som de tidigare inställningarna för att säkerställa att de gamla inställningarna skrivs över. Annars är risken att de gamla profilerna och principerna ligger kvar på enheterna.    

  > [!TIP]    
  > Vi rekommenderar att du skapar alla hanteringsinställningar och konfigurationer, samt även distributionerna, så snart som möjligt efter ändringen av MDM-utfärdaren. På så sätt kan du vara säker på att enheterna skyddas och hanteras aktivt under övergångsperioden.

-  Bekräfta att de nya enheterna registreras korrekt med den nya utfärdaren genom att utföra följande steg när du har ändrat MDM-utfärdaren:   
    - Registrera en ny enhet.
    - Kontrollera att den registrerade enheten visas i Configuration Manager-konsolen.
    - Utför en åtgärd på enheten, t.ex. fjärrlåsning, från administrationskonsolen. Om åtgärden lyckas betyder det att enheten hanteras av den nya MDM-utfärdaren.
- Om du har problem med specifika enheter kan du avregistrera och registrera om enheterna så att de börjar använda den nya utfärdaren och hanteras så snart som möjligt.