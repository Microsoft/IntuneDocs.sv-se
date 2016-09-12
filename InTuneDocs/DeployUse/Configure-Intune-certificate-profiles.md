---
title: Konfigurera certifikatprofiler | Microsoft Intune
description: "Läs om hur du skapar en certifikatprofil för Intune."
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6a7f2eeb0114f525890d1dcb61344d60a19943d1
ms.openlocfilehash: 14419092edc77b2229cf980a74e81048941a2c28


---

# Konfigurera certifikatprofiler för Intune
När infrastrukturen och certifikaten har konfigurerats enligt beskrivningen i [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md) eller [Konfigurera certifikatinfrastrukturen för PFX](configure-certificate-infrastructure-for-pfx.md) kan du konfigurera certifikatprofiler:

**Uppgift 1** – Exportera certifikatet från betrodd rotcertifikatutfärdare **Uppgift 2** – Skapa certifikatprofiler för betrodda certifikatutfärdare **Uppgift 3** – Antingen:

Skapa SCEP-certifikatprofiler, eller

Skapa .PFX-certifikatprofiler

### Uppgift 1 – Exportera certifikatet för betrodd rotcertifikatutfärdare
Exportera certifikatet som en **CER** -fil från den utfärdande certifikatutfärdaren eller från en enhet som litar på den utfärdande certifikatutfärdaren. Exportera inte den privata nyckeln.

Det här certifikatet importeras när du konfigurerar en certifikatprofil för en betrodd certifikatutfärdare.

### Uppgift 2 – Skapa certifikatprofiler för betrodda certifikatutfärdare
Du måste skapa en **betrodd certifikatprofil** innan du kan skapa en SCEP- eller .PFX-certifikatprofil. Du behöver en betrodd certifikatprofil och en SCEP- eller .PFS-profil för varje mobil enhetsplattform.

##### Så här skapar du en betrodd certifikatprofil

1.  Öppna [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och klicka på **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande principer:

    **Android &gt; Betrodd certifikatprofil (Android 4 och senare)**

    **iOS &gt; Betrodd certifikatprofil (iOS 7.1 och senare)**

    **Mac OS X &gt; Betrodd certifikatprofil (Mac OS X 10.9 och senare)**

    **Windows &gt; Betrodd certifikatprofil (Windows 8.1 och senare)**

    **Windows &gt; Betrodd certifikatprofil (Windows Phone 8.1 och senare)**

    Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Ange den information som efterfrågas för att konfigurera inställningar för betrodda certifikatprofiler för Android, iOS, Mac OS X, Windows 8.1 eller Windows Phone 8.1. 

    - I inställningen **Certifikatfil** importerar du certifikatet för betrodd rotcertifikatutfärdare (**.cer**) som du exporterade från den utfärdande certifikatutfärdaren. Inställningen **Målarkiv** gäller endast för enheter som kör Windows 8.1 och senare, och endast om enheten har flera certifikatarkiv.

    
    - Välj **Anpassad** under **Format för namn på certifikatmottagare** om du vill ange ett eget format för namn på certifikatmottagare.  

        De två variabler som stöds för närvarande för det anpassade formatet är **Nätverksnamn (cn)** och **E-post (e)**. Genom att kombinera dessa variabler och statiska strängar kan du skapa ett eget format för namn på certifikatmottagare. Exempel:  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        I det här exemplet har administratören skapat ett format som utöver variablerna cn och e använder strängar för organisationsenhet, organisation, plats, delstat och land. En lista med strängar som stöds finns i avsnittet om [funktionen CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx).  


4.  När du är klar klickar du på **Spara profilen**.

Den nya principen visas i arbetsytan **Princip** och kan nu distribueras.

### Uppgift 3 – skapa SCEP- eller .PFX-certifikatprofiler
När du har skapat en certifikatprofil för betrodd certifikatutfärdare skapar du SCEP- eller .PFX-certifikatprofiler för varje plattform som du vill använda. När du skapar en SCEP-certifikatprofil måste du ange en betrodd certifikatprofil för samma plattform. Detta länkar de två certifikatprofilerna, men du måste fortfarande distribuera varje profil separat.

##### Så här skapar du en SCEP-certifikatprofil

1.  Öppna [Intune-administratörskonsolen](https://manage.microsoft.com) och välj **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande principer:

    **Android &gt; SCEP-certifikatprofil (Android 4 och senare)**

    **iOS &gt; SCEP-certifikatprofil (iOS 7.1 och senare)**

    **Mac OS X &gt; SCEP-certifikatprofil (Mac OS X 10.9 och senare)**

    **Windows &gt; SCEP-certifikatprofil (Windows 8.1 och senare)**

    **Windows &gt; SCEP-certifikatprofil (Windows Phone 8.1 och senare)**

    Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Följ anvisningarna på profilsidan för att konfigurera inställningarna för SCEP-certifikatet.
    > [!NOTE]
    > 
    > Välj **Anpassad** under **Format för namn på certifikatmottagare** om du vill ange ett eget format för namn på certifikatmottagare.
    > 
    >  De två variabler som stöds för närvarande för det anpassade formatet är Nätverksnamn (cn) och E-post (e). Genom att kombinera dessa variabler och statiska strängar kan du skapa ett eget format för namn på certifikatmottagare. Exempel:
    
    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US
    
    >    I det här exemplet har administratören skapat ett format som utöver variablerna *cn* och *e* använder strängar för organisationsenhet, organisation, plats, delstat och land. En lista med strängar som stöds finns i avsnittet om [funktionen CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx).

4.  När du är klar klickar du på **Spara profilen**.

Den nya principen visas i arbetsytan **Princip** och kan nu distribueras.

##### Så här skapar du en .PFX-certifikatprofil

1.  Öppna [Intune-administratörskonsolen](https://manage.microsoft.com) och välj **Princip** &gt; **Lägg till princip**.

2.  Konfigurera en av följande principer:



-   **Android &gt; .PFX-certifikatprofil (Android 4 och senare)**

    -   **Windows &gt; PKCS #12 (.PFX)--certifikatprofil (Windows 10 och senare)**

    -   **Windows &gt; PKCS #12 (.PFX)--certifikatprofil (Windows Phone 10 och senare)**

    -    **iOS > PKCS #12 (.PFX)-certifikatprofil (iOS 7.1 och senare)**    

    Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Ange den information som efterfrågas i principformuläret.

4.  När du är klar klickar du på **Spara profilen**.

Den nya principen visas i arbetsytan **Princip** och kan nu distribueras.

## Distribuera certifikatprofiler
När du distribuerar certifikatprofiler, installeras certifikatfilen från certifikatprofilen för den betrodda certifikatutfärdaren på enheter och SCEP- eller .PFX-certifikatprofilen används av enheten för att skapa en certifikatbegäran.

Certifikatprofiler installeras endast på tillämpliga enheter utifrån vilken plattform som används när profilen skapas.

-   Du kan distribuera certifikatprofiler till användarsamlingar eller enhetssamlingar.

    > [!TIP]
    > Om du vill tillåta att certifikat publiceras till enheter snabbt efter att enheten registrerats, distribuera profilcertifikatet till en användargrupp (inte en enhetsgrupp). Om du distribuerar till en enhetsgrupp måste en fullständig enhetsregistrering utföras innan enheten tar emot principer.

-   Även om varje profil distribueras separat, måste både den betrodda rotcertifikatprofilen och SCEP/.PFX-profilen distribueras. Annars misslyckas SCEP/.PFX-certifikatpolicyn.

Du distribuerar certifikatprofiler på samma sätt som du distribuerar andra principer för Intune:

1.  Välj den princip på arbetsytan **Princip** som du vill distribuera och klicka sedan på **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   **Om du vill distribuera principen** markerar du en eller flera grupper som du vill distribuera principen till och klickar sedan på **Lägg till** &gt; **OK**.

    -   **Om du vill stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**.

När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.
###  Nästa steg

Du kan nu använda certifikat för att skydda e-post-, Wi-Fi- och VPN-profiler:

-  [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Wi-Fi-anslutningar i Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


