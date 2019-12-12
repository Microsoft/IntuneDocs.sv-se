---
title: Lägg till program för Windows-datorer som kör Intune-klientprogramvaran
titleSuffix: Microsoft Intune
description: I det här avsnittet kan du läsa om hur du lägger till appar för Windows-datorer i Intune innan du distribuerar dem.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/29/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23868303d598be1bc2e45f0852edfd3cf8338ab3
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509156"
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Lägg till program för Windows-datorer som kör Intune-klientprogramvaran

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Använd informationen i det här avsnittet för att lära dig hur du lägger till appar i Intune innan du distribuerar dem.

> [!IMPORTANT]
> Informationen i det här avsnittet hjälper dig att lägga till program för Windows-datorer som du hanterar med Intune-klientprogramvaran. Om du vill lägga till appar för registrerade Windows-datorer och andra mobila enheter kan du läsa [Lägga till appar till Microsoft Intune](../apps/apps-add.md).

För att du ska kunna installera appar på datorer måste apparna kunna installeras i obevakat läge, utan någon användarinteraktion. Annars misslyckas installationen.

## <a name="additional-security-settings-for-windows-installer"></a>Ytterligare säkerhetsinställningar för Windows Installer
Du kan tillåta användarna att styra appinstallationer. Om den här inställningen är aktiverad tillåts installationer som i annat fall skulle stoppats på grund av en säkerhetsöverträdelse. Du kan ange att Windows Installer ska använda förhöjd behörighet när program installeras i ett system. Du kan också ange att WIP-objekt (Windows Information Protection) ska indexeras och att deras metadata ska lagras på en okrypterad plats. När principen är inaktiverad indexeras inte Windows informationsskyddade objekt och resultaten visas inte i Cortana eller Utforskaren. Funktionerna för dessa alternativ är inaktiverade som standard. 

## <a name="add-the-app"></a>Lägg till appen
Använd Intune-programvaruutgivaren för att konfigurera egenskaper för appen och överföra den till molnlagringsutrymmet på följande sätt.

1. Gå till [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) och välj **Appar** &gt; **Lägg till appar** så startas Intune programvaruutgivare.

   > [!TIP]
   > Du kan behöva ange ditt användarnamn och lösenord för Intune innan utgivaren startas.

2. Välj **Programinstallation** under **Hur ska enheterna få tillgång till den här programvaran** på sidan **Programvaruinstallation** och gör sedan följande:

   - **Välj typ av programinstallationsfil**. Detta anger vilken typ av programvara som du vill distribuera. För en Windows-dator väljer du **Windows Installer**.
   - **Ange platsen för programvarans installationsfiler**. Ange platsen för installationsfilerna, eller välj **Bläddra** för att välja platsen i en lista.
   - **Inkludera ytterligare filer och undermappar från samma mapp**. Vissa program som använder Windows Installer kräver stödfiler. Dessa måste finnas i samma mapp som installationsfilen. Välj det här alternativet om du vill distribuera dessa stödfiler.

   Om du till exempel vill publicera en app med namnet Application.msi i Intune skulle sidan se ut så här: ![Sidan Programvaruinstallation i programvaruutgivaren](./media/add-apps-for-windows-pcs-in-microsoft-intune/publisher-for-pc.png)

   Den här installationstypen använder en del av ditt molnlagringsutrymme.

3. På sidan **Programvarubeskrivning** konfigurerar du följande.

   > [!NOTE]
   > En del av dessa värden kan anges automatiskt eller visas inte, beroende på den installationsfil som används.

   - **Utgivare**. Ange namnet på appens utgivare.
   - **Namn**. Ange namnet på appen så som det ska visas i företagsportalen.<br />Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
   - **Beskrivning**. Ange en beskrivning för appen. Detta visas för användare i företagsportalen.
   - **Webbadress (URL) för programinformation** (valfritt). Ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användare i företagsportalen.
   - **Sekretesswebbadress** (valfritt). Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användare i företagsportalen.
   - **Kategori** (valfritt). Välj någon av de inbyggda appkategorierna. Det gör det enklare för användarna att hitta appen när de söker i företagsportalen.
   - **Ikon** (valfritt). Överför en ikon som ska kopplas till appen. Den här ikonen visas med appen när användare söker i företagsportalen.

4. På sidan **Krav** väljer du de krav som måste uppfyllas innan appen kan installeras. Välj mellan:

   - **Arkitektur**. Välj om den här appen kan installeras på 32-bitars eller 64-bitars operativsystem, eller båda.
   - **Operativsystem**. Välj det lägsta operativsystem där den här appen kan installeras.

5. På sidan **Identifieringsregler** kan du konfigurera regler för att identifiera om den app som du konfigurerar redan är installerad på en dator. Eller så kan du använda standardidentifieringsreglerna för att automatiskt skriva över eventuella tidigare installerade versioner av appen. Det här alternativet är för Windows Installer (endast .exe-filer).

   Reglerna du kan konfigurera är:
   - **Filen finns**. Ange sökvägen till filen som du vill identifiera. Du kan söka under **%ProgramFiles%** (som söker i **Program Files**\&lt;sökväg&gt; och **Program Files (x86)** \&lt;sökväg&gt;) på datorn eller **%SystemDrive%** (som söker från datorns rotenhet, normalt enhet C).
   - **MSI produktkod finns**. Välj **Bläddra** för att välja den Windows Installer-fil (.msi) som du vill identifiera.
   - <strong>Registernyckeln finns</strong>. Ange en registernyckel som börjar med <strong>HKEY_LOCAL_MACHINE\</strong>. Både 32-bitars och 64-bitars registersökvägar genomsöks. Om den nyckel som du angav finns på någon av platserna uppfylls identifieringsregeln.

   Om appen uppfyller någon av de regler som du har konfigurerat kommer den inte att installeras.

6. Endast för **Windows Installer**-filtypen (.msi och .exe): På sidan **Kommandoradsargument** väljer du om du vill ange valfria kommandoradsargument för installationsprogrammet.
   Följande parametrar läggs till automatiskt av Intune:
   - För EXE-filer läggs **/install** till.
   - För MSI-filer läggs **/quiet** till.
   Observera att dessa alternativ bara fungerar om den som skapat appaketet har aktiverat funktioner för detta.

7. Endast för **Windows Installer**-filtypen (endast .exe): På sidan **Returkoder** kan du lägga till nya felkoder som tolkas av Intune när appen installeras på en hanterad Windows-dator.

   Som standard använder Intune returkoder som är branschstandard för att rapportera fel eller framgång för installation av ett appaket: **0** (Klart) eller **3010** (Lyckas med omstart). Du kan också lägga till egna returkoder i listan. Om du anger en lista över returkoder och appinstallationen returnerar en kod som inte finns i listan tolkas det som ett fel.

8. På sidan **Sammanfattning** läser du igenom den information som du har angivit. När du är klar väljer du **Överför**.

9. Välj **Stäng** för att slutföra.

Appen visas i noden **Appar** på arbetsytan **Appar**.

## <a name="next-steps"></a>Nästa steg

När du har skapat en app är nästa steg att distribuera den. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](../apps/apps-deploy.md).

Fler tips och råd om hur du distribuerar programvara till Windows-datorer finns i blogginlägget [Support Tip: Best Practices for Intune Software Distribution to PC’s](https://support.microsoft.com/en-US/help/2583929) (Supporttips: Metodtips för distribution av Intune-programvara till datorer).
