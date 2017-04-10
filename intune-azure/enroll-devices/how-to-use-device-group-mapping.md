---
title: "Så här använder du enhetskategorier i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur du använder enhetskategorier som användare kan välja när de registrerar sina enheter i Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: c635ced382074f7f45254fb219b58f54b56abb8e
ms.lasthandoff: 02/18/2017


---

# <a name="map-device-groups"></a>Mappa enhetsgrupper


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd Microsoft Intune-enhetskategorier för att automatiskt lägga till enheter i grupper baserat på kategorier som du definierar för att göra det enklare att hantera dessa enheter.

Enhetskategorier använder följande arbetsflöde:
1.    Skapa kategorier som användare väljer från när de registrerar sina enheter
4.    När slutanvändare registrerar sina enheter måste de välja en kategori från de listan över kategorier som du har konfigurerat. Om en enhet redan har registrerats kommer användaren uppmanas att välja en kategori nästa gång de öppnar appen i företagsportalen.


Du kan skapa vilken typ av enhetskategori som du vill, till exempel:
- Butiksenhet
- Demonstrationsenhet
- Försäljning
- Redovisning
- Manager

## <a name="how-to-configure-device-categories"></a>Så här konfigurerar du enhetsinställningar

### <a name="step-1---create-device-categories-in-the-intune-blade-of-the-azure-portal"></a>Steg ett – Skapa enhetskategorier i Intune-bladet på Azure-portalen
1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. På **Intune**-bladet väljer du **Registrera enheter**.
3. I bladet **Registrering** väljer du **Enhetskategorier**.
4. På sidan **Enhetskategorier** väljer du **Skapa** för att lägga till en ny kategori.
5. I nästa blad anger du ett **Namn** för den nya kategorin och en valfri **Beskrivning**.
6. Klicka på **Skapa** när du är klar. Du kommer att se den kategori som du just har skapat i listan över kategorier.

Du kommer att använda enhetskategorinamnet när du skapar Azure Active Directory-säkerhetsgrupper i steg två.

### <a name="step-2---create-azure-active-directory-security-groups"></a>Steg två – Skapa Azure Active Directory-säkerhetsgrupper
I det här steget kommer du att skapa dynamiska grupper i Azure Portal baserat på enhetskategori och enhetskategorinamn.

Se avsnittet [Using attributes to create advanced rules](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects) (Använda attribut för att skapa avancerade regler) i Azure Active Directory-dokumentationen för att fortsätta. 

Använd informationen i det här avsnittet för att skapa en enhetsgrupp med en avancerad regel med hjälp av **deviceCategory**-attributet. Till exempel (**device.deviceCategory -eq** "*<the device category name you got from the Intune portal>*")

När du har konfigurerat enhetsgrupper och användarna då registrerar sina enheter får de se en lista med de kategorier som du har konfigurerat. När användaren har valt en kategori och slutfört registreringen läggs enheten till i den Active Directory-säkerhetsgrupp som motsvarar den kategori som har valts.

### <a name="how-to-view-the-categories-of-devices-you-manage"></a>Så här visar du kategorier av enheter som du hanterar

1.    På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Enheter och grupper** i Intune-bladet på Azure-portalen.

3.    Under **Hantera** klickar du på **Alla enheter**.

4.    I listan över enheter utforskar du kolumnen **Kategori**.

Om **Kategori**-kolumnen inte visas klickar du på **Kolumner**, väljer **Kategori** från listan och klickar sedan på **Tillämpa**.

### <a name="to-change-the-category-of-a-device"></a>Ändra kategori för en enhet

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. På **Intune**-bladet väljer du **Enheter och grupper**.
4. På bladet **Enheter och grupper** väljer du **Hantera** > **Alla enheter**.
5. I listan över enheter väljer du den enhet som du önskar och väljer sedan, på enhetens egenskapsblad, **Hantera** > **Egenskaper**.
6. På nästa blad kan du ändra **Enhetskategori** för den valda enheten till ett kategorinamn som du tidigare har konfigurerat.



## <a name="further-information"></a>Ytterligare information
- Du kan redigera en enhetskategori i Azure-Portal, men om du gör detta måste du manuellt uppdatera alla Azure Active Directory-säkerhetsgrupper som refererar till den här kategorin.

- Om du tar bort en kategori kommer alla enheter som var tilldelade den att visa kategorinamnet **Otilldelad**.



