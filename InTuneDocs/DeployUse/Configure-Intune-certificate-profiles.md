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
ms.sourcegitcommit: 8e3f7cac8eb3495aad3835ec4713d67a58383c66
ms.openlocfilehash: 8b08f8fde6136b8eca61f6ae7a8c21635f7d452e


---

# Konfigurera certifikatprofiler för Intune
När du har konfigurerat infrastrukturen och certifikaten enligt beskrivningen i [Konfigurera certifikatinfrastruktur för SCEP](configure-certificate-infrastructure-for-scep.md) eller [Konfigurera certifikatinfrastrukturen för PFX](configure-certificate-infrastructure-for-pfx.md) kan du skapa certifikatprofiler. Så här ser processen ut:

- **Uppgift 1**: Exportera certifikatet för betrodd rotcertifikatutfärdare
- **Uppgift 2**: Skapa certifikatprofiler för betrodda certifikatutfärdare
- **Uppgift 3**: Skapa en av dessa typer av certifikatprofiler:
  - SCEP-certifikatprofiler
  - .PFX-certifikatprofiler

## **Uppgift 1**: Exportera certifikatet för betrodd rotcertifikatutfärdare
Exportera certifikatet för betrodda rotcertifikatutfärdare som en **CER**-fil från den utfärdande certifikatutfärdaren eller från en enhet som litar på den utfärdande certifikatutfärdaren. Exportera inte den privata nyckeln.

Det här certifikatet importeras när du konfigurerar en certifikatprofil för en betrodd certifikatutfärdare.

## **Uppgift 2**: Skapa certifikatprofiler för betrodda certifikatutfärdare
Du måste skapa en certifikatprofil för en betrodd certifikatutfärdare innan du kan skapa en SCEP-certifikatprofil (Simple Certificate Enrollment Protocol) eller en PKSC #12-certifikatprofil (.PFX). Du behöver en betrodd certifikatprofil och en SCEP- eller .PFX-profil för varje mobil enhetsplattform.

### Så här skapar du en betrodd certifikatprofil

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Lägg till princip**.
2.  Lägg till en av dessa principtyper:
    - **Android &gt; Betrodd certifikatprofil (Android 4 och senare)**
    - **iOS &gt; Betrodd certifikatprofil (iOS 7.1 och senare)**
    - **Mac OS X &gt; Betrodd certifikatprofil (Mac OS X 10.9 och senare)**
    - **Windows &gt; Betrodd certifikatprofil (Windows 8.1 och senare)**
    - **Windows &gt; Betrodd certifikatprofil (Windows Phone 8.1 och senare)**

    Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Ange den information som efterfrågas för att konfigurera inställningar för betrodda certifikatprofiler för Android, iOS, Mac OS X, Windows 8.1 eller Windows Phone 8.1.

    - I inställningen **Certifikatfil** importerar du certifikatet för betrodd rotcertifikatutfärdare (CER-fil) som du exporterade från den utfärdande certifikatutfärdaren. Inställningen **Målarkiv** gäller endast för enheter som kör Windows 8.1 och senare, och endast om enheten har flera certifikatarkiv.
    -  Välj **Anpassad** under **Format för namn på certifikatmottagare** om du vill ange ett eget format för namn på certifikatmottagare.  
        De två variabler som stöds för närvarande för det anpassade formatet är `Common Name (CN)` och `Email (E)`. Genom att kombinera dessa variabler och statiska strängar kan du skapa ett eget format för namn på certifikatmottagare. Exempel:  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        I det här exemplet har administratören skapat ett format som utöver variablerna `CN` och `E` använder strängar för värdena organisationsenhet, organisation, plats, delstat och land. [Funktionen CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) visar en lista över strängar som stöds.  
4.  Välj **Spara princip**.

Den nya principen visas på arbetsytan **Princip**. Nu kan du distribuera den.

## **Uppgift 3**: Skapa SCEP- eller .PFX-certifikatprofiler
När du har skapat en certifikatprofil för betrodd certifikatutfärdare skapar du SCEP- eller .PFX-certifikatprofiler för varje plattform som du vill använda. När du skapar en SCEP-certifikatprofil måste du ange en betrodd certifikatprofil för samma plattform. Detta länkar de två certifikatprofilerna, men du måste fortfarande distribuera varje profil separat.

### Så här skapar du en SCEP-certifikatprofil

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Lägg till princip**.
2.  Lägg till en av dessa principtyper:
    - **Android &gt; SCEP-certifikatprofil (Android 4 och senare)**
    - **iOS &gt; SCEP-certifikatprofil (iOS 7.1 och senare)**
    - **Mac OS X &gt; SCEP-certifikatprofil (Mac OS X 10.9 och senare)**
    - **Windows &gt; SCEP-certifikatprofil (Windows 8.1 och senare)**
    - **Windows &gt; SCEP-certifikatprofil (Windows Phone 8.1 och senare)**

    Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Följ anvisningarna på profilsidan för att konfigurera inställningarna för SCEP-certifikatet.
    > [!NOTE]
    >
    > Välj **Anpassad** under **Format för namn på certifikatmottagare** om du vill ange ett eget format för namn på certifikatmottagare.
    >
    > De två variabler som stöds för närvarande för det anpassade formatet är `Common Name (CN)` och `Email (E)`. Genom att kombinera dessa variabler och statiska strängar kan du skapa ett eget format för namn på certifikatmottagare. Exempel:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > I det här exemplet har administratören skapat ett format som utöver variablerna `CN` och `E` använder strängar för värdena organisationsenhet, organisation, plats, delstat och land. [Funktionen CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) visar en lista över strängar som stöds.

4.  Välj **Spara princip**.

Den nya principen visas på arbetsytan **Princip**. Nu kan du distribuera den.

### Så här skapar du en .PFX-certifikatprofil

1.  I [Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Lägg till princip**.
2.  Lägg till en av dessa principtyper:
  - **Android &gt; .PFX-certifikatprofil (Android 4 och senare)**
  - **Windows &gt; PKCS #12-certifikatprofil (.PFX) (Windows 10 och senare)**
  - **Windows &gt; PKCS #12-certifikatprofil (.PFX) (Windows Phone 10 och senare)**
  - **iOS > PKCS #12 (.PFX)-certifikatprofil (iOS 7.1 och senare)**    
    Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Ange den information som efterfrågas i principformuläret.
4.  Välj **Spara princip**.

Den nya principen visas på arbetsytan **Princip**. Nu kan du distribuera den.

## Distribuera certifikatprofiler
När du distribuerar certifikatprofiler installeras certifikatfilen från certifikatprofilen för betrodd certifikatutfärdare på enheten. Enheten använder SCEP- eller .PFX-certifikatprofilen för att skapa en certifikatbegäran.

Certifikatprofiler installeras endast på enheter som kör den plattform som du använder när du skapar profilen.

-   Du kan distribuera certifikatprofiler till användarsamlingar eller enhetssamlingar.

    > [!TIP]
    > Om du vill publicera certifikat till enheter snabbt efter att enheten registrerats, distribuerar du certifikatprofilen till en användargrupp i stället för en enhetsgrupp. Om du distribuerar till en enhetsgrupp krävs en fullständig enhetsregistrering innan enheten tar emot principer.

-   Även om du distribuerar varje profil separat måste du också distribuera betrodd rotcertifikatutfärdare och SCEP- eller .PFX-profilen. Annars misslyckas SCEP- eller .PFX-certifikatprincipen.

Distribuera certifikatprofiler på samma sätt som du distribuerar andra principer för Intune:

1.  På arbetsytan **Princip** markerar du den princip som du vill distribuera och väljer sedan **Hantera distribution**.
2.  I dialogrutan **Hantera distribution** :
    -   **Om du vill distribuera principen** väljer du en eller flera grupper som du vill distribuera principen till. Välj sedan **Lägg till** &gt; **OK**.
    -   **Om du vill stänga dialogrutan utan att distribuera den** väljer du **Avbryt**.

När du väljer en distribuerad princip visas mer information om distributionen i den nedre delen av principlistan.

### Nästa steg

Nästa steg är att läsa om hur du skyddar e-post-, Wi-Fi- och VPN-profiler med certifikat.

-  [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Wi-Fi-anslutningar i Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [VPN-anslutningar i Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Aug16_HO5-->


