---
# required metadata

title: Starta en utvärdering av Microsoft Intune och distribuera en PIN-princip för iOS | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Starta en utvärdering av Microsoft Intune och distribuera PIN-principen för iOS
Dessa stegvisa anvisningar hjälper dig att konfigurera en Intune-utvärdering och att konfigurera en PIN-princip för iOS-enheter. En lista över andra vanliga Intune-utvärderingsaktiviteter som du kan prova finns i [Vanliga Microsoft Intune-utvärderingsaktiviteter](common-microsoft-intune-evaluation-tasks.md)



## Granska kraven för den här aktiviteten

-   Windows-dator med Internet Explorer – för att utföra administrativa uppgifter

-   iOS 7.1 eller senare enhet för att testa verifieringen av användarprinciper

-   Telefonnummer för att autentisera dig under utvärderingsregistreringen

## Skapa ett kostnadsfritt utvärderingskonto för Intune
> Om du redan har en Intune-prenumeration hoppar du över det här avsnittet och går till nästa avsnitt.

1.  På en Windows-dator högerklickar du på **Internet Explorer** (IE) och väljer **InPrivate-surfning**

    ![Starta InPrivate-surfning](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  Gå till [registreringsportalen för Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1), ange den begärda informationen och klicka på **Nästa**.

    ![Registrera dig för ett konto](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  Ange ett användar-ID och lösenord för administratörskontot och klicka sedan på **Nästa**. Du ska använda det här ID:t för att logga in på Intune-portalen där du kan utföra dina administratörsuppgifter.

    ![Skapa ett ID](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  Ange ditt mobiltelefonnummer och klicka på **SMS:a mig** för att verifiera ditt nummer.

    ![Kontrollera dina uppgifter](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  Spara informationen som visas på skärmen och klicka sedan på **Allt är klart**.

    ![Redo att sätta igång](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## Skapa en testanvändare

1.  På en Windows-dator klickar du på **Starta** för att gå till sidan för användarhantering.

    ![Gå till sidan för användarhantering](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  Klicka på knappen **+** för att lägga till en användare.

    ![Lägg till en användare](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  På sidan **Skapa nytt användarkonto**:

    1.  Ange information om testanvändaren.

    2.  Välj alternativet **Ange lösenordet**.

    3.  Avmarkera kryssrutan **Användaren måste byta lösenord vid nästa inloggning**.

    4.  Klicka på **Skapa**

    ![Skapa ett nytt användarkonto](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  Klicka på **Stäng** på bekräftelsesidan

    ![Bekräftelsesida för användargenerering](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  Klicka på **Uppdatera** för att visa testanvändaren som du skapat.

    ![Kontobekräftelse](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## Konfigurera en PIN-princip för iOS för testanvändaren

1.  På en Windows-dator anger du Intune som MDM-utfärdare:

    1.  Gå till [Intune-hanteringskonsolen](http://manage.microsoft.com/), logga in med ditt administratörskonto och klicka på **Börja hantera mobila enheter**. Sidan Utfärdare av Hantering av mobila enheter öppnas.

        ![Komma igång i Intune-konsolen](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  Klicka på länken **Ange utfärdare för hantering av mobila enheter**.

        ![Ange utfärdare för hantering av mobila enheter](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  Aktivera iOS-enheter för registrering. Den här processen ställer in ett betrott certifikat mellan Apple Push Notification Service (APNs) och din Intune-prenumeration.

    1.  Klicka på **Aktivera iOS- och Mac OS X-plattformen**

        ![Aktivera iOS- och Mac OS X-registrering](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  Klicka på **Hämta begäran om APN-certifikat**

        ![Hämta APN-certifikatet](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  Ange ett filnamn och en plats för certifikatsigneringsförfrågan och klicka på **Spara**. Den här filen innehåller den offentliga nyckeln som motsvarar en privat nyckel som innehas av Intune-prenumerationen.

        ![Ange begäran om certifikatsignering](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  Öppna en ny flik genom att klicka på **Apple Push Certificates-portalen**.

        ![Gå till sidan för APNs-certifikat](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  Ange ditt Apple-ID och lösenord och klicka på **Logga in**. Det här ID:t kan vara det som du använder på din iOS-enhet för att hämta appar från iOS App Store.

        ![Logga in på Apples portal för Push-certifikat](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  Klicka på **Skapa ett certifikat**

        ![Skapa ett APNs-certifikat](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  Läs Apples användningsvillkor, markera kryssrutan och klicka på **Acceptera**

        ![Acceptera villkoren](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  Klicka på **Bläddra**

        ![Bläddra till platsen där du sparade certifikatet](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. Välj CSR-filen som du sparade tidigare och klicka på **Öppna**

        ![Öppna certifikatet](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. Klicka på knappen **Ladda upp**.

        ![Ladda upp certifikatet](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. När du uppmanas att hämta en JSON-fil klickar du på **Spara som**

        ![Spara JSON-filen](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. Ange en plats för JSON-filen och klicka på **Spara**

        ![Ange var du vill spara JSON-filen](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        Om du inte omdirigeras automatisk efter några sekunder klickar du på **Avbryt**

        ![Avbryt om du inte omdirigeras automatiskt](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. Hämta den nya certifikatfilen genom att klicka på **Ladda ned**

        ![Hämta certifikatet](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. När du uppmanas att ladda ned en PEM-fil klickar du på **Spara som**

        ![Hämta PEM-filen](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. Ange en plats för PEM-filen och klicka på **Spara**

        ![Spara PEM-filen](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. Gå tillbaka till fliken för Intune-hanteringskonsolen och klicka på **Överför ett APN-certifikat**

        ![Ladda upp APN-certifikatet](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. Ange ditt Apple-ID och klicka på **Bläddra**

        ![Ange ditt Apple-ID](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. Välj PEM-filen som du precis sparat och klicka på **Öppna**

        ![Öppna PEM-filen](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. Klicka på **Överför**

        ![Ladda upp PEM-filen](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        Nu har ditt APN-certifikat konfigurerats.

        ![APN-certifikatet har konfigurerats](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  Skapa en testanvändargrupp för riktad principtillämpning:

    1.  I den vänstra rutan klickar du på **Grupper**

        ![Öppna grupper](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  Längst till höger klickar du på **Skapa grupp**

        ![Skapa en grupp](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  Ange ett gruppnamn, välj **Alla användare** som den överordnade gruppen och klicka på **Nästa**

        ![Välj Alla användare som den överordnade gruppen](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  I fältet **Starta gruppmedlemskap med** väljer du **Alla användare i den överordnade gruppen** och klickar på **Slutför**

        ![Starta gruppmedlemskap med den överordnade gruppen](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  Skapa en PIN-princip för iOS och aktivera den för testanvändargruppen:

    1.  I den vänstra rutan klickar du på **Princip**

        ![Öppna principarbetsytan](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  Längst till höger klickar du på **Lägg till princip**

        ![Lägg till en princip](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  Expandera iOS-noden, välj raden **Allmän konfiguration** och klicka på **Skapa princip**

        ![Skapa en allmän iOS-konfigurationsprincip](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  Ange ett namn för principen, aktivera alternativet **Kräv lösenord för att låsa upp mobila enheter** och ange **Minsta längd på lösenord** till **4**

        ![Konfigurera inställningar för lösenord](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  Distribuera principen genom att klicka på **Ja**.

        ![Distribuera princip](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  Klicka på användargruppen som du skapade tidigare, klicka på **Lägg till** och sedan på **OK**

        ![Välj grupp för principen](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        Nu har du en PIN-princip för iOS som tillämpas på testanvändargruppen.

        ![Principen har konfigurerats](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## Kontrollera att principen tillämpas på en iOS-enhet

1.  På en iPad startar du App Store för iOS och installerar den kostnadsfria appen **Microsoft Intune-företagsportal** och öppnar den.

    ![Installera företagsportalen](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  Ange namnet på ditt testanvändarkonto och tryck på **Logga in**

    ![Ange dina inloggningsuppgifter](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  Tryck på **Registrera** för att börja registrera enheten i Intune.

    ![Starta registreringen](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  Tryck på **Installera** på skärmen **Installera profil**

    ![Installera en profil](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  Tryck på **Installera** i dialogrutan **Installera profil**

    ![Fortsätt att installera profilen](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  Tryck på **Installera** på skärmen **Varning**

    ![Acceptera varningsmeddelandet](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  Tryck på **Förtroende** i dialogrutan **Fjärrhantering**

    ![Välj att lita på fjärrhantering](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  När hanteringsprofilen har installerats trycker du på **Klart**. Registreringen är klar.

    ![Registreringen är klar](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. När registreringen är klar trycker du på **OK** och stänger sedan företagsportalappen.

    ![Stäng företagsportalappen genom att trycka på OK](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. När du uppmanas att konfigurera ett lösenord trycker du på **Fortsätt**

    ![Acceptera uppmaningen om att konfigurera lösenordet](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. Ange ditt lösenord, tryck på **Fortsätt**, ange lösenordet igen och tryck på **Spara**

    ![Ange ett lösenord](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. Tryck på strömknappen för att låsa iPad-enheten och dra sedan för att låsa upp den. Som du ser måste du nu ange ditt lösenord för att låsa upp enheten.

### Se även
[Utvärderingsguiden för Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md)


<!--HONumber=May16_HO2-->


