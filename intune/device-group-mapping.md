---
title: Kategorisera enheter i grupper i Intune
titleSuffix: Microsoft Intune
description: Läs mer om att kategorisera enheter i grupper för enklare hantering.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a52244ae9ef8490bc95d242f896e45dc4ccbdf2f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31024421"
---
# <a name="categorize-devices-into-groups-for-easier-management"></a>Kategorisera enheter i grupper för enklare hantering

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Använd Microsoft Intune enhetskategorier för att automatiskt lägga till enheter i grupper baserat på kategorier som du definierar. Det gör det enklare för dig att hantera enheterna.

Enhetskategorier använder följande arbetsflöde:
1. Skapa kategorier som användare kan välja från när de registrerar sina enheter.
2. När användare av iOS- och Android-enheter registrerar en enhet, måste de välja en kategori från listan över kategorier som du har konfigurerat. Om de vill tilldela en kategori till en Windows-enhet måste användarna använda webbplatsen Företagsportal.
3. Du kan sedan distribuera principer och appar för dessa grupper.

Du kan skapa vilken typ av enhetskategori som du vill. Exempel:
- Butikskassa
- Demonstrationsenhet
- Försäljning
- Redovisning
- Manager

## <a name="how-to-configure-device-categories"></a>Så här konfigurerar du enhetsinställningar

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>Steg 1: Skapa enhetskategorier på Intune-bladet på Azure-portalen
1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering**.
2. På bladet **Enhetsregistrering** väljer du **Enhetskategorier**.
3. På sidan **Enhetskategorier** väljer du **Skapa** för att lägga till en ny kategori.
4. På bladet **Skapa enhetskategori** anger du ett **Namn** på den nya kategorin och en valfri **Beskrivning**.
5. När du är klar väljer du **Skapa**. Du kan se den nya kategorin i listan över kategorier.

Du kommer att använda enhetskategorinamnet när du skapar Azure Active Directory-säkerhetsgrupper (Azure AD) i steg 2.

### <a name="step-2-create-azure-active-directory-security-groups"></a>Steg 2: Skapa Azure Active Directory-säkerhetsgrupper
I det här steget kommer du att skapa dynamiska grupper i Azure Portal baserat på enhetskategori och enhetskategorinamn.

Se [Using attributes to create advanced rules](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) (Använda attribut för att skapa avancerade regler) i Azure AD-dokumentationen för att fortsätta.

Använd informationen i det här avsnittet för att skapa en enhetsgrupp med en avancerad regel med hjälp av **deviceCategory**-attributet. Till exempel: **device.deviceCategory - eq** ”*enhetskategorinamnet som du fick från Azure Portal*”.

När du har konfigurerat enhetsgrupper och användarna då registrerar sina enheter får de se en lista med de kategorier som du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den Active Directory-säkerhetsgrupp som motsvarar den kategori som har valts.

### <a name="view-the-categories-of-devices-that-you-manage"></a>Visa kategorier av enheter som du hanterar

1.  I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enheter**.

2.  Under **Hantera** väljer du **Alla enheter**.

3.  I listan med enheter granskar du kolumnen **Enhetskategori**.

Om kolumnen **Enhetskategori** inte visas väljer du **Kolumner**. Välj **Enhetskategori** i listan och välj sedan **Använd**.

### <a name="change-the-category-of-a-device"></a>Ändra kategori för en enhet

1. I [Intune på Azure-portalen](https://aka.ms/intuneportal) väljer du **Enheter**.
2. På bladet **Enheter** under avsnittet **Hantera** väljer du **Alla enheter**.
3. Välj önskad enhet i listan över enheter. På bladet med enhetsegenskaper väljer du **Egenskaper** under avsnittet **Hantera**.
4. På nästa blad kan du ändra **Enhetskategori** för den valda enheten till ett kategorinamn som du tidigare har konfigurerat.

## <a name="after-you-configure-device-groups"></a>När du har konfigurerat enhetsgrupper

När användare av iOS- och Android-enheter registrerar sin enhet, måste de välja en kategori från listan över kategorier som du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den Intune-enhetsgruppen eller Active Directory-säkerhetsgruppen som motsvarar den kategori som har valts.

Windows-användare bör använda den nya webbplatsen för företagsportalen och välja en kategori där.

Oavsett vilken plattform användarna har kan de alltid gå till portal.manage.microsoft.com efter att enheten registrerats. Få användaren att gå till **Mina enheter** på företagsportalens webbplats. Användaren kan välja en registrerad enhet som visas på sidan och sedan välja en kategori.

Efter att du har valt en kategori, läggs enheten automatiskt till i motsvarande grupp som du har skapat. Om en enhet redan har registrerats innan du konfigurerar kategorier, ser användaren ett meddelande om enheten på Företagsportalen. Användaren får veta att hon eller han ska välja en kategori nästa gång öppnar företagsportalsappen på iOS eller Android.

## <a name="further-information"></a>Ytterligare information
- Du kan redigera en enhetskategori i Azure-Portal, men du måste manuellt uppdatera alla Azure AD-säkerhetsgrupper som refererar till den här kategorin.

- Om du tar bort en kategori kommer enheter tilldelade till den att visa kategorinamnet **Otilldelad**.
