---
title: "Intune-roller (RBAC) för Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur RBAC kan kontrollera vem som ska kunna utföra åtgärder och göra ändringar."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 9a6dfde1d02313e51f59d4fd101a175f347f6cec
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="intune-roles-rbac-for-microsoft-intune"></a>Intune-roller (RBAC) för Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Enkel uttryckt så hjälper Intune-**roller** (eller RBAC) dig att kontrollera vem som kan utföra olika Intune-åtgärder och vem dessa åtgärder gäller för. Du kan antingen använda de inbyggda roller täcker vissa vanliga scenarier för Intune eller du kan skapa egna roller.

En roll definieras av:

- **Definition** – Namnet på en roll och de behörigheter som den konfigurerar.
- **Medlemmar** – Den användare eller grupp av användare som kommer att ges dessa behörigheter.
- **Omfång** – De användare eller enheter som en angiven person (medlemmen) kan hantera.
- **Tilldelning** – När definition, medlemmar och omfång har konfigurerats är rollen tilldelad.

## <a name="built-in-roles"></a>Inbyggda roller

Följande roller är inbyggda i Intune och du kan antingen anpassa dessa roller eller tilldela dem till grupper utan någon ytterligare konfiguration.

- **Intune-administratör** – Har fullständiga behörigheter för alla Intune-åtgärder.
- **Programhanterare** – Hantera och distribuera program och profiler.
- **Konfigurationsprinciphanterare** – Hantera och distribuera konfigurationsinställningar och profiler.
- **Supportoperatör** – Utföra fjärråtgärder och visa användar- och enhetsinformation.
- **Skrivskyddad operatör** – Visa information i Intune Portal utan möjlighet att göra ändringar.


## <a name="custom-roles"></a>Anpassade roller

Om ingen av de inbyggda rollerna passar dina behov kan du skapa din egen roll genom att välja inställningar som sträcker sig över flera av funktionerna i Intune. Du kan se en lista över de tillgängliga inställningarna senare i det här avsnittet.

### <a name="example"></a>Exempel

Du anställer en ny IT-administratör som kommer att ansvara för distribution och hantering av appar till användare på ert Londonkontor. Användarna är i en Azure AD-grupp med namnet **London**. Du vill säkerställa att IT-administratören inte kan distribuera appar till användare på något annat kontor. Du vidtar följande åtgärder:

- Tilldela den inbyggda rollen **Programhanterare** med följande egenskaper:
    - **Medlemmar** – Välj en grupp som innehåller den IT-administratör som ska distribuera appar
    - **Omfång** – Välj Azure AD-gruppen **London**.

    >[!IMPORTANT]
    >För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
    >- **Global AAD-administratör**
    >- **Intune-tjänstadministratör**

### <a name="how-to-create-a-custom-role"></a>Skapa en anpassad roll

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Intune-roller** på bladet **Intune**.
![Åtkomstkontroll arbetsbelastning](./media/axxess-control.png)
1. På bladet **Roller** i **Åtkomstkontroll** arbetsbelastning väljer du **Lägg till anpassad**.
2. På bladet **Lägg till anpassad roll** anger du namn och beskrivning för den nya rollen och klickar sedan på **Behörigheter**.
3. På bladet **Behörigheter** väljer du de behörigheter som du vill använda med den här rollen. Använd listan över referenser för anpassade rollinställningar i detta avsnitt som hjälp.
4. När du är klar klickar du på **OK**.
5. På bladet **Lägg till anpassad roll** klickar du på **Skapa**.

Den nya rollen visas i listan på bladet **Roller**.

## <a name="how-to-assign-a-role"></a>Så här tilldelar du en roll

1. På bladet **Roller** i **Åtkomstkontroll** arbetsbelastning väljer du den inbyggda eller anpassade roll som du vill tilldela.
2. På bladet <*rollnamn*> – **Egenskaper** väljer du **Hantera** > **Tilldelningar**. På det här bladet kan du även redigera eller ta bort befintliga roller.
3. Välj **Tilldela** på nästa blad.
4. På bladet **Rolltilldelningar** anger du ett **Namn** och en valfri **Beskrivning** för tilldelningen och väljer sedan följande:
    - **Medlemmar** – Välj en grupp som innehåller den användare som du vill ge behörighet.
    - **Omfång** – Välj en grupp som innehåller de användare som ovanstående medlem ska kunna hantera.
5. När du är klar klickar du på **OK**.

Den nya tilldelningen visas i listan över tilldelningar.

## <a name="custom-role-settings-reference"></a>Referenser för anpassade rollinställningar

När du skapar en anpassad roll kan konfigurera du en eller fler av följande inställningar:

### <a name="device-configurations"></a>Enhetskonfigurationer

|||
|-|-|
|**Tilldela**|Tilldela enhetsprofiler till grupper.|
|**Skapa**|Skapa enhetsprofiler.|
|**Ta bort**|Ta bort enhetsprofiler.|
|**Läsa**|Visa information om enhetsprofiler och deras egenskaper.|
|**Uppdatera**|Uppdatera befintliga enhetsprofiler.|

### <a name="managed-apps"></a>Hanterade appar

|||
|-|-|
|**Tilldela**|Tilldela hanterade appar till grupper.|
|**Skapa**|Lägg till nya hanterade appar i Intune.|
|**Ta bort**|Ta bort hanterade appar.|
|**Läsa**|Visa information om hanterade appar och deras egenskaper.|
|**Uppdatera**|Uppdatera befintliga hanterade appar.|
|**Rensning**|Rensa hanterade appar från enheter.|

### <a name="managed-devices"></a>Hanterade enheter

|||
|-|-|
|**Ta bort**|Ta bort hanterade enheter från Intune.|
|**Läsa**|Visa information om hanterade enheter i Intune Portal.|
|**Uppdatera**|Uppdatera information om hanterade enheter.|

### <a name="mobile-apps"></a>Mobilappar

|||
|-|-|
|**Tilldela**|Tilldela mobilappar till grupper.|
|**Skapa**|Lägg till nya mobilappar i Intune.|
|**Ta bort**|Radera mobilappar.|
|**Läsa**|Visa information om mobilappar och deras egenskaper.|
|**Uppdatera**|Uppdatera befintliga mobilappar.|

### <a name="organization"></a>Organisation

|||
|-|-|
|**Läsa**|Visa information om klientinställningar.|
|**Uppdatera**|Uppdatera klientinställningar.|

### <a name="remote-tasks"></a>Fjärråtgärder

|||
|-|-|
|**Kringgå aktiveringslås**|Ta bort aktiveringslås från en iOS-enhet utan användarens Apple-ID och lösenord. |
|**Inaktivera borttappat läge**|Inaktivera borttappat läge. Borttappat läge gör att du kan ange ett meddelande och ett telefonnummer som ska visas på enhetens låsskärm.|
|**Aktivera borttappat läge**|Aktivera borttappat läge. Borttappat läge gör att du kan ange ett meddelande och ett telefonnummer som ska visas på enhetens låsskärm.|
|**Lokalisera enhet**|-|
|**Starta om nu**|Gör så att enheten startas om.|
|**Fjärrlåsning**|Låser en enhet. Enhetens ägare måste använda sitt lösenord för att låsa upp den.|
|**Återställ lösenord**|Skapar ett nytt lösenord för enheten som ska visas på <device name> översiktsblad.|
|**Pensionera**|Tar endast bort företagsdata som hanteras av Intune. Personliga data tas inte bort från enheten.|
|**Rensning**|Återställer enheten till standardinställningarna.|



### <a name="telecom-expenses"></a>Telekomkostnader

|||
|-|-|
|**Läsa**|Visa information om inställningar för kostnadsuppföljning av telekommunikation (TEM).|
|**Uppdatera**|Uppdatera inställningar för kostnadsuppföljning av telekommunikation (TEM).|

### <a name="terms-and-conditions"></a>Villkor

|||
|-|-|
|**Tilldela**|Tilldela användarvillkor för grupper.|
|**Skapa**|Skapa inställningar för användarvillkor.|
|**Ta bort**|Ta bort inställningar för användarvillkor.|
|**Läsa**|Visa information om inställningar för användarvillkor i Intune Portal.|
|**Uppdatera**|Uppdatera befintliga inställningar för användarvillkor.|
