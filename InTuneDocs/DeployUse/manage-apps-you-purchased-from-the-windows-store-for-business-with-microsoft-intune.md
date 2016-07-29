---
title: "Hantera Windows Store för företag-appar | Microsoft Intune"
description: "Anslut Microsoft Intune till Windows Store för företag om du vill hantera och distribuera volyminköpsappar från Intune-konsolen"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 07079b6566bec45593bb9ae49272aa7154a7174d


---

# Hantera appar som du har köpt från Windows Store för företag med Microsoft Intune
[Windows Store för företag](https://www.microsoft.com/business-store) ger dig en plats för att söka efter och köpa appar för din organisation, enskilt eller i volym. Genom att ansluta Windows Store till Microsoft Intune kan du hantera appar köpta i volym från Intune-konsolen, till exempel:
* Du kan synkronisera listan över appar som du har köpt från Windows Store med Intune.
* Appar som är synkroniserade visas i administrationskonsolen för Intune och du kan distribuera dem precis som andra appar
* Du kan spåra hur många licenser är tillgängliga och hur många som används i administrationskonsolen för Intune
* Intune blockerar distribution och installation av appar om det inte finns tillräckligt många tillgängliga licenser

## Innan du börjar
Granska följande information innan du börjar synkronisera och distribuera appar från Windows Store för företag:
* Du måste konfigurera Intune som utfärdare för hantering av mobila enheter för din organisation. Se [Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md) för mer information
* Du måste ha registrerat dig för ett konto i Windows Store för företag
* När du har associerat ett konto i Windows Store för företag med Intune kan du inte ändra till ett annat konto i framtiden.
* Appar från Windows Store kan inte manuellt läggas till eller tas bort från Intune. De kan endast synkroniseras med Windows Store för företag.
* Intune synkroniserar bara online-licensierade appar som du har köpt från Windows Store för företag.
* Enheterna måste vara anslutna till Active Directory-domänen eller arbetsplatsanslutna om du vill använda den här funktionen.
* Registrerade enheter måste använda 1511-versionen av Windows 10.

## Koppla ditt konto för Windows Store för företag till Intune
Innan du aktiverar synkronisering i Intune-konsolen måste du konfigurera ditt Windows Store-konto för att använda Intune som ett hanteringsverktyg:
1. Se till att du loggar in i Windows Store för företag med samma innehavarkonto som du använder för att logga in på Intune.
2. Välj **Inställningar** > **Hanteringsverktyg** i Business Store.
3. Välj **Lägg till ett hanteringsverktyg** och välj Microsoft Intune på sidan Hanteringsverktyg.

Du kan nu fortsätta och konfigurera synkronisering i Intune-konsolen.

## Konfigurera synkronisering

1. Klicka på **Admin** i [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com).
2. I fönstret **Administration** expanderar du **Hantering av mobila enheter** och klickar sedan på **Store för företag**.
3. Gör följande på sidan **Windows Store för Business**:
* Klicka på länken till registreringen för Windows Store för företag om du inte redan gjort det
* När du har loggat in klickar du på **Konfigurera synkronisering**
4. Välj **Aktivera synkronisering för Windows Store för företag** i dialogrutan **Konfigurera appsynkronisering för Windows Store för företag**.
5. Välj det språk du vill att appar från Windows Store för företag ska visas i Intune-konsolen från listrutan **Språk**. De kommer att installeras i slutanvändarens språk när det är tillgängligt oavsett vilket språk de visas i.
6. Klicka på **OK**.

## Synkronisera appar

1. På sidan **Windows Store för företag** klickar du på **Synkronisera nu** för att synkronisera de appar som du har köpt från Windows Store med Intune.
2. I arbetsytan **appar** klickar du på **Hanterad programvara** > **Licensierad programvara** för att se tillgängliga appar och kontrollera att dina köpta appar har importerats korrekt.
Appar i den här noden visas med det totala antalet licenser som du äger, tillsammans med antalet licenser som finns tillgängliga.

## Distribuera appar

Du kan distribuera appar från Windows Store på samma sätt som du distribuerar andra Intune-appar. Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).
När du distribuerar en app från Windows Store för företag används en licens för varje användare som installerar appen. Om du använder alla tillgängliga licenser för en distribuerad app kommer du inte att kunna distribuera fler kopior och måste vidta någon av följande åtgärder:
* Avinstallera appen från vissa enheter
* Minska omfånget för den aktuella distributionen för att fokusera på de användare som du har tillräckligt många licenser för
* Köpa fler kopior av appen från Windows Store för företag


### Se även
[Lägg till appar för mobila enheter i Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)





<!--HONumber=Jul16_HO4-->


