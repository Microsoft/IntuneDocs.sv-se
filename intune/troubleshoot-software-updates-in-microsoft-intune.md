---
title: Felsöka programuppdateringar i Microsoft Intune – Azure | Microsoft Docs
description: Lös problem med programuppdateringar i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7ec762e7e7299e400fefedbf7a8810e1da929f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461353"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Felsökning av programuppdateringar i Microsoft Intune

Lös problem med programuppdateringar i Microsoft Intune.

Om den här informationen inte är till någon hjälp, kan du även [få support för Microsoft Intune](get-support.md).

## <a name="update-agent-error-codes"></a>Felkoder för Update Agent

I följande tabell visar felkoderna för Intunes **Update Agent**. Om du inte hittar en viss felkod i den här tabellen går du till [Lista med felkoder för Windows Update](https://support.microsoft.com/help/938205/windows-update-error-code-list).

|Felkod|Symboliskt namn|Mer information|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|Agenten har stoppats.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|Åtgärden har slutförts men det uppstod fel när uppdateringarna skulle tillämpas.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Ett återanrop har markerats för att kopplas från senare eftersom begäran om att koppla från åtgärden gjordes när ett återanrop kördes.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|Datorn måste startas om för att installationen av uppdateringen ska slutföras.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|Uppdateringen som ska installeras är redan installerad på datorn.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|Uppdateringen som ska tas bort är inte installerad på datorn.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|Uppdateringen håller på att installeras.|
|**0x80cf0001**|OM_E_NO_SERVICE|Agenten kunde inte tillhandahålla tjänsten.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|Tjänstens maximala kapacitet har överskridits.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|Det går inte att hitta ett ID.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|Det gick inte att initiera objektet.|
|**0x80cf0007**|OM_E_INVALIDINDEX|Indexet för en samling är inte giltigt.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|Det gick inte att hitta nyckeln för det efterfrågade objektet.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|En åtgärd i konflikt utfördes. Vissa åtgärder, t.ex. flera installationer, kan inte utföras samtidigt.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|Åtgärden avbröts.|
|**0x80cf000C**|OM_E_NOOP|Ingen åtgärd krävdes.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|Agenten kunde inte hitta nödvändig information i uppdateringens XML-data.|
|**0x80cf000E**|OM_E_XML_INVALID|Agenten hittade information i uppdateringens XML-data som inte är giltig.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|Cirkulära uppdateringsrelationer identifierades i metadata.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|Uppdateringsrelationerna var för djupt kapslade för att kunna utvärderas.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|En uppdateringsrelation hittades som inte är giltig.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|Ett registervärde lästes som inte är giltigt.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|Åtgärden försökte lägga till ett dubblettobjekt i en lista.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|Anroparen kan inte installera uppdateringar som begärdes för installation.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|Åtgärden försökte utföra installationen medan en annan installation kördes, eller så väntade datorn på en obligatorisk omstart.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|Åtgärden utfördes inte eftersom det inte finns några tillämpliga uppdateringar.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|Åtgärden misslyckades eftersom en obligatorisk användartoken saknas.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|En exklusiv uppdatering kan inte installeras tillsammans med andra uppdateringar.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|Ett principvärde har inte angetts.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|En uppdatering innehåller metadata som inte är giltiga.|
|**0x80cf001E**|OM_E_SERVICE_STOP|Det gick inte att slutföra åtgärden eftersom tjänsten eller datorn stängdes av.|
|**0x80cf001F**|OM_E_NO_CONNECTION|Det gick inte att slutföra åtgärden eftersom nätverksanslutningen inte var tillgänglig.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|Det gick inte att slutföra åtgärden eftersom det inte finns någon inloggad interaktiv användare.|
|**0x80cf0021**|OM_E_TIME_OUT|Det gick inte att slutföra åtgärden på grund av timeout.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|Åtgärden misslyckades för alla uppdateringar.|
|**0x80cf0024**|OM_E_NO_UPDATE|Det finns inga uppdateringar.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|Grupprincipinställningar förhindrade åtkomsten till Windows Update.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|Uppdateringstypen är inte giltig.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|Det gick inte att avinstallera uppdateringen eftersom begäran inte kom från en WSUS-server.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|Sökningen kan ha missat några uppdateringar eller så kanske det finns ett program utan licens på datorn.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|Det gick inte att installera en deltakomprimerad uppdatering eftersom källan krävdes.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|Det gick inte att installera en fullständig filuppdatering eftersom källan krävdes.|
|**0x80cf002E**|OM_E_WU_DISABLED|Åtkomst till en ohanterad server tillåts inte.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|Det gick inte att slutföra åtgärden eftersom principen **DisableWindowsUpdateAccess** har angetts.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|Proxylistformatet är inte giltigt.|
|**0x80cf0031**|OM_E_INVALID_FILE|Filen har fel format.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|Strängen med sökvillkor är inte giltig.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|Det gick inte att hämta uppdateringen.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|Uppdateringen bearbetades inte.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|Objektets aktuella tillstånd tillät inte åtgärden.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|Åtgärden stöds inte.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|Den hämtade filen har en oväntad innehållstyp.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|Servern bad agenten synkronisera om för många gånger.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|Det finns inte stöd för WUA-användargränssnittet.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Endast administratörer kan utföra den här åtgärden för uppdateringar på varje dator.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|En sökning gjordes med en omfattning som inte stöds.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|URL:en refererar inte till en fil.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|Den begärda åtgärden stöds inte.|
|**0x80cf0049**|OM_E_OUTOFRANGE|Data är utanför intervallet.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|Data innehåller en version som inte är giltig.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|Sökanropet slutfördes, men det gick inte att identifiera vissa uppdateringar.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|Hämtningsanropet slutfördes, men det gick inte att hämta vissa uppdateringar.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|Installationen slutfördes, men det gick inte att installera vissa uppdateringar.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Windows Update-cachen är tom eftersom den inte har initierats.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|Servern stöder inte kategorispecifik sökning. Fullständig katalogsökning måste anges i stället.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Det uppstod ett problem med auktoriseringen med tjänsten.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|Det finns ingen väg eller nätverksanslutning till slutpunkten.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|Mottagna data uppfyller inte förväntningarna för datakontraktet.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|Webbadressen är inte giltig.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|Det går inte att läsa in NWS-körtiden.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|Proxyautentiseringsschemat stöds inte.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|Den begärda tjänstegenskapen är inte tillgänglig.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|Plugin-providern för tjänstslutpunkten kräver en onlineuppdatering.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|Det finns ingen tillgänglig URL för den begärda tjänstslutpunkten.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|Anslutningen till tjänstslutpunkten avbröts.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|Åtgärden är inte giltig eftersom protokolltalaren är i ett felaktigt tillstånd.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|En åtgärd misslyckades av skäl som inte förklaras av en annan felkod.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|Sökningen kan ha missat vissa uppdateringar eftersom Windows Installer är en tidigare version än version 3.1.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|Sökningen kan ha missat vissa uppdateringar eftersom Windows Installer inte har konfigurerats.|
|**0x80cf1003**|OM_E_MSP_DISABLED|Sökningen kan ha missat vissa uppdateringar eftersom principen har inaktiverat Windows Installer-korrigering.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|Det gick inte att tillämpa en uppdatering eftersom programmet installeras per användare.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|Det gick inte att utföra en begäran för en fjärruppdateringshanterare eftersom ingen fjärrprocess är tillgänglig.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|Det gick inte att utföra en begäran för en fjärruppdateringshanterare eftersom hanteraren endast är lokal.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|Det gick inte att skapa en fjärruppdateringshanterare eftersom det redan finns en.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|Det gick inte att utföra en begäran för hanteraren om att installera (avinstallera) en uppdatering eftersom uppdateringen inte stöder installation (avinstallation).|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|Det gick inte att utföra åtgärden eftersom fel hanterare angavs.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|Det gick inte att utföra en hanteraråtgärd eftersom uppdateringen innehåller metadata som inte är giltiga.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|Det gick inte att utföra en åtgärd eftersom installationsprogrammet överskred tidsgränsen. Kontrollera om en uppdatering som kräver användarinteraktion har godkänts för distribution. I så fall måste du ändra installationsparametrarna för uppdateringen så att den kan installeras tyst i bakgrunden.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|En åtgärd som utfördes av uppdateringshanteraren avbröts.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|Det gick inte att utföra en åtgärd eftersom hanterarspecifika metadata inte är giltiga.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|Det gick inte att installera (avinstallera) en eller flera uppdateringar.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|Uppdateringshanteraren installerade inte uppdateringen eftersom den måste hämtas igen.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|Uppdateringshanteraren kunde inte skicka meddelanden om installationsåtgärdens (avinstallationsåtgärdens) status.|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|Åtgärderna som utförs efter omstart för uppdateringen pågår fortfarande.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|Det gick inte att bestämma resultatet av åtgärderna som utförs efter omstart för uppdateringen.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|Uppdateringen har oväntad status efter att åtgärderna som utförs efter omstart utfördes.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|OS-tjänststacken måste uppdateras innan den här uppdateringen hämtas eller installeras.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Ett fel inträffade vid en motringning med en motringningsinstallation.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|Signaturen för det anpassade installationsprogrammet överensstämmer inte med signaturen som krävs för uppdateringen.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|Installationsprogrammet stöder inte installationskonfigurationen.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|Målsessionen för installationen är inte giltig.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Ett uppdateringshanterarfel motsvarar ingen annan OM_E_UH_&#42;-kod.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|Det går inte att visa UI i icke-UI-läge. Windows Update-klientens UI-moduler kanske inte är installerade.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|Versionen av WU-klientgränssnittets exporterade funktioner stöds inte.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Det uppstod ett användargränssnittsfel som inte motsvarar någon annan OM_E_AUCLIENT_&#42;-felkod.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|Samma som **SOAPCLIENT_SOAPFAULT**. SOAP-klienten misslyckades på grund av SOAP-felet **OM_E_PT_SOAP_&#42;**|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|Samma som **SOAPCLIENT_PARSEFAULT_ERROR**.  SOAP-klienten kunde inte parsa ett SOAP-fel.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|Samma som **SOAPCLIENT_PARSE_ERROR**.  SOAP-klienten kunde inte parsa svaret från servern.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|Samma som **SOAP_E_VERSION_MISMATCH**. SOAP-klienten hittade ett okänt namnområde för SOAP-kuvertet.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|Samma som **SOAP_E_MUST_UNDERSTAND**. SOAP-klienten kunde inte tolka ett sidhuvud.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|Samma som **SOAP_E_CLIENT**. SOAP-klienten upptäckte att meddelandet har fel format. Åtgärda problemet innan du skickar meddelandet igen.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|Samma som **SOAP_E_SERVER**. SOAP-meddelandet kunde inte bearbetas på grund av ett serverfel. Skicka senare.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|Gränsen för antalet sändningar fram och tillbaka till servern överskreds.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|Initieringen misslyckades eftersom objektet redan hade initierats.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|Det gick inte att fastställa namnet på datorn.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|Svaret från servern anger att servern har ändrats eller att cookien var ogiltig. Uppdatera det interna cacheminnet och försök igen.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|Samma som **HTTP-status 400**. Servern kunde inte bearbeta begäran eftersom syntaxen inte är giltig.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|Samma som **HTTP-status 401**. Den begärda resursen kräver användarautentisering.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|Samma som **HTTP-status 403**. Servern förstod begäran, men avböjde att utföra den.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|Samma som **HTTP-status 404**. Servern kan inte hitta begärd URI (Uniform Resource Identifier).|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|Samma som **HTTP-status 405**. HTTP-metoden tillåts inte.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|Samma som **HTTP-status 407**. Proxyautentisering krävs.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|Samma som **HTTP-status 408**. Tidsgränsen överskreds när servern väntade på begäran.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|Samma som **HTTP-status 409**. Begäran slutfördes inte på grund av en konflikt med resursens aktuella tillstånd.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|Samma som **HTTP-status 410**. Den begärda resursen är inte längre tillgänglig på servern.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|Samma som **HTTP-status 500**. Ett internt serverfel förhindrade att begäran utfördes.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|Samma som **HTTP-status 500**. Servern stöder inte funktionerna som krävs för att utföra begäran.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|Samma som **HTTP-status 502**. När servern fungerade som en gateway eller proxy tog den emot ett ogiltigt svar från den överordnade server som den anslöt till när den försökte utföra begäran.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|Samma som **HTTP-status 503**. Tjänsten är tillfälligt överbelastad.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|Samma som **HTTP-status 503**. Tidsgränsen för begäran gick ut i väntan på en gateway.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|Samma som **HTTP-status 505**. Servern stöder inte den version av HTTP-protokollet som används för begäran.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|Åtgärden misslyckades på grund av en ändrad filplats. Uppdatera det interna tillståndet och skicka igen.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|Servern returnerade en tom lista med autentiseringsinformation.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|Agenten kunde inte skapa några giltiga autentiseringscookies.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Konfigurationsegenskapens värde var fel.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Konfigurationsegenskapens värde saknas.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|Det gick inte att slutföra HTTP-begäran och orsaken motsvarade inte någon av **OM_E_PT_HTTP_&#42;**-felkoderna.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|Samma som **ERROR_WINHTTP_NAME_NOT_RESOLVED**. Det går inte att matcha proxyserverns eller målserverns namn.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|Bearbetningen av den externa CAB-filen slutfördes med fel.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|Initieringen av den externa CAB-processorn kunde inte slutföras.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|Formatet för en metadatafil är inte giltigt.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|Den externa CAB-processorn hittade metadata som inte är giltiga.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|Det gick inte att extrahera filsammandraget från en extern CAB-fil.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|Det gick inte att dekomprimera en extern CAB-fil.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|Den externa CAB-processorn kunde inte hämta filplatserna.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Det uppstod ett kommunikationsfel som inte motsvarar någon annan **OM_E_PT_&#42;**-felkod.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|Det gick inte att utföra en åtgärd för hämtningshanteraren eftersom den begärda filen inte har någon URL.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|Det gick inte att utföra åtgärden för hämtningshanteraren eftersom filsammandraget inte kändes igen.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|Det gick inte att utföra åtgärden för hämtningshanteraren eftersom filens metadata begärde en okänd hashalgoritm.|
|**0x80cf6005**|OM_E_DM_NONETWORK|Det gick inte att utföra en åtgärd för hämtningshanteraren eftersom nätverksanslutningen inte var tillgänglig.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|Uppdateringen har inte hämtats.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|En åtgärd för hämtningshanteraren misslyckades eftersom hämtningshanteraren inte kunde ansluta BITS (Background Intelligent Transfer Service).|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|En åtgärd för hämtningshanteraren misslyckades eftersom det uppstod ett okänt BITS-överföringsfel (Background Intelligent Transfer Service).|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|Hämtningen måste startas om eftersom källplatsen för hämtningen har ändrats.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|Hämtningen måste startas om eftersom uppdateringsinnehållet har ändrats i en ny version.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Det uppstod ett fel med hämtningshanteraren som inte motsvarar någon annan **OM_E_DM_&#42;**-felkod.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|En händelsenyttolast angavs som inte är giltig.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|Storleken på händelsenyttolasten som skickades är inte giltig.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|Tjänsten har inte registrerats.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|En åtgärd misslyckades eftersom agenten stängs.|
|**0x80cf8001**|OM_E_DS_INUSE|En åtgärd misslyckades eftersom datalagret användes.|
|**0x80cf8002**|OM_E_DS_INVALID|Det aktuella och förväntade tillståndet för datalagret stämmer inte överens.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|En tabell saknas i datalagret.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|Datalagret innehåller en tabell som har oväntade kolumner.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|En tabell kunde inte öppnas eftersom tabellen inte finns i datalagret.|
|**0x80cf8006**|OM_E_DS_BADVERSION|Den aktuella och förväntade versionen för datalagret stämmer inte överens.|
|**0x80cf8007**|OM_E_DS_NODATA|Den information som efterfrågas finns inte i datalagret.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|Nödvändig information saknas i datalagret eller så innehåller datalagret ett null-värde i en tabellkolumn som kräver ett värde som inte är null.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|Nödvändig information saknas i datalagret eller så innehåller datalagret en referens till licensvillkor, en fil, en lokaliserad egenskap eller en länkad rad som saknas.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|Uppdateringen kunde inte bearbetas eftersom uppdateringshanteraren inte kändes igen.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|Uppdateringen togs inte bort eftersom en eller flera tjänster fortfarande refererar till den.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|Det gick inte att låsa datalageravsnittet inom utsatt tid.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|Raden lades inte till eftersom en befintlig rad har samma primärnyckel.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|Datalagret kunde inte initieras eftersom det har låsts av en annan process.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|Datalagret får inte registreras med COM i den aktuella processen.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|En åtgärd kunde inte skapa ett datalagerobjekt i en annan process.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|Servern skickade samma uppdatering till klienten med två olika revisions-ID:n.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|Det gick inte att utföra en åtgärd eftersom tjänsten inte finns i datalagret.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|Det gick inte att utföra en åtgärd eftersom registreringen av tjänsten har upphört att gälla.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|En begäran om att dölja en uppdatering nekades eftersom det är en obligatorisk uppdatering eller eftersom den distribuerades med en tidsgräns.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|En tabell stängdes inte eftersom den inte är associerad med sessionen.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|En tabell stängdes inte eftersom den inte är associerad med sessionen.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|Begäran om att ta bort eller avregistrera tjänsten nekades eftersom det är en inbyggd tjänst eller eftersom Automatiska uppdateringar inte kan växla över till en annan tjänst.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|Begäran nekades eftersom åtgärden inte tillåts.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|Schemat för det aktuella datalagret och schemat för en tabell i ett säkerhetskopierat XML-dokument stämmer inte överens.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|Datalagret kräver en sessionsåterställning. Frisläpp sessionen och försök igen med en ny session.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|En datalageråtgärd kunde inte utföras eftersom den begärdes med en personifierad identitet.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Det uppstod ett fel med datalagret som inte motsvarar någon annan **OM_E_DS_&#42;**-felkod.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|Automatiska uppdateringar kunde inte hantera inkommande begäranden.|
|**0x80cfA004**|OM_E_AU_PAUSED|Automatiska uppdateringar kunde inte bearbeta inkommande begäranden eftersom funktionen har pausats.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|Ingen ohanterad tjänst har registrerats med Automatiska uppdateringar.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|Standardtjänsten som har registrerats med Automatiska uppdateringar ändrades under sökningen.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|Automatiska uppdateringar uppmanar redan användaren att starta om.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|Det uppstod ett fel med funktionen för automatiska uppdateringar som inte motsvarar någon annan **OM_E_AU &#42;**-felkod.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|Det gick inte att utföra en uttrycksutvärderingsåtgärd eftersom ett uttryck inte kändes igen.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|Det gick inte att utföra en uttrycksutvärderingsåtgärd eftersom ett uttryck inte var giltigt.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|Det gick inte att utföra en uttrycksutvärderingsåtgärd eftersom ett uttryck innehåller fel antal metadatanoder.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|Det gick inte att utföra en uttrycksutvärderingsåtgärd eftersom versionen av serialiserade uttrycksdata inte är giltiga.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|Det gick inte att initiera uttrycksutvärderaren.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|Det gick inte att utföra en uttrycksutvärderingsåtgärd eftersom ett attribut inte är giltigt.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|Det gick inte att utföra en uttrycksutvärderingsåtgärd eftersom det inte gick att fastställa datorns klustertillstånd.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Det uppstod ett fel med uttrycksutvärderaren som inte motsvarar någon annan **OM_E_EE_&#42;**-felkod.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|Händelsecachefilen var skadad.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|Det gick inte att parsa XML-koden i beskrivningen av händelsenamnområdet.|
|**0x80cfF003**|OM_E_INVALID_EVENT|XML-koden i beskrivningen av händelsenamnområdet är inte giltig.|
|**0x80cfF004**|OM_E_SERVER_BUSY|Servern avvisade en händelse eftersom servern var för upptagen.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Det uppstod ett rapporteringsfel som inte motsvarar någon annan felkod.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|Installationen misslyckades eftersom en obligatorisk omstart väntar.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|Hämtningen avbröts.|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>Windows 7-baserade datorer med många ersatta programuppdateringar slutar rapportera till Microsoft Intune-konsolen
**Problem**: Du kan stöta på en situation där ett eller flera av följande problem uppstår i Microsoft Intune-klienter:
- De slutar plötsligt rapportera till Microsoft-administrationskonsolen.  
- De uppvisar hög processoranvändning.
- Programmen installeras långsamt när de installeras via Intune-portalen.
- Microsoft Intune Center utlöser följande fel: *Ett fel uppstod när datorn uppdaterades. Fel hittades: kod 0x800705b4*.
- Statusfältet på Intune-administratörskonsolen > Grupper > Alla enheter visar: *En eller flera agenter installerade på den här datorn har fel. Informationen för datorn är kanske felaktig eller inaktuell*.

Det här problemet kan uppstå om ersatta programuppdateringar (uppdateringar som har ersatts av en annan uppdatering) inte har avfärdats under en längre tid. Under vissa processer, till exempel installationen av ett program, kontrollerar Windows alla ersatta uppdateringar i följd så att uppdateringarna och deras efterträdare kan mappas korrekt. Om listan över ersatta programuppdateringar blir för stor kan den här kontrollåtgärden leda till hög processoranvändning på grund av den bearbetningsbelastning och tid som krävs. Det här problemet påverkar huvudsakligen klienter som kör Windows 7 på grund av det stora antalet ersatta programuppdateringar som är tillgängliga för Windows 7. Windows 8 och senare operativsystem har inte lika många ersatta uppdateringar och är därför inte lika mottagliga för det här problemet.

**Lösning**:  
1. Logga in på [Azure-portalen](https://portal.azure.com) och öppna **Microsoft Intune**. 
2. Välj **Programuppdateringar**.
3. Avfärda alla ersatta uppdateringar som gäller Windows 7 eller program (till exempel Microsoft Office) som har installerats på de berörda klienterna.
4. Starta om de berörda klienterna.

Om du kör Windows 7 kontrollerar du dessutom att följande uppdatering är installerad: [3050265 Windows Update-klienten för Windows 7: juni 2015](https://support.microsoft.com/kb/3050265).

### <a name="next-steps"></a>Nästa steg
Om den här informationen inte är till någon hjälp, kan du även [få support för Microsoft Intune](get-support.md).
