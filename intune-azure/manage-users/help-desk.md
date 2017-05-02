---
title: "Supportavdelningens felsökningsportal | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e0ecc775f70703574c4e1adf0f0aa204f2745b72
ms.openlocfilehash: 723830f686991fe13de13f75c6a5d1bc84e6920b
ms.lasthandoff: 04/20/2017

---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Hjälpa användarna med felsökningsportalen i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Med felsökningsportalen kan supportansvariga och Intune-administratörer se användarna och deras enheter, samt utföra åtgärder för att lösa tekniska problem i Intune.

## <a name="add-help-desk-operators"></a>Lägga till supportansvariga
En Intune-administratör kan tilldela supportansvariga behörighet för användarna. Supportavdelningen kan sedan se Intune-portalen, men de kan inte visa eller utföra administrativa åtgärder utanför felsökningens arbetsbelastning.

1. Som Intune-administratör kan du logga in på [Azure-portalen](https:portal.azure.com), välja **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. I det vänstra navigeringsbladet väljer du **Intune-roller**.
3. I arbetsbelastningen **Intune-roller** väljer du **Supportansvarig** och sedan **Tilldela**.
4. Skriv ett **Namn på tilldelning** (obligatoriskt), en **Tilldelningsbeskrivning** (valfritt) och tilldela sedan **Medlemmar (grupper)** och **Omfång (grupper)**.
5. Medlemmar i rollen som supportansvarig kan nu använda felsökningsportalen.

Mer information om Intune-roller finns i [Intune-roller (RBAC)](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control).

## <a name="access-the-troubleshooting-portal"></a>Åtkomst till felsökningsportalen

Supportpersonal och Intune-administratörer kan få åtkomst till felsökningsportalen på två sätt:
- I [Azure-portalen](https:portal.azure.com)väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. I det vänstra navigeringsbladet väljer du sedan **Felsök**. Andra arbetsbelastningar syns i det vänstra navigeringsbladet, men de är inte tillgängliga.
![Skärmbild av Intunes arbetsbelastning för felsökning med länken Välj användare](media/help-desk-user.png)
- Öppna [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) i en webbläsare. Det är endast felsökningsportalen som visas.

## <a name="use-the-troubleshooting-portal"></a>Använda felsökningsportalen

I felsökningsportalen kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter. Felsökningsportalen visar följande information om Intune-användare och enheter:
- Kontoinformation om användare
- Gruppmedlemskap för användare
- Information om enhet

Supportavdelningen kan även utföra fjärråtgärder på enheter, som t.ex. **Fjärrlåsning**.

