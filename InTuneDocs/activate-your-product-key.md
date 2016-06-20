---
# required metadata

title: Aktivera din produktnyckel | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 844c2ca8-2721-4f72-b1dd-be9b1da1f220

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Aktivera din produktnyckel
Du kan använda en produktnyckel för att lösa in en prenumeration eller lägga till användare till en befintlig prenumeration. En produktnyckel är en unik, 25 tecken lång alfanumerisk kod som krävs för att lösa in en prenumeration, komma åt onlinetjänster eller hämta programvara. Du kan köpa produktnycklar från en Microsoft-partner eller en återförsäljare.

## Lösa in produktnyckel
Lös in produktnyckeln genom att ange den 25 tecken långa koden.

-   Om du aktiverar en produktnyckel för [!INCLUDE[wit_firstref](./includes/wit_firstref_md.md)] går du [hit](https://account.manage.microsoft.com/commerce/productkeystart.aspx).

-   Om du aktiverar en produktnyckel för Enterprise Mobility Suite går du [hit](http://www.microsoft.com/ems/open).

> [!NOTE] Om du förlorar produktnyckeln kontaktar du partnern eller återförsäljaren du har handlat från.

## Hämta din System Center Configuration Manager-programvara
För att hämta programvaran för System Center Configuration Manager går du till [Volume Licensing Service Center](http://go.microsoft.com/fwlink/?LinkID=232300).

## Felsökning av problem när du skriver in produktnyckeln

|Felmeddelande|Lösning|
|-----------------|--------------|
|**Produktnyckeln som du skrev in är inte giltig. Försök att skriva in den igen** eller så är **den här produktnyckeln inte giltig. Skriv in en annan produktnyckel**.|Kontrollera noggrant siffror och tecken som du skriver in. Ibland kan man blanda ihop tecken och siffror, till exempel "O" och 0, "S" och 5, osv. Om problemet kvarstår bör du kontakta återförsäljaren som du har köpt produktnyckeln av.|
|**Du har redan skrivit in den här produktnyckeln. Skriv in en annan nyckel**.|Kontrollera att de produktnycklar du har angett inte redan har lagts till. Om problemet kvarstår bör du kontakta [supportavdelningen](http://go.microsoft.com/fwlink/?LinkID=394189).|
|**Den produktnyckel du har skrivit in är inte giltig längre. Skriv in en annan nyckel**.|Kontakta [supportavdelningen](http://go.microsoft.com/fwlink/?LinkID=394189).|
|**Du har skrivit in en produktnyckeln som redan används. Skriv in en annan produktnyckel**.|Du har skrivit in en produktnyckeln som redan har lösts in. Kontrollera att nyckeln har redan använts av dig eller någon annan i din organisation. Om nyckeln inte redan har använts, kontakta din återförsäljare där du har köpt produktnyckeln.|
|**Tyvärr kan vi inte bearbeta din begäran just nu. Vänta några minuter och försök igen**.|Om flera försök resulterar i samma felmeddelande under mer än 15 minuter bör du kontakta [supportavdelningen](http://go.microsoft.com/fwlink/?LinkID=394189).|
|**Den begärda prenumerationen är inte tillgänglig. En av följande orsaker kan ha orsakat detta: Erbjudandet är inte tillgänglig – tjänsten är inte tillgänglig i ditt land – det går inte att använda/välja samma utvärderingsversion två gånger. Kontakta Microsofts supportavdelning om problemet kvarstår**.|Kontakta [supportavdelningen](http://go.microsoft.com/fwlink/?LinkID=394189).|
|**Du har lagt till fler användarlicenser än vad det här erbjudandet tillåter. Det maximala värdet är 10000000 användarlicenser. Ta bort den här produktnyckeln och ange en som lägger till färre användarlicenser**.|Kontakta återförsäljaren eller partnern. Du har köpt fler licenser än vad som kan användas med det här kontot.|
|**Du måste vara global administratör eller faktureringsadministratör för att kunna lösa in en produktnyckel**.|Kontrollera att dina behörigheter har angetts som till faktureringsadministratör eller global administratör. Kontrollera detta genom att gå till administratörskonsolen, klicka på **Admin** &gt; **Inställningar**.|
|**Tyvärr kan vi inte skapa kontot just nu. Vänta några minuter och försök igen**.|Om problemet kvarstår bör du kontakta [supportavdelningen](http://go.microsoft.com/fwlink/?LinkID=394189).|
|**Tyvärr kan vi inte behandla din order**.|Klienten skapades men produktnycklarna har inte lösts in. Försök att lösa in dina produktnycklar igen via länken ovan. Om problemet kvarstår bör du kontakta [supportavdelningen](http://go.microsoft.com/fwlink/?LinkID=394189).|


<!--HONumber=Jun16_HO2-->


