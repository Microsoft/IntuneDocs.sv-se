---
title: Migrera till Intune | Microsoft Intune
description: 
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: jeffgilb
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: c5adeb2164a55d029c9d7f86490092a72f04f126


---

# <a name="migrate-to-intune"></a>Migrera till Intune


Migreringen till Intune från din befintliga lösning för mobilitetshantering i företaget kan följa de allmänna stegen nedan:

![Migreringssteg för Intune](./media/migrate-intune-steps.png)

## <a name="notify-users"></a>Meddela användarna

När du anser att pilotdistributionen av Intune uppfyller dina krav informerar du användarna om den kommande migreringen av deras enheter till Intune. E-postmeddelanden, instruktioner och [affischer](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT) kan hjälpa dig att skapa förväntningar och ge registreringsinformation om de steg användarna måste följa för att upprätthålla kontinuerlig anslutning till företagets resurser och program. Se till att supportteamet är redo att hjälpa användarna med migreringen.

## <a name="modify-your-existing-enterprise-mobility-management-solution"></a>Ändra din befintliga lösning för mobilitetshantering i företaget

Beroende på hur du planerar att hantera principer för villkorlig åtkomst mellan din befintliga lösning för mobilitetshantering i företaget och Intune, kan du behöva inaktivera de befintliga principerna för villkorlig åtkomst. Du inaktiverar antingen de befintliga principerna för villkorlig åtkomst ELLER ändrar de befintliga principerna för villkorlig åtkomst så att de inte omfattar användare/enheter som du håller på att migrera till Intune.  Se till att inte både Intune och din befintliga lösning för mobilitetshantering i företaget använder principer för villkorlig åtkomst för samma användare/enheter.

## <a name="enable-intune-conditional-access-policy-optional"></a>Aktivera princip för villkorlig åtkomst i Intune (valfritt)

Om du har valt att omedelbart tillämpa principerna för villkorlig åtkomst utan respitperiod för migrering av enheter, aktiverar du principer för villkorlig åtkomst i Intune i det här steget.  Se till att användarna och supportteamet informeras om beslutet.  Om enheter inte är registrerade i Intune och inte är kompatibla med Intune-principer har användarna inte åtkomst till företagsresurser förrän de registreras i Intune och enheterna är kompatibla med Intune-principer.

## <a name="unenrolling-devices-from-your-existing-enterprise-mobility-management-solution"></a>Avregistrera enheter från din befintliga lösning för mobilitetshantering i företaget

Enheter måste avregistreras från din befintliga lösning för mobilitetshantering i företaget innan de registreras i Intune. Vår rekommendation är att låta användarna avregistrera sina enheter själva för bästa möjliga användarupplevelse.  Följ anvisningarna för avregistrering från lösningsleverantören för att se till att du tar bort användare och enheter från plattformen på rätt sätt, för minsta möjliga störningar för slutanvändarna.

## <a name="enrolling-devices-in-intune"></a>Registrera enheter i Intune

Användare som har schemalagts för migrering bör omedelbart registreras i Intune för att få tillbaka eller förhindra förlorad åtkomst till företagets resurser, e-post och program. Om du har konfigurerat villkorlig åtkomst och användarna försöker ansluta till e-post innan de registrerats i Intune blockeras deras åtkomst och de får ett e-postmeddelande om registrering. I e-postmeddelandet får de hjälp att registrera sin enhet i Intune.  Användarna kan också registreras i Intune via företagsportalappen för Intune eller internt via operativsystemet på Windows 8.1 och Windows 10 Mobile. Mer information om registreringsstegen för varje plattform finns i [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).

## <a name="configure-intune-conditional-access-optional"></a>Konfigurera villkorlig åtkomst i Intune (valfritt)

Om du har tillåtit en respitperiod för tillämpning av villkorlig åtkomst aktiverar du principer för villkorlig åtkomst i Intune för att starta tillämpning när respitperioden som du har informerat slutanvändarna om är slut. Det kräver omedelbart att alla enheter uppfyller kraven enligt principen för villkorlig åtkomst i Intune.

## <a name="enroll-remaining-devices-and-users"></a>Registrera återstående enheter och användare

Nu när du har aktiverat villkorlig åtkomst måste alla användare registreras i Intune och uppfylla organisationens principer för efterlevnad för att få åtkomst till företagets resurser. Om du har migrerat användarna i en fasindelad registrering (inte alla samtidigt) upprepar du ovanstående steg tills alla enheter och användare har registrerats och hanteras av Intune.

## <a name="retire-the-previous-enterprise-mobility-management-solution"></a>Dra tillbaka den tidigare lösningen för mobilitetshantering i företaget

När du har migrerat alla användare och enheter till Intune och bekräftat att migreringarna till Intune har lyckats kan du dra tillbaka den tidigare lösningen för mobilitetshantering i företaget och/eller avsluta prenumerationen på tjänsten. Följ anvisningarna från lösningsleverantören för att se till att du tar bort eventuella onödiga infrastrukturkrav och avbryter alla prenumerationer/licenser på rätt sätt.

## <a name="additional-migration-resources"></a>Ytterligare migreringsresurser

Behöver du mer hjälp med migreringen till Intune? Vi erbjuder alternativ för experthjälp för att se till att migreringen sker utan problem:

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft Consulting Services](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Teknisk och icke-teknisk support för Intune](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [TechNet-forum om Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## <a name="get-a-downloadable-copy-of-this-guide"></a>Hämta en nedladdningsbar kopia av den här guiden

Om du vill hämta en kopia av hela handboken går du till [TechNet-galleriet](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387).



<!--HONumber=Nov16_HO4-->


