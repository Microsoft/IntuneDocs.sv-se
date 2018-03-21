---
title: "Hantera appar från Microsoft Store för företag"
titlesuffix: Microsoft Intune
description: "Lär dig hur du kan synkronisera appar i Intune från Microsoft Store för företag och sedan tilldela och spåra dessa appar."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa5e3b5559c5c17ea726b26f1c1f56ef37cfe0ae
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Så här hanterar du appar som du har köpt från Microsoft Store för företag med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


I [Microsoft Store för företag](https://www.microsoft.com/business-store) kan du söka efter och köpa appar för din organisation, separat eller i volym. Genom att ansluta butiken till Microsoft Intune kan du hantera volyminköpta program från Azure-portalen. Exempel:
* Du kan synkronisera listan över appar som du har köpt från Windows Store med Intune.
* Appar som är synkroniserade visas i administrationskonsolen för Intune. Du kan tilldela de här apparna på samma sätt som andra appar.
* Du kan spåra hur många licenser som är tillgängliga och hur många som används i administrationskonsolen för Intune.
* Intune blockerar tilldelning och installation av appar om det inte finns tillräckligt många tillgängliga licenser.
* Appar som hanteras av Microsoft Store för företag återkallar automatiskt licenser när en användare lämnar företaget eller när administratören tar bort användaren och användarenheterna.

## <a name="before-you-start"></a>Innan du börjar

Granska följande information innan du börjar synkronisera och tilldela appar från Microsoft Store för företag:

- Konfigurera Intune som utfärdare för hantering av mobila enheter för din organisation.
- Du måste ha registrerat dig för ett konto i Microsoft Store för företag.
- När du har associerat ett konto i Microsoft Store för företag med Intune kan du inte ändra till något annat konto i framtiden.
- Appar som köpts från butiken kan inte manuellt läggas till i eller tas bort från Intune. De kan endast synkroniseras med Microsoft Store för företag.
- Både online- och offlinelicensierade appar som du har köpt från Microsoft Store för företag synkroniseras i Intune-portalen. Du kommer sedan att kunna distribuera apparna till enhetsgrupper eller användargrupper. 
- Online-appinstallationer hanteras i butiken.
- Kostnadsfria offlineappar kan också synkroniseras till Intune. Dessa appar installeras av Intune och inte av butiken.
- För användning av den här funktionen måste enheterna vara anslutna till Active Directory Domain Services eller arbetsplatsanslutna.
- Registrerade enheter måste använda 1511-versionen av Windows 10 eller senare.

Relaterade uppsättningar och offlinelicensierade appar som synkroniseras från Microsoft Store för företag kommer dessutom nu konsolideras till en enda appost i användargränssnittet. All distributionsinformation från enskilda paket migreras till den enda posten. Om du vill se relaterade uppsättningar i Azure-portalen väljer du **Applicenser** på bladet **Mobilappar**.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>Koppla ditt konto för Microsoft Store för företag till Intune
Innan du aktiverar synkronisering i Intune-konsolen måste du konfigurera ditt Windows Store-konto för att använda Intune som ett hanteringsverktyg:
1. Se till att du loggar in i Windows Store för företag med samma klientkonto som du använder för att logga in på Intune.
2. Välj **Inställningar** > **Hanteringsverktyg** i Business Store.
3. Välj **Lägg till ett hanteringsverktyg** och välj **Microsoft Intune** på sidan Hanteringsverktyg.

> [!NOTE]
> Tidigare kunde du bara associera ett hanteringsverktyg för att tilldelning av appar med Microsoft Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager.

Du kan nu fortsätta och konfigurera synkronisering i Intune-konsolen.

## <a name="configure-synchronization"></a>Konfigurera synkronisering

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
1. I fönstret **Mobilappar** väljer du **Installation** > **Microsoft Store för företag**.
2. Klicka på **Aktivera**.
3. Om du inte redan gjort det klickar du på länken för att registrera Microsoft Store för företag och kopplar kontot på det sätt som beskrivs tidigare.
5. I listrutan **Språk** väljer du det språk som ska användas vid visning av program från Microsoft Store för företag i Azure Portal. Apparna installeras i slutanvändarens språk om det är tillgängligt oavsett vilket språk de visas i.
6. Klicka på **Synkronisera** för att hämta appar som du har köpt från Microsoft Store i Intune.

## <a name="synchronize-apps"></a>Synkronisera appar

1. Välj **Installation** > **Microsoft Store för företag** i arbetsbelastningen **Mobilappar**.
2. Klicka på **Synkronisera** för att hämta appar som du har köpt från Microsoft Store i Intune.

## <a name="assign-apps"></a>Tilldela appar

Du kan tilldela appar från Windows Store på samma sätt som du tilldelar andra Intune-appar. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md). I stället för att tilldela appar från sidan **Alla appar** kan du tilldela dem från sidan **Licensierade appar**.

Offlineappar kan riktas till användargrupper, enhetsgrupper eller grupper med användare och enheter.
Offlineappar kan installeras för en viss användare av en enhet eller för alla användare av en enhet. 


När du tilldelar en app från Microsoft Store för företag används en licens för varje användare som installerar appen. Om du använder alla tillgängliga licenser för en tilldelad app kommer du inte att kunna tilldela fler exemplar. Välj en av följande åtgärder:
* Avinstallera appen från vissa enheter.
* Minska omfånget för den aktuella tilldelningen för att bara fokusera på de användare som du har tillräckliga licenser för.
* Köpa fler kopior av appen från Microsoft Store för företag.


