---
title: Registrera din macOS-enhet i Intune med företagsportalen| Microsoft Docs
description: Beskriver hur du registrerar en macOS-enhet i Intune med företagsportalappen
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: af5c7492563c8df0168eff3250ae1bbad2cc323e
ms.sourcegitcommit: 490365fb8b5405f323b4358fb1ec9dfdd9ff2d58
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2018
ms.locfileid: "43147725"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrera din macOS-enhet i Intune på företagsportalappen

Registrera din macOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

Organisationer kräver ofta att din enhet blir hanterad innan du kan komma åt egna data från den. När en enhet blir hanterad kan organisationer skicka principer och appar till enheten via sin leverantör av hantering av mobilenheter. För att få kontinuerlig tillgång till arbets- eller skolinformation från enheten måste du konfigurera den så att principinställningarna matchar.  

Den här artikeln beskriver hur Intune-företagsportalappen för macOS hjälper dig att registrera, konfigurera och underhålla enheten så att den uppfyller organisationens krav.

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen

Under installationen kräver appen att du autentiserar dig själv hos organisationen. Den informerar dig sedan om eventuella enhetsinställningar du måste göra. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.    

När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. Appskyddsprinciper som den här är vanliga i organisationer och kräver ofta att du avinstallerar ej betrodda appar innan du kan få åtkomst.

Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Få din enhet hanterad  
Använd följande steg för att registrera macOS-enheter som kör OS X El Capitan 10.11 och senare.   


1. Du kommer åt företagsportalwebbplatsen genom att öppna ett nytt fönster i __Safari__ och gå till https://portal.manage.microsoft.com.  

2. Logga in på företagsportalens webbplats med ditt arbets- eller skolkonto.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Gå till sidans övre vänstra hörn och klicka på **Meny** > **Enheter**.  

4. På sidan __Enheter__ visas en lista över hanterade enheter eller ett meddelande. Vad som visas beror på om du redan har en hanterad enhet. 
    * Om du vill lägga till en enhet som inte visas i listan väljer du meddelandet **Tap here to tell us which device you're using or add a new device** (Tryck här för att berätta vilken enhet du använder eller lägga till en ny enhet).
    * Om du inte har några enheter visas meddelandet: **You don't have any managed devices. Add this one by tapping here.** (Du har inga hanterade enheter. Lägg till den här genom att trycka här.). Klicka på meddelandet för att lägga till din enhet.  

     ![En skärmbild av sidan Enheter med en röd ruta runt meddelandealternativet för att markera var du ska klicka.](./media/CP-enroll-MACOS-1808.png)  
5.  Slutför det steg nedan som överensstämmer med det meddelande som visas i företagsportalen.  
    * Om du lägger till en enhet för första gången uppmanas du att ladda ned företagsportalappen på enheten. Klicka på **Hämta** att fortsätta.  

         ![Exempel på skärmbild för meddelandeskärmen för att hämta macOS-företagsportalappen. Användaren kan välja att klicka på den blå knappen Hämta längst ned till vänster i meddelandet, eller den grå knappen Avbryt längst ned till höger.](./media/CP-enroll-download-macOS-1808.png)  

    * Om du redan har en hanterad macOS-enhet visas ett meddelande med en lista över dina macOS-enheter som hanteras för närvarande. Välj **My device isn't listed here** (Min enhet visas inte här) > **Hämta** för att hämta företagsportalappen på den enhet som du lägger till.  

         ![Exempel på skärmbild för meddelandeskärmen för att hämta macOS-företagsportalappen. Användaren kan välja *My device isn't listed here* (Min enhet visas inte här) eller en specifik enhet från mitten av sidan. Den blå knappen Hämta visas längst ned till vänster i meddelandet och den grå knappen Avbryt visas längst ned till höger](./media/cp-mac-os-device-isnt-here-1808.png)  

6. Enheten kontrollerar att installationsfilen **CompanyPortal.pkg** är säker att öppna. När det är slutfört öppnar du installationsprogrammet och slutför installationen.  

7. När installationsprogrammet har slutförts går du till **Startfönstret** och öppnar **Företagsportal**.  

8. macOS-enheten uppmanar dig att bekräfta att du vill öppna företagsportalappen. Klicka på **Öppna**.  

   > [!TIP]
   > Intune behöver åtkomst till datorn för att se till att enheten är säker nog för att få åtkomst till organisationens resurser. Om datorn vägrar att öppna företagsportalappen kan du [inaktivera Gatekeeper](https://support.apple.com/HT202491). Öppna sedan appen.

9. Den första skärmen som visas i företagsportalappen uppmanar dig att **Logga in**. Använd samma arbets- eller skolkonto som du använde för att logga in på företagsportalens webbplats.

10. Företagsportalen bekräftar kontoinformationen och visar statusen för **Enhetsregistrering** och **Enhetsefterlevnad**. Gula trianglar markerar de åtgärder du måste utföra för att skydda din macOS-enhet för skolan eller arbetet. Klicka på **Börja** för att starta registreringen. Läs om [vad din organisation kan se](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) när du registrerar en enhet.

11. Du kan uppmanas att ange din dators inloggningsinformation. Det kan ta några minuter att registrera enheten i hantering. Du kan göra andra saker på enheten under tiden. Du får ett meddelande när du har slutfört konfigurationen av företagsåtkomst så att du vet att du är färdig.  

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  
