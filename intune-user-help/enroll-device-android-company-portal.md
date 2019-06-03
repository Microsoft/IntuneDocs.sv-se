---
title: Registrera en Android-enhet med Intune-företagsportalen | Microsoft Docs
description: Beskriver hur du registrerar en Android-enhet med Intune-företagsportalen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 736b1d891207a19f281aa1127975de1a55889e8b
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197033"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrera din enhet med företagsportalen  
Registrera din personliga eller företagsägda Android-enhet för att få säker åtkomst till företagets e-post, appar och data. Företagsportalen har stöd för Android-enheter, däribland Samsung Knox, som kör Android 4.4 och senare.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox är en typ av säkerhet som vissa Samsung-enheter använder för ytterligare skydd utöver vad den interna säkerheten i Android ger. Du kan kontrollera om du har en Samsung Knox-enhet genom att gå till **Inställningar** > **Om enheten**. Om du inte ser **Knox version** där har du en ursprunglig Android-enhet.

## <a name="enroll-device"></a>Registrera enhet  
Se till att [installera den kostnadsfria Intune-företagsportalsappen från Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Under registreringen kan du bli ombedd att välja en kategori som bäst beskriver hur du använder enheten. Företagets support använder ditt svar för att se vilka appar du har åtkomst till.  

1. Öppna företagsportalappen.  

3. På företagsportalens skärm **Välkommen** trycker du på **Logga in** och loggar sedan in med ditt arbets- eller skolkonto.

   ![Välkomstskärmen i företagsportalsappen för Android, som uppmanar användarna att logga in med sina obligatoriska arbets- eller skolkonton. Här informeras även om att Microsoft-konton och andra personliga konton inte godkänns.](./media/and-enroll-0-welcome-screen.png)   

4. Om du uppmanas att godkänna organisationens villkor trycker du på **GODKÄNN**. Den här skärmen kan skilja sig något från exemplet på skärmbilden nedan. 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. Logga in på företagsportalappen med ditt konto och lösenord för arbetet eller skolan och tryck sedan på **Logga in**.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. Tryck på **FORTSÄTT** på skärmen **Konfiguration av företagsåtkomst**.

   ![Skärmen Konfiguration av företagsåtkomst](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > De gula trianglarna innebär inte att du redan har råkat ut för ett fel. Ikonerna anger att det fortfarande finns oavslutade steg i registreringsprocessen.

7. Läs informationen om vad företagets support kan se och inte kan se på enheten och tryck sedan på **FORTSÄTT**.

   ![Sekretessinställningar](/intune/media/android_cp_enroll_02_after_1710.png)

8. På skärmen **Vad händer nu?** kan du läsa om vad som händer under registreringen. Tryck sedan på **REGISTRERA**.

   ![Skärmen Vad kommer härnäst](/intune/media/android_cp_enroll_03_after_1710.png)

9. Gör så här om du använder Android 6.0 eller senare. Annars går du till nästa steg.

   Följande meddelanden kan visas om företagets support har konfigurerat vissa principer:
   - **Tillåt att företagsportalen kan ringa och hantera telefonsamtal?**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   Om det här meddelandet visas trycker du på **TILLÅT**. Det är säkert att trycka på TILLÅT eftersom **Microsoft aldrig ringer eller hanterar dina telefonsamtal**! Google styr meddelandetexten och Microsoft kan inte ändra den. Allt du gör när du ger åtkomst är att du låter din enhet skicka enhetens IMEI-nummer (International Mobile Station Equipment Identity) till Intune. IMEI är ett slags serienummer som är en unik identifierare för en mobil enhet.

   Om du nekar åtkomst visas meddelandet igen nästa gång du loggar in på företagsportalen. Om du vill inaktivera framtida meddelanden väljer du **Fråga inte igen**. Om du vill återkalla åtkomstbehörigheten går du till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Telefon** och aktiverar sedan behörigheten.  

   - **Tillåt att företagsportalappen får åtkomst till dina kontakter?**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     Om det här meddelandet visas trycker du på **TILLÅT**. Det är säkert att trycka på TILLÅT eftersom **Microsoft aldrig bereder sig åtkomst till dina kontakter!** Google styr meddelandetexten och Microsoft kan inte ändra den. När du beviljar åtkomst låter det endast företagsportalappen att skapa, använda och hantera ditt arbetskonto.

     Om du nekar åtkomst visas meddelandet igen nästa gång du loggar in på företagsportalen, men du kan inaktivera framtida meddelanden genom att trycka på rutan **Fråga inte igen**. Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** &gt; **Appar** &gt; **Företagsportal** &gt; **Behörigheter** &gt; **Telefon** och sedan aktivera behörigheten.

10. På skärmen **Aktivera enhetsadministratör** trycker du på **Aktivera**.

    ![Skärmen Aktivera enhetsadministratör](./media/and-enroll-5-activate.png)

    Företagsportalen måste innehålla enhetsadministratörens roll för att kunna hantera enheten. Det innebär att administratören kan se vissa saker – t.ex. hur många gånger som du har försökt att låsa upp din skärm – och utföra vissa åtgärder.    

    Microsoft styr inte över det här meddelandet och vi förstår att dess formulering kan verka lite drastisk. Företagsportalen kan inte visa just de begränsningar och den åtkomst som gäller för din organisation. Alla beviljas samtidigt på den här skärmen. Kontakta företagets support med hjälp av kontaktinformationen på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980) om du har frågor som är specifika för användningen i din organisation.  

11. Följ anvisningarna för att ange en PIN-kod eller ett lösenord. Om du redan har ställt in en PIN-kod eller ett lösenord på enheten, visas inte den här skärmen och du behöver inte ange en ny PIN-kod eller ett nytt lösenord.  

    ![Ange PIN-kod eller lösenord](./media/and-enroll-6-PIN-native.png)

12. Om du använder en Samsung Knox-enhet trycker du på **Bekräfta**, så visas ett meddelande om att enheten registreras. Se följande skärm som visar att enheten registreras om du använder en Android-enhet.

    ![Sekretesspolicy för Samsung Knox](./media/and-enroll-7-knox-privacy-policy.png)

    Den här skärmen visar att enheten registreras.

    ![Skärmen Registrerar enheten](./media/and-enroll-8-device-enrolling.png)

13. När skärmen **Konfigurera företagsåtkomst** visas trycker du på **FORTSÄTT**. Om ett meddelande indikerar att enheten är inkompatibel följer du anvisningarna för att åtgärda problemet. Tryck sedan på **FORTSÄTT**.

    ![Enheten är inte kompatibel, men har registrerats](/intune/media/android_cp_enroll_05_post_1709.png)

    ![Det förekommer enhetsefterlevnadsproblem som måste lösas](/intune/media/android_cp_enroll_03_post_1709.png)

    Du hittar mer information om problemen genom att trycka på dem.

    ![Utvidgade enhetsefterlevnadsproblem](/intune/media/android_cp_enroll_04_post_1709.png)

    ![Skärmen Konfiguration av företagsåtkomst](./media/and-enroll-9d-comp-access-setup.png)  

14. På skärmen **Konfigurering av företagsåtkomst har slutförts** trycker du på **KLAR**. Enheten har nu registrerats.

    ![Skärmen Konfiguration av företagsåtkomst slutförd](./media/and-enroll-10-comp-access-setup-complete.png)

## <a name="next-steps"></a>Nästa steg  

Innan du försöker installera företagsappar går du till **Inställningar** > **Säkerhet** och aktiverar **Okända källor**. Om du inte aktiverar det här alternativet innan du försöker installera apparna visas följande meddelande: "Installationen blockerades". Av säkerhetsskäl är enheten inställd på att blockera installationer av appar från okända källor. Du kan trycka på **Inställningar** i dialogrutan med felmeddelandet för att gå till alternativet **Okända källor**.  

> [!Note]
> Om din organisation använder kostnad hanteringsprogramvara för telekomtjänster måste ytterligare ett part steg utföras innan enheten har registrerats fullständigt. Läs mer [här](enroll-your-device-with-telecom-expense-management-android.md).

Om du får ett felmeddelande när du försöker registrera enheten i Intune kan du [skicka ett e-postmeddelande till företagets support](send-logs-to-your-it-admin-by-email-android.md).  

Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.
