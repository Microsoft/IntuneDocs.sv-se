---
title: Kategorisera enheter i grupper i Intune
titleSuffix: Microsoft Intune
description: "Läs mer om att kategorisera enheter i grupper för enklare hantering."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d07b025881ea78299d617205ce5ba39bb92a1231
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="categorize-devices-into-groups-for-easier-management"></a>Kategorisera enheter i grupper för enklare hantering

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd Microsoft Intune-enhetskategorier för att automatiskt lägga till enheter i grupper baserat på kategorier som du definierar för att göra det enklare att hantera dessa enheter.

Enhetskategorier använder följande arbetsflöde:
1. Skapa kategorier som användare kan välja från när de registrerar sina enheter
2. När slutanvändare av iOS- och Android-enheter registrerar sin enhet, måste de välja en kategori från listan över kategorier som du har konfigurerat. Om de vill tilldela en kategori till en Windows-enhet, måste slutanvändare använda företagsportalen (du hittar mer information i **När du har konfigurerat enhetsgrupper** i den här artikeln).
3. Du kan sedan distribuera principer och appar för dessa grupper.

Du kan skapa vilken typ av enhetskategori som du vill, till exempel:
- Butiksenhet
- Demonstrationsenhet
- Försäljning
- Redovisning
- Manager

## <a name="how-to-configure-device-categories"></a>Så här konfigurerar du enhetsinställningar

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Steg ett – Skapa enhetskategorier i Intune-bladet på Azure-portalen
1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering**.
2. På bladet **Enhetsregistrering** väljer du **Enhetskategorier**.
3. På sidan **Enhetskategorier** väljer du **Skapa** för att lägga till en ny kategori.
4. På bladet **Skapa enhetskategori** anger du ett **Namn** på den nya kategorin och en valfri **Beskrivning**.
5. Klicka på **Skapa** när du är klar. Du kan se den nya kategorin i listan över kategorier.

Du kommer att använda enhetskategorinamnet när du skapar Azure Active Directory-säkerhetsgrupper i steg två.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Steg två – Skapa Azure Active Directory-säkerhetsgrupper
I det här steget kommer du att skapa dynamiska grupper i Azure Portal baserat på enhetskategori och enhetskategorinamn.

Se artikeln [Using attributes to create advanced rules](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) (Använda attribut för att skapa avancerade regler) i Azure Active Directory-dokumentationen för att fortsätta.

Använd informationen i det här avsnittet för att skapa en enhetsgrupp med en avancerad regel med hjälp av **deviceCategory**-attributet. Till exempel (**device.deviceCategory -eq** "*<the device category name you got from the Azure portal>*")

När du har konfigurerat enhetsgrupper och användarna då registrerar sina enheter får de se en lista med de kategorier som du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den Active Directory-säkerhetsgrupp som motsvarar den kategori som har valts.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Så här visar du kategorier av enheter som du hanterar

1.  I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enheter**.

2.  Under **Hantera** klickar du på **Alla enheter**.

3.  I listan med enheter granskar du kolumnen **Enhetskategori**.

Om kolumnen **Enhetskategori** inte visas klickar du på **Kolumner**, väljer **Enhetskategori** i listan och klickar sedan på **Tillämpa**.

### <a name="to-change-the-category-of-a-device"></a>Ändra kategori för en enhet

1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enheter**.
2. På bladet **Enheter** under avsnittet **Hantera** väljer du **Alla enheter**.
3. I listan med enheter väljer du önskad enhet och på enhetens egenskapsblad, under avsnittet **Hantera**, väljer du **Egenskaper**.
4. På nästa blad kan du ändra **Enhetskategori** för den valda enheten till ett kategorinamn som du tidigare har konfigurerat.

## <a name="after-you-configure-device-groups"></a>När du har konfigurerat enhetsgrupper

När slutanvändare av iOS- och Android-enheter registrerar sin enhet, måste de välja en kategori från listan över kategorier som du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den Intune-enhetsgruppen eller Active Directory-säkerhetsgruppen som motsvarar den kategori som har valts.

Slutanvändare i Windows bör använda den nya webbplatsen för företagsportalen och välja en kategori där.

Oavsett vilken plattform slutanvändarna har kan de alltid gå till portal.manage.microsoft.com efter att enheten registrerats. Få användaren att gå till **Mina enheter** på företagsportalens webbplats. De kan välja en registrerad enhet som visas på sidan och sedan välja en kategori.

Efter att du har valt en kategori, läggs enheten automatiskt till i motsvarande grupp som du har skapat. Om en enhet redan är registrerad innan du konfigurerar kategorier, får slutanvändaren ett meddelande om enheten på företagsportalen och uppmanas att välja en kategori nästa gång de går in på företagsportalappen på iOS eller Android.

## <a name="further-information"></a>Ytterligare information
- Du kan redigera en enhetskategori i Azure-Portal, men du måste manuellt uppdatera alla Azure Active Directory-säkerhetsgrupper som refererar till den här kategorin.

- Om du tar bort en kategori kommer enheter tilldelade till den att visa kategorinamnet **Otilldelad**.
