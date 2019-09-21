---
title: Registrera din macOS-enhet i Intune med företagsportalen| Microsoft Docs
description: Beskriver hur du registrerar en macOS-enhet i Intune med företagsportalappen
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
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
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9047dd9bbc55162eae4693d3035cb05ff4becb91
ms.sourcegitcommit: 8934b1abec96e18cee15a77107d37551766f7666
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71099848"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrera din macOS-enhet i Intune på företagsportalappen

Registrera din macOS-enhet i Intune-företagsportalappen för att få säker åtkomst till organisationens e-post, filer och appar.

Organisationer kräver ofta att din enhet blir hanterad innan du kan komma åt egna data från den. När en enhet blir hanterad kan organisationer skicka principer och appar till enheten via sin leverantör av hantering av mobilenheter. För att få kontinuerlig tillgång till arbets- eller skolinformation från enheten måste du konfigurera den så att principinställningarna matchar.  

Den här artikeln beskriver hur Intune-företagsportalappen för macOS hjälper dig att registrera, konfigurera och underhålla enheten så att den uppfyller organisationens krav.  
</br>
> [!VIDEO https://www.youtube.com/embed/Pa2pfhwq_yk?rel=0]

## <a name="what-to-expect-from-the-company-portal-app"></a>Vad du kan förvänta dig av företagsportalappen

Under installationen kräver appen att du autentiserar dig själv hos organisationen. Den informerar dig sedan om eventuella enhetsinställningar du måste göra. Organisationer anger exempelvis ofta krav på lägsta eller högsta antal tecken i lösenordet som du måste uppfylla.    

När enheten har registrerats fortsätter företagsportalappen att se till att enheten är skyddad. Om du till exempel installerar en app från en ej betrodd källa kommer appen meddela dig och återkallar ibland åtkomst till företagets data. Appskyddsprinciper som den här är vanliga i organisationer och kräver ofta att du avinstallerar ej betrodda appar innan du kan få åtkomst.

Om organisationen inför ett nytt säkerhetskrav efter registreringen, t.ex. multifaktorautentisering, meddelar företagsportalappen dig. Du får möjlighet att justera dina inställningar så att du kan fortsätta arbeta från enheten.  

Mer information om registrering finns i [Vad händer när jag installerar företagsportalappen och registrerar min enhet?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md).  

## <a name="get-your-device-managed"></a>Få din enhet hanterad  
Använd följande steg för att registrera macOS-enheter som kör macOS 10,12 och senare.   


1. Du kommer åt företagsportalwebbplatsen genom att öppna ett nytt fönster i __Safari__ och gå till https://portal.manage.microsoft.com.  

2. Logga in på företagsportalens webbplats med ditt arbets- eller skolkonto.

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. Gå till sidans övre vänstra hörn och klicka på **Meny** > **Enheter**.  

4. På sidan __Enheter__ visas en lista över hanterade enheter eller ett meddelande. Vad som visas beror på om du redan har en hanterad enhet. 
    * Om du vill lägga till en enhet som inte visas i listan väljer du meddelandet **Tap here to tell us which device you're using or add a new device** (Tryck här för att berätta vilken enhet du använder eller lägga till en ny enhet).
    * Om du inte har några enheter visas meddelandet: **You don't have any managed devices. Add this one by tapping here.** (Du har inga hanterade enheter. Lägg till den här genom att trycka här.). Klicka på meddelandet för att lägga till din enhet.  

     ![En skärmbild av sidan Enheter med en röd ruta runt meddelandealternativet för att markera var du ska klicka.](./media/CP-enroll-MACOS-1808.png)  
5. Slutför det steg nedan som överensstämmer med det meddelande som visas i företagsportalen.  
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

10. Företagsportalen bekräftar kontoinformationen och visar statusen för **Enhetsregistrering** och **Enhetsefterlevnad**. Gula trianglar markerar de åtgärder du måste utföra för att skydda din macOS-enhet för skolan eller arbetet. Klicka på **Börja** för att starta registreringen. 

11. Om du uppmanas att göra det anger du datorns inloggningsinformation.  

Det kan ta några minuter att registrera enheten i hantering. Du kan göra andra saker på enheten under tiden. Du får ett meddelande när du har slutfört konfigurationen av företagsåtkomst så att du vet att du är färdig.  

## <a name="unverified-profiles"></a>Overifierade profiler
När du visar de installerade MDM-profilerna för hantering av mobilenheter för din macOS-enhet kan vissa profiler visas med statusen **Inte verifierad**. Så länge som **Hanteringsprofil** visar statusen **Verifierad** behöver du inte bry dig om detta.  

Hanteringsprofilen är vad som definierar MDM-kanalanslutningen. Så länge hanteringsprofilen är verifierad ärver alla andra profiler som levereras till datorn, via kanalen, hanteringsprofilens säkerhetsegenskaper.

Och eftersom de övriga profilerna inte kräver enskilda verifieringar genereras och levereras de snabbare till enheter. 

## <a name="updating-the-company-portal-app"></a>Uppdatera företagsportalappen

Företagsportalappen uppdateras på samma sätt som andra Office-appar, genom Microsoft AutoUpdate för Mac. Läs mer om [uppdatering av Microsoft-appar för macOS här](https://support.office.com/article/Check-for-Office-for-Mac-updates-automatically-bfd1e497-c24d-4754-92ab-910a4074d7c1).  

## <a name="next-steps"></a>Nästa steg  
Behöver du mer hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  


