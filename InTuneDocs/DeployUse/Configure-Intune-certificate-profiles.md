---
# required metadata

title: Konfigurera certifikatprofiler | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurera certifikatprofiler för Intune
När infrastrukturen och certifikaten har konfigurerats enligt beskrivningen i [Konfigurera infrastrukturen för certifikat](configure-certificate-infrastructure.md) kan du konfigurera certifikatprofiler:

**Uppgift 1** – Exportera certifikatet för betrodd rotcertifikatutfärdare

**Uppgift 2** – Skapa certifikatprofiler för betrodda certifikatutfärdare

**Uppgift 3** – Antingen:

### Skapa SCEP-certifikatprofiler, eller
Skapa .PFX-certifikatprofiler Uppgift 1 – Exportera certifikatet för betrodd rotcertifikatutfärdare

Exportera certifikatet som en **CER** -fil från den utfärdande certifikatutfärdaren eller från en enhet som litar på den utfärdande certifikatutfärdaren.

### Exportera inte den privata nyckeln.
Det här certifikatet importeras när du konfigurerar en certifikatprofil för en betrodd certifikatutfärdare. Uppgift 2 – Skapa certifikatprofiler för betrodda certifikatutfärdare

##### Du måste skapa en **betrodd certifikatprofil** innan du kan skapa en SCEP- eller .PFX-certifikatprofil.

1.  Du behöver en betrodd certifikatprofil och en SCEP- eller .PFS-profil för varje mobil enhetsplattform.

2.  Så här skapar du en betrodd certifikatprofil

    **Öppna [Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Princip** &gt; **Lägg till princip****

    **Konfigurera en av följande principer:**

    **Android &gt; Betrodd certifikatprofil (Android 4 och senare)**

    **iOS &gt; Betrodd certifikatprofil (iOS 7.1 och senare)**

    **Mac OS X &gt; Betrodd certifikatprofil (Mac OS X 10.9 och senare)**

    Windows &gt; Betrodd certifikatprofil (Windows 8.1 och senare)

3.  Windows &gt; Betrodd certifikatprofil (Windows Phone 8.1 och senare) Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) Ange den information som efterfrågas för att konfigurera inställningar för betrodda certifikatprofiler för Android, iOS, Mac OS X, Windows 8.1 eller Windows Phone 8.1.


4.  I inställningen **Certifikatfil** importerar du certifikatet för betrodd rotcertifikatutfärdare (**.cer**) som du exporterade från den utfärdande certifikatutfärdaren.

Inställningen **Målarkiv** gäller endast för enheter som kör Windows 8.1 och senare, och endast om enheten har flera certifikatarkiv.

### När du är klar klickar du på **Spara princip**
Den nya principen visas i arbetsytan **Princip** och kan nu distribueras. Uppgift 3 – skapa SCEP- eller .PFX-certifikatprofiler När du har skapat en certifikatprofil för betrodd certifikatutfärdare skapar du SCEP- eller .PFX-certifikatprofiler för varje plattform som du vill använda.

##### När du skapar en SCEP-certifikatprofil måste du ange en betrodd certifikatprofil för samma plattform.

1.  Detta länkar de två certifikatprofilerna, men du måste fortfarande distribuera varje profil separat.

2.  Så här skapar du en SCEP-certifikatprofil

    **Öppna [Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Princip** &gt; **Lägg till princip****

    **Konfigurera en av följande principer:**

    **Android &gt; SCEP-certifikatprofil (Android 4 och senare)**

    **iOS &gt; SCEP-certifikatprofil (iOS 7.1 och senare)**

    **Mac OS X &gt; SCEP-certifikatprofil (Mac OS X 10.9 och senare)**

    Windows &gt; SCEP-certifikatprofil (Windows 8.1 och senare)

3.  Windows &gt; SCEP-certifikatprofil (Windows Phone 8.1 och senare)

4.  Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

Följ anvisningarna på profilsidan för att konfigurera inställningarna för SCEP-certifikatet.

##### När du är klar klickar du på **Spara princip**

1.  Den nya principen visas i arbetsytan **Princip** och kan nu distribueras.

2.  Så här skapar du en .PFX-certifikatprofil



-   **Öppna [Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Princip** &gt; **Lägg till princip****

    -   **Konfigurera en av följande principer:**

    -   **Android &gt; .PFX-certifikatprofil (Android 4 och senare)**

    -    **Windows &gt; PKCS #12 (.PFX)--certifikatprofil (Windows 10 och senare)**    

    Windows &gt; PKCS #12 (.PFX)--certifikatprofil (Windows Phone 10 och senare)

3.  iOS > PKCS #12 (.PFX)-certifikatprofil (iOS 7.1 och senare)

4.  Läs mer: [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

Ange den information som efterfrågas i principformuläret.

## När du är klar klickar du på **Spara princip**
Den nya principen visas i arbetsytan **Princip** och kan nu distribueras.

Distribuera certifikatprofiler

-   När du distribuerar certifikatprofiler, installeras certifikatfilen från certifikatprofilen för den betrodda certifikatutfärdaren på enheter och SCEP- eller .PFX-certifikatprofilen används av enheten för att skapa en certifikatbegäran.

    > [!TIP]
    > Certifikatprofiler installeras endast på tillämpliga enheter utifrån vilken plattform som används när profilen skapas. Du kan distribuera certifikatprofiler till användarsamlingar eller enhetssamlingar.

-   Om du vill tillåta att certifikat publiceras till enheter snabbt efter att enheten registrerats, distribuera profilcertifikatet till en användargrupp (inte en enhetsgrupp).

Om du distribuerar till en enhetsgrupp måste en fullständig enhetsregistrering utföras innan enheten tar emot principer.

1.  Även om varje profil distribueras separat, måste både den betrodda rotcertifikatprofilen och SCEP/.PFX-profilen distribueras. Annars misslyckas SCEP/.PFX-certifikatpolicyn.

2.  Du distribuerar certifikatprofiler på samma sätt som du distribuerar andra principer för Intune:

    -   Välj den princip som du vill distribuera på arbetsytan **Princip** och klicka sedan på **Hantera distribution**

    -   I dialogrutan **Hantera distribution** :

**Distribuera principen** – Markera en eller flera grupper som du vill distribuera principen till och klicka sedan på **Lägg till** &gt; **OK**
###  **Stänga dialogrutan utan att distribuera den** – Klicka på **Avbryt**

När du väljer en distribuerad princip visas ytterligare information om distributionen i den nedre delen av principlistan.

-  [Nästa steg](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Du kan nu använda certifikat för att skydda e-post-, Wi-Fi- och VPN-profiler:](wi-fi-connections-in-microsoft-intune.md)
-  [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler](vpn-connections-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


