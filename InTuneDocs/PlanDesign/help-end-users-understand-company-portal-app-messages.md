---
# required metadata

title: Hjälpa slutanvändarna att förstå meddelanden i företagsportalappen | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3df993aa-48c5-4799-b68d-c85fe4f7b02c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hjälpa slutanvändarna att förstå meddelanden i företagsportalappen

Följande information gäller endast på Android 6.0 och senare enheter. Under enhetsregistrering ser slutanvändarna två meddelanden, som visas under registreringsprocessen:

- Tillåt att företagsportalen kan ringa och hantera telefonsamtal?
- Tillåt att företagsportalen kommer åt foton, media och filer på enheten?

Se följande stycken för information om dessa meddelanden och för information som du kan dela med slutanvändare om dem.

## Tillåt att företagsportalen kan ringa och hantera telefonsamtal?

### Meddelandetext och var den visas
Meddelandetexten är **Tillåt att företagsportalen kan ringa och hantera telefonsamtal?** och visas när användare loggar in på företagsportalen för första gången för att börja registrera sin enhet.

### Vad meddelandet betyder
Meddelandet uppmanar användare att låta deras telefonnummer och IMEI skickas till Intune-tjänsten och att de visas i administrationskonsolen på sidan Maskinvara.

> [!NOTE]
> **Företagsportalappen ringer eller hanterar aldrig telefonsamtal!** Meddelandetexten styrs av Google och kan inte ändras.

Öppna sidan **Maskinvara** genom att gå till **Grupper** > **Alla mobila enheter** > **Enheter**. Välj användarens enhet och gå till **Visa egenskaper** > **Maskinvara**.

### Vad händer om användarna tillåter eller nekar åtkomst
Om användarna tillåter åtkomst visas enhetens telefonnummer och IMEI på sidan Maskinvara i administrationskonsolen.

Om användarna nekar åtkomst kan de fortsätta att använda företagsportalappen och registrera sina enheter, men användarnas enhetstelefonnummer och IMEI är tomma på sidan Maskinvara i administrationskonsolen. Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen.

Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren loggar in på företagsportalappen efter registreringen.</br></br>Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Telefon** och aktiverar sedan behörigheten.

### Vart ska användarna vända sig för mer information
Steg 5 i [Registrera en Android-enhet i Intune](/Intune/EndUser/enroll-your-device-in-intune-android)

## Tillåt att företagsportalen kommer åt foton, media och filer på enheten?

### Meddelandetext och var den visas
Meddelandetexten är **Tillåt att företagsportalen kommer åt foton, media och filer på enheten?** och visas när användarna trycker på **Skicka Data** för att skicka dataloggar till sin IT-administratör.

### Vad meddelandet betyder
Meddelandet uppmanar användarna att låta deras enheter skriva dataloggar till enhetens SD-kort och tillåta att loggarna flyttas med hjälp av en USB-kabel.   

> [!NOTE]
> **Företagsportalappen bereder sig aldrig åtkomst till användarnas foton, media och filer!** Meddelandetexten styrs av Google och kan inte ändras.

### Vad händer om användarna tillåter eller nekar åtkomst
Om användarna tillåter det, kopieras loggfilerna till SD-kortet.

Om användarna nekar åtkomst kan de fortfarande skicka loggar, men loggarna kopieras inte till enhetens SD-kort.

Den andra gången användarna loggar in på företagsportalappen efter att de nekat åtkomst visas kryssrutan **Fråga inte igen** som de kan markera så att meddelandet inte visas igen. Om användare tillåter men senare nekar åtkomst visas meddelandet nästa gång användaren försöker skicka loggar. Om användare senare bestämmer sig för att tillåta åtkomst kan de gå till **Inställningar** > **Appar** > **Företagsportal** > **Behörigheter** > **Lagring** och aktiverar sedan behörigheten.

### Vart ska användarna vända sig för mer information
[Skicka loggar med diagnostikdata till din IT-administratör med e-post](/Intune/EndUser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android)


### Se även
[Vad du ska berätta för slutanvändare om att använda Intune](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune.md)


<!--HONumber=May16_HO2-->


