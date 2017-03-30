---
title: Hantera enheter med Intune
titleSuffix: Intune Azure preview
description: "Intune Azure Preview: Lär dig hur du visar de enheter som du hanterar med Intune och utför olika åtgärder på dem."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 671d862c8d9a98e02f33d96cf6ceba712e740dec
ms.openlocfilehash: 8a43e1646476696b978a7f8a3e92f920606a698b
ms.lasthandoff: 03/17/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>Vad är enhetshantering i Microsoft Intune? 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Arbetsbelastningen **Enheter** ger dig insikter om de enheter du hanterar och låter dig utföra fjärråtgärder på dessa enheter. För att få åtkomst till arbetsbelastningen:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.

Välj nu något av följande:

- **Översikt** – Hämta information om enheter som du har registrerat och operativsystemen som körs för varje enhet.
- **Hantera** – Välj **Alla enheter** för att visa en lista över alla enheter som du hanterar.
    Välj en av enheterna i listan för att öppna bladet <*enhetsnamn*> **Översikt** där du kan välja:
    - **Översikt** – Visa allmän information om enheten inklusive information om dess namn, ägare, om det är en BYOD-enhet, när den senast var incheckad, med mera. 
                
    - **Maskinvara** – Visa mer detaljerad information om enheten, inklusive dess lediga lagringsutrymme, modell, tillverkare och mycket annat.
    ![Maskinvaruinventering för hanterade enheter](./media/hardware-inventory.png)
    - **Identifierade program** – Visar en lista över alla appar som Intune hittar installerade på enheten.
    ![Identifierad programnod](./media/detected-applications.png)
- **Övervaka** Välj **Enhetsåtgärder** för att se en lista över enhetsåtgärder som har utförts på enheter som du hanterar och det aktuella tillståndet för dessa åtgärder.
![Övervaka enhetsåtgärder](./media/monitor-device-actions.png)
- **Hjälp och Support** – Visar länkar till dokumentationen för felsökning och support.

## <a name="available-device-actions"></a>Tillgängliga enhetsåtgärder

Dessutom kan du utföra följande fjärråtgärder på enheten (alla åtgärderna stöds inte av alla enhetsplattformar):

### <a name="remove-company-data"></a>**Ta bort företagsdata**
Tar endast bort företagsdata som hanteras av Intune. Personliga data tas inte bort från enheten. Enheten kommer inte längre att hanteras av Intune och kommer inte längre att kunna komma åt företagets resurser (stöds inte för Windows-enheter som är anslutna till Azure Active Directory).

### <a name="factory-reset"></a>**Fabriksåterställning**
Återställer enheten till standardinställningarna. Enheten kommer inte längre att hanteras av Intune och både företagsdata och personliga data tas bort. Du kan inte ångra den här åtgärden.

### <a name="remote-lock"></a>**Fjärrlåsning**
Låser enheten. Enhetens ägare måste använda sitt lösenord för att låsa upp den. Du kan endast fjärrlåsa en enhet som har en PIN-kod eller angett lösenord.

### <a name="reset-passcode"></a>**Återställ lösenord**
Genererar ett nytt lösenord för enheten som visas på bladet <*enhetsnamn*> **Översikt**.

### <a name="bypass-activation-lock"></a>**Kringgå aktiveringslås**
Detta tar bort aktiveringslåset från en iOS-enhet utan användarens Apple-ID och lösenord. När du har kringgått aktiveringslåset aktiverar enheten aktiveringslåset igen när appen Hitta Min iPhone startar. Kringgå bara aktiveringslåset om du har fysisk åtkomst till enheten.

### <a name="lost-mode"></a>**Borttappat läge**
Om en iOS-enhet har blivit tappats bort eller blivit stulen kan du aktivera borttappat läge. Det gör att du kan ange ett meddelande och ett telefonnummer som ska visas på enhetens låsskärm. Gör så här:
1.    Välj **Mer** > **Borttappat läge**på en iOS-enhets egenskapsblad.
2.    Aktivera borttappat läge på bladet **Borttappat läge** och ange det meddelandet som ska visas och, vilket är valfritt, ett telefonnummer.
3.    Klicka på **OK**.
När du aktiverar borttappat läge blockerar du all användning av enheten. Slutanvändaren kan inte öppna enheten förrän du inaktiverar borttappat läge. Borttappat läge är aktiverat, men du kan använda åtgärden **Leta upp enheten** om du vill veta var enheten finns.
För att kunna använda Borttappat läge måste enheten vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge.

### <a name="locate-device"></a>**Hitta enhet**
Använd den här fjärråtgärder om du vill visa platsen för en förlorad eller stulen iOS-enhet på en karta. Enheten måste vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge. Innan du använder den här åtgärden måste enheten har placerats i borttappat läge.
1.    Välj **Mer** > **Hitta enhet** på en iOS-enhets egenskapsblad.
2.    När enheten har hittats visas dess plats visas på bladet **Hitta enhet**. 
    ![Hitta enhetsblad](./media/locate-device.png)

### <a name="restart"></a>**Starta om**
Gör så att enheten startas om. Enhetens ägare meddelas inte automatiskt om omstarten, och kan därför förlora arbete.


## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Information om säkerhet och sekretess för åtgärderna för borttappat läge och hitta enhet
- Ingen platsinformation för enheten skickas till Intune förrän du har aktiverat den här åtgärden.
- När du använder åtgärden Hitta enhet skickas enhetens latitud- och longitudkoordinater till Intune och visas i Azure Portal.
- Data lagras i 24 timmar och tas sedan bort. Du kan inte ta bort platsdata manuellt.
- Platsinformationen krypteras både under lagring och vid överföring.
- När du konfigurerar borttappat läge, rekommenderar vi att det meddelande du skriver och som visas på låsskärmen innehåller information så att enhetens plats kan fastställas.

