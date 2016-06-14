---
# required metadata

title: Hantera licensavtal för Windows-datorprogram | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hantera licensavtal för Windows-datorprogram i Microsoft Intune
Med Microsoft Intune kan du lägga till och hantera licensinformation för programvara som köpts via Microsofts volymlicensavtal och för programvara från Microsoft eller andra leverantörer som har köpts på annat sätt. Du kan även sortera informationen i logiska grupper.

> [!IMPORTANT]
> Den här funktionen tillhandahålls enbart i informationssyfte och vi garanterar inte att uppgifterna stämmer. Lita inte på den för att säkerställa efterlevnad med Microsofts volymlicensavtal. Microsoft kommer inte att använda några data som samlas in för att undersöka potentiella överträdelser av eller uppfyllelse av licensavtal som du kan ha med oss.
> 
> Licenser som du lägger till i Intune påverkar inte ditt licensavtal eller rättigheter för att använda din programvara.  Om du till exempel tar bort ett licensavtalspar i Intune tar det inte bort eller upphäver licensavtal som finns mellan dig och Microsoft.

I arbetsytan **Licenser** i administrationskonsolen för Intune kan du:

-   Lägga till och redigera Microsofts volymlicensavtal

-   Lägga till och redigera andra licensavtal

-   Hantera licenser och grupper

-   Jämföra berättigandeinformationen som Intune hämtar från Volume Licensing Service Center (VLSC) med lagret för Microsoft-programvara som Intune identifierar på dina hanterade Windows-datorer.

Du kan även generera rapporter som visar installations- och licensantal för programvarutitlar. Licensrapporter kan hjälpa dig att bedöma ditt fullständiga licensläge för Microsofts mjukvaruprogram och mjukvaruprogramtitlar som inte kommer från Microsoft.

> [!TIP] Arbetsytan **Licenser** visas inte i administratörskonsolen förrän du hanterar minst en Windows-dator med Intune-klienten för Windows-datorer.

## Lägga till Microsofts volymlicensavtal
Intune-volymlicensavtal tillhandahåller licensinformation för programvara som köpts via Microsofts volymlicensavtal. Du kan lägga till Microsofts volymlicensavtal i Intune genom att tillhandahålla matchande par av avtalsnummer. Avtalet eller tillståndsnumret måste anpassas till rätt licens eller registreringsnummer. Avtalsnummerpar erhåller du när du köper dina licensavtal från [Volume Licensing Service Center (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842).

1.  I [Microsoft Intune adminstratörskonsolen](https://account.manage.microsoft.com/admin/default.aspx)klickar du på **Licenser**.

2.  På sidan **Lägg till avtal** under **Välj avtalstyp**väljer du **Volymlicensieringsavtal**.

3.  I avsnittet **Lägg till avtalsuppgifter** väljer du något av följande:

    -   **Överför en CSV-fil som innehåller avtalsuppgifter** – Klicka på Bläddra och välj den CSV-fil som du vill överföra.

        -   Filen kan innehålla antingen två eller tre kolumner; två för enbart avtalspar eller tre om du vill lägga till ett eget namn för varje avtalspar.

        -   Det totala antalet tecken i ett avtalsnummerpar får inte överstiga 16 ASCII tecken.

        -   Endast ASCII tecken stöds.

        -   Följande tecken är inte tillåtna i avtalsnamnet: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Mellanslag är tillåtna i namnet.

        -   Filnamnet får inte vara mer än 128 tecken långt.

        -   Filen måste innehålla minst ett avtalspar och får inte innehålla mer än 5.000 avtalspar.

        **Format för filen**

        Du kan skapa den här filen genom att lägga till avtalspar till ett vanligt textdokument med något av följande format, beroende på organisationstypen som du har registrerat hos VLSC. Ange ett avtalsnummerpar per rad.

        -   **Open Value-kunder:** *Avtalsnummer*, *upprepa avtalsnummer*, *avtalsnamn*

        -   **Open-kunder:** *Auktoriseringsnummer*, *relaterat licensnummer*, *avtalsnamn*

        -   **Select- och Enterprise-kunder:** *Avtalsnummer*, *relaterat registreringsnummer*, *avtalsnamn*

        **Lägg till avtal** formlen uppmanar dig att leta efter den här filen när du lägger till ett nytt avtal.

        Följande är ett exempel på .csv filinnehåll för en kund med öppna värden.

        `01-07001, 01-07001, Office agreements`

    -   **Lägg till avtalsuppgifter manuellt** – Ange följande information och ange sedan avtalsnummerparen i rutorna **Auktoriserings-/avtalsnummer** och **Licens-/registrerings-/kundnummer**. Efter att du fyllt i båda numren, klicka på **Lägg till par** ikonen för att spara dina nummer, och sedan eventuellt lägga till ett nytt par.

        -   **Avtalsnamn** – Ange ett unikt namn för avtalet.

            Avtalsnamnet får innehålla högst 256 tecken och får inte innehålla följande tecken: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Mellanslag är tillåtna i namnet.

        -   **Auktoriserings-/avtalsnummer** – Ange auktoriserings-/avtalsnummer för licensparet.

        -   **Licens-/registrerings-/kundnummer** – Ange licens-/registrerings-/kundnummer för licensparet.

        > [!NOTE] Om du lägger till flera avtalsnummerpar skapar Intune ett avtal med det namn som du anger, och alla par som du har lagt till kommer att bli en del av detta avtal.

    Du kan klicka på **+** för att lägga till ett till avtalsnummerpar eller **-** för att ta bort ett avtalsnummerpar som du har angett.

4.  I **Välj licensgrupp** området, välj en av följande:

    -   **Lägg till avtalen i gruppen Otilldelade avtal** – Välj det här om du inte vill lägga till de nya avtalen i en licensgrupp.

    -   **Lägg till avtalen i en ny licensgrupp** – Ange ett namn på den nya licensgruppen.

    -   **Lägg till avtalen i en befintlig licensgrupp** – I listan **Gruppnamn** väljer du den licensgrupp där du vill lägga till avtalen.

5.  Klicka på **OK**.

Vyn **Alla avtal** visas och Intune ansluter till Microsoft Volume Licensing Service Center för att bekräfta de avtalsnummerpar som du har angett.

Om du vill uppdatera volymlicensinformationen efter att du har lagt till licensavtal i Intune går du till sidan **Licensöversikt** och klickar på **Uppdatera nu**. Denna åtgärd hämtar den aktuella licensinformationen från [Microsoft volymlicens servicecenter (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT] Fram till dess att du uppdaterar volymlicensinformationen kan du se olika typer av information i avtalslistan och rättighetsinformationen på sidan **Avtalsöversikt**.

När du har uppdaterat volymlicensinformationen kan du jämföra licensinformationen med din upptäckta Microsoft-programvara i arbetsytan **Appar** arbetsområdet. Du kan också köra följande licensrapporter:

-   **Rapporter om licensköp** – Gör det möjligt att visa den licensierade programvaran i licensgrupper som du väljer så att du kan hitta luckor i täckningen.

-   **Licensinstallationsrapport** – Hjälper dig att avgöra om du har tillräcklig licensavtalstäckning.

> [!NOTE] Den **Produkttitel** som visas för alla Microsofts volymlicensavtal är **Inte tillgänglig**.

## Lägga till och redigera andra licensavtal
Du kan också lägga till andra typer av licensavtal i Intune utöver Microsofts volymlicensavtal. Dessa avtal kan omfatta mjukvaruprogram som inte är Microsofts eller mjukvaruprogram från Microsoft som köptes via en återförsäljare.

> [!IMPORTANT]
> Du måste ha minst en Windows-dator registrerad i Intune innan du kan lägga till ett avtal.  Dessutom måste minst en registrerad dator ha överfört ett licensierbart programvarupaket som du vill använda för att lägga till ett licensavtal.

### För att lägga till mjukvaruprogramavtal

1.  I [Microsoft Intune adminstratörskonsolen](https://account.manage.microsoft.com/admin/default.aspx)klickar du på **Licenser**.

2.  Klicka på **Lägg till avtal** i **Övriga mjukvaruprogramlicensavtal** sektionen.

3.  Välj **Övriga mjukprogramvarulicensavtal** i **Välj avtalstyp** sektionen på **Lägg till avtal** sidan.

4.  I **Lägg till avtalsdetaljer** området, specificera följande:

    -   **Agreement name** (krävs). Avtalsnamnet får innehålla högst 256 tecken och får inte innehålla följande tecken: **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ' " &lt; &gt; /**. Mellanslag är tillåtna i namnet.

    -   **Utgivare** (krävs). När du börjar skriva en utgivares namn, hämtar tjänsten alla utgivares namn som innehåller de bokstäver som du skriver. Till exempel, om du skriver "mjuk" kommer alla utgivarnamn som innehåller "mjuka" som en del av namnet, till exempel "Microsoft" och "Microsoft Research" att visas. Utgivarnamnen hämtas från Software Asset Catalog. Du måste välja utgivare innan du kan ange produkttiteln.

        > [!IMPORTANT]
        > Det företag som du vill lägga till kanske inte visas i listan. Du kan bara lägga till programvaruavtal för företag som redan finns i Software Asset Catalog. Microsoft lägger dock kontinuerligt till de mest populära programvarutitlarna. Om du vill skicka en begäran för att få ett företag tillagt på listan kan du göra detta på [UserVoice-webbplatsen för Intune](https://microsoftintune.uservoice.com/).

    -   **Produkttitel** (krävs). När du börjar skriva en utgivares namn, hämtar tjänsten alla utgivares namn som innehåller de bokstäver som du skriver. Du måste specificera en **Utgivare** innan du kan specificera en **Produkttitel**.

    -   **Licensräknare** (krävs). Ange antal köpta licenser.

    -   **Licensstartdatum**. Ange startdatum för licenstäckning.

    -   **Licensslutdatum**. Ange slutdatum för licenstäckning.

    -   **Avtalsdetaljer**. Du kan välja om du vill ange kontaktinformation, registreringsnycklar och annan information.

5.  I **Välj licensgrupp** området, välj en av följande:

    -   Välj **Lägg till avtalen till avtalsgruppen som ännu inte tilldelats** om du inte vill lägga till de nya avtalen i en ny eller befintlig licensgrupp. Du kan lägga till avtalen till användardefinierade licensgrupper när som helst.

    -   Välj **Lägg till avtalen till en ny avtalsgrupp** för att lägga till de nya avtalen i en ny licensgrupp. Du uppmanas att ange ett namn för den nya licensgruppen.

    -   Välj **Lägg till avtalen till en existerande licensgrupp** för att lägga till de nya avtalen i en ny licensgrupp. I **Gruppnamn** listan, välj den licensgrupp till vilken du vill lägga till avtalen.

6.  Klicka på **OK**.

**Alla avtal** listan visas.

## Hantera licensavtal
Avtal för mjukvaruprogram kan läggas till licensgrupper. Du kan använda licensgrupper för att organisera licensavtal i enheter som är logiska för din organisation. Dessutom kan du ta bort licensavtal som du har skapat tidigare.

|||
|-|-|
|Aktivitet|Information|
|Skapa en licensgrupp|På sidan **Översikt** i arbetsytan **Licenser** klickar du på **Skapa licensgrupp** på menyn **Aktiviteter** . **Obs!** Du kan skapa totalt max 500 licensgrupper.|
|Byta namn på en licensgrupp|Välj en licensgrupp i arbetsytan **Licenser** och klicka sedan på **Redigera licensgrupp** på menyn **Aktiviteter** .|
|Ta bort en licensgrupp|Välj en licensgrupp i arbetsytan **Licenser** och klicka sedan på **Ta bort licensgrupp** på menyn **Aktiviteter** . **Tips!** Eventuella licenser som fanns i den borttagna gruppen flyttas till licensgruppen **Otilldelade avtal**.|
|Ta bort ett licensavtal|I arbetsytan **Licenser** väljer du ett avtal och klickar sedan på **Ta bort**. **Tips:** När du har tagit bort volymlicensavtalen uppdaterar du licensinformationen genom att klicka på **Uppdatera nu** på sidan **Licensöversikt** eller på fliken **Allmänt** för en viss licensgrupp.|





<!--HONumber=May16_HO2-->


