---
title: Registrera din Android-enhet i Intune | Microsoft Intune
description: Beskriver hur du registrerar en Android-enhet i Intune
keywords: 
author: staciebarker
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08eeb1f330ed8fcea5da41f71ded0ccf124da7c5
ms.openlocfilehash: 6fa1e13b6b0e29144c3740f00b232807e6e4e984


---


# Registrera en Android-enhet i Intune

Om företaget eller skolan använder Microsoft Intune kan du registrera din Android-enhet så att den får tillgång till företagets e-post, filer och andra resurser. Genom att registrera dina enheter kan IT-avdelningen hantera dessa arbets- eller skolresurser och skydda dem, samtidigt som du får friheten att använda den enhet du önskar för att utföra arbetet. Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md).

De här registreringsanvisningarna är för Samsung Knox Android-enheter och "ursprungliga" Android-enheter (inte Samsung Knox). Avgör om du har en Samsung Knox-enhet genom att välja **Inställningar** &gt; **Om enheten**. Om du inte ser orden "Knox version" i listan har du en ursprunglig Android-enhet.

Före eller efter registreringen kan du bli ombedd att välja en kategori som bäst beskriver hur du använder enheten. Din IT-administratör använder den här kategorin för att avgöra vilka appar du har åtkomst till.

Om du får ett felmeddelande när du försöker registrera enheten i Intune kan du [skicka registreringsfel till din IT-administratör](send-enrollment-errors-to-your-it-administrator-android.md).

**Registrera en Android-enhet:**

1.  Installera den kostnadsfria Intune-företagsportalsappen från [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2.  Öppna Microsoft Intune företagsportalapp.

3.  På företagsportalens skärm **Välkommen** trycker du på **Logga in** och loggar sedan in med ditt arbets- eller skolkonto.

    ![android-company-portal-sign-in](./media/and-enroll-0-welcome-screen.png)   

4.  Om IT-administratören konfigurerar företagsvillkor trycker du på **GODKÄNN** för att godkänna villkoren.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Logga in på företagsportalappen med ditt konto och lösenord för arbetet eller skolan och tryck på **Logga in**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  Tryck på **BÖRJA** på skärmen **Konfiguration av företagsåtkomst**.

    ![Skärmen Konfiguration av företagsåtkomst](./media/and-enroll-4a-comp-access-setup.png)

7.  På skärmen **Varför ska jag registrera enheten?** kan du läsa vad du kan göra när du har registrerat enheten. Tryck sedan på **FORTSÄTT**.

    ![Skärmen Varför ska jag registrera enheten](./media/and-enroll-4b-why-enroll.png)

8.  Läs informationen om vad IT-administratören kan se och inte kan se på enheten och tryck sedan på **FORTSÄTT**.

    ![Sekretessinställningar](./media/and-enroll-4c-we-care-privacy.png)

9.  På skärmen **Vad kommer härnäst** läser du om vad som händer under registreringen och trycker sedan på **REGISTRERA**.

    ![Skärmen Vad kommer härnäst](./media/and-enroll-4d-what-comes-next.png)

10.  Gör så här om du använder Android 6.0 eller senare. Annars går du till nästa steg.

    Följande meddelanden kan visas om IT-administratören har konfigurerat vissa principer:
    -   **Tillåt att företagsportalen kan ringa och hantera telefonsamtal?**

    ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Om det här meddelandet visas trycker du på **TILLÅT**. Det är säkert att trycka på TILLÅT, eftersom **Microsoft aldrig ringer eller hanterar dina telefonsamtal**! Google styr meddelandetexten och Microsoft kan inte ändra den. När du tillåter åtkomst tillåter du endast att enheten skriver dataloggar till enhetens SD-kort, vilket gör att du kan flytta dessa loggar med hjälp av en USB-kabel.

    Om du nekar åtkomst visas meddelandet igen nästa gång du loggar in på företagsportalen, men du kan inaktivera framtida meddelanden genom att trycka i kryssrutan **Fråga inte igen**.  Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** &gt; **Appar** &gt; **Företagsportal** &gt; **Behörigheter** &gt; **Telefon** och sedan aktivera behörigheten.

    -   **Tillåta att företagsportalappen får åtkomst till dina kontakter?**

    ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

    Om det här meddelandet visas trycker du på **TILLÅT**. Det är säkert att trycka på TILLÅT, eftersom **Microsoft aldrig bereder sig åtkomst till dina kontakter!** Google styr meddelandetexten och Microsoft kan inte ändra den. Om du beviljar åtkomst kan endast företagsportalappen skapa, använda och hantera ditt arbetskonto.

    Om du nekar åtkomst visas meddelandet igen nästa gång du trycker på **Skicka data**, men du kan inaktivera framtida meddelanden genom att markera kryssrutan **Fråga inte igen**. Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** &gt; **Appar** &gt; **Företagsportal** &gt; **Behörigheter** &gt; **Lagring** och sedan aktivera behörigheten.

11.  På skärmen **Aktivera enhetsadministratör** trycker du på **Aktivera**.

    ![Skärmen Aktivera enhetsadministratör](./media/and-enroll-5-activate.png)

12.  Följ anvisningarna för att ange en PIN-kod eller ett lösenord. Om du redan har ställt in en PIN-kod eller ett lösenord på enheten, visas inte den här skärmen och du behöver inte ange en ny PIN-kod eller ett nytt lösenord.

    ![Ange PIN-kod eller lösenord](./media/and-enroll-6-PIN-native.png)

13.  Om du använder en Samsung Knox-enhet trycker du på **Bekräfta**, så visas ett meddelande om att enheten registreras. Om du använder en ursprunglig Android-enhet observerar du skärmen nedan som visar att enheten registreras.

    ![Sekretesspolicy för Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    Den här skärmen visar att enheten registreras.

    ![Skärmen Registrerar enheten](./media/and-enroll-8-device-enrolling.png)

14. När skärmen **Konfigurera företagsåtkomst** visas trycker du på **FORTSÄTT**. Om ett meddelande om att enheten är inkompatibel visas följer du anvisningarna för att åtgärda problemet. Tryck sedan på **FORTSÄTT**.

    ![Skärmen Konfiguration av företagsåtkomst](./media/and-enroll-9-comp-access-setup.png)  

11. På skärmen **Konfigurering av företagsåtkomst har slutförts** trycker du på **KLAR**. Enheten har nu registrerats.

    ![Skärmen Konfiguration av företagsåtkomst slutförd](./media/and-enroll-10-comp-access-setup-complete.png)

Innan du försöker installera företagsappar besöker du **Inställningar** &gt; **Säkerhet**, och aktiverar **Okända källor**. Om du inte aktiverar det här alternativet innan du försöker installera apparna visas meddelandet Installationen blockerades. Av säkerhetsskäl är enheten inställd på att blockera installationer av appar från okända källor. Du kan trycka på **Inställningar** i dialogrutan med felmeddelandet för att gå till alternativet **Okända källor**.

Behöver du fortfarande hjälp? Kontakta IT-administratören (kontaktinformation finns på [företagsportalens webbplats](http://portal.manage.microsoft.com)) eller skriv till Microsoft Android-teamet på wintunedroidfbk@microsoft.com.






<!--HONumber=Aug16_HO5-->


