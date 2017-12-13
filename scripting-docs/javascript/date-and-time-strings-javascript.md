---
title: "Zeichenfolgen für Datum und Uhrzeit (JavaScript) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba0798c5-3574-4434-89f4-3d90be276001
caps.latest.revision: "47"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6218ba273b26243382d1e825b6da961d604917ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="date-and-time-strings-javascript"></a>Zeichenfolgen für Datum und Uhrzeit (JavaScript)
Sie können diverse Techniken verwenden, um JavaScript-Datums- und Uhrzeitzeichenfolgen anzugeben und zu formatieren.  
  
## <a name="formatting-dates-using-intldatetimeformat"></a>Formatieren von Daten mit "International.DateTimeFormat"  
 Internet Explorer 11 stellt die Unterstützung für das [Intl.DateTimeFormat-Objekt](../javascript/reference/intl-datetimeformat-object-javascript.md) bereit, das Teil der [ECMAScript-Internationalisierungs-API-Spezifikation](http://www.ecma-international.org/ecma-402/1.0/) ist. Um Datumsangaben zu formatieren, können Sie dieses Objekt direkt verwenden oder die aktualisierte Implementierung der [toLocaleDateString-Methode (Date)](../javascript/reference/tolocaledatestring-method-date-javascript.md) und der [toLocaleTimeString-Methode (Date)](../javascript/reference/tolocaletimestring-method-date-javascript.md) nutzen. Diese Methoden des [Date-Objekts](../javascript/reference/date-object-javascript.md) verwenden intern `Intl.DateTimeFormat`, um neue optionale Parameter für das Gebietsschema und für andere Formatierungsoptionen zu unterstützen.  
  
 Das folgende Beispiel zeigt, wie `toLocaleDateString` und `toLocaleTimeString` zu verwenden sind, um Datumsangaben und Zeitangaben zu formatieren. Der erste an diese Methoden übergebene Parameter ist ein Gebietsschemawert wie z. B. "de-de". Der zweite Parameter, wo vorhanden, gibt Formatierungsoptionen an, wie z. B. das lange Format für den Wochentag.  
  
```JavaScript  
var date = new Date(Date.UTC(2013, 1, 1, 14, 0, 0));  
var options = {  
    weekday: "long", year: "numeric", month: "short",  
    day: "numeric", hour: "2-digit", minute: "2-digit"  
};  
  
document.write(date.toLocaleDateString("en-US"));  
document.write(date.toLocaleTimeString("en-us", options));  
document.write(date.toLocaleDateString("ja-JP"));  
document.write(date.toLocaleTimeString("ja-JP", options));  
  
// Output:  
// ‎2‎/‎1‎/‎2013  
// ‎Friday‎, ‎Feb‎ ‎1‎, ‎2013‎ ‎06‎:‎00‎ ‎AM  
// ‎2013‎年‎2‎月‎1‎日‎  
// ‎2013‎年‎2‎月‎1‎日 ‎金曜日‎ ‎06‎:‎00  
```  
  
 Eine vollständige Liste der Formatierungsoptionen finden Sie unter [Intl.DateTimeFormat-Objekt](../javascript/reference/intl-datetimeformat-object-javascript.md).  
  
## <a name="formatting-dates"></a>Formatieren von Datumsangaben  
 Vor Internet Explorer 11 hatte JavaScript keine bestimmten Methoden, um Datums- und Zeitangaben zu formatieren. Damit Sie Ihre eigene Datumsformatierung für vorherige Browserversionen bereitstellen können, verwenden Sie die [getDay-Methode (Date)](../javascript/reference/getday-method-date-javascript.md), die [getDate-Methode (Date)](../javascript/reference/getdate-method-date-javascript.md), die [getMonth-Methode (Date)](../javascript/reference/getmonth-method-date-javascript.md) und die [getFullYear-Methode (Date)](../javascript/reference/getfullyear-method-date-javascript.md). (Die [getYear-Methode (Date) ](../javascript/reference/getyear-method-date-javascript.md) ist veraltet und sollte nicht verwendet werden.)  
  
```JavaScript  
var myDate = new Date("February 3, 2001");  
var myDate = new Date("February 3 2001");  
document.write((myDate.getMonth() + 1) + "-" + myDate.getDate() + "-" + myDate.getFullYear());  
document.write("<br/>");  
document.write((myDate.getMonth() + 1) + "/" + myDate.getDate() + "/" + myDate.getFullYear());  
  
//Output:  
// 2-3-2001  
// 2/3/2001  
```  
  
 Sie können Ihre eigenen Zeitformate mithilfe der [getHours-Methode (Date)](../javascript/reference/gethours-method-date-javascript.md), [getMinutes-Methode (Date)](../javascript/reference/getminutes-method-date-javascript.md), [getSeconds-Methode (Date)](../javascript/reference/getseconds-method-date-javascript.md) und [getMilliseconds-Methode (Date)](../javascript/reference/getmilliseconds-method-date-javascript.md) bereitstellen.  
  
```JavaScript  
myDate = new Date();  
myDate.setHours(10, 30, 53, 400);  
  
document.write(myDate.getHours() + ":" + myDate.getMinutes() + ":" + myDate.getSeconds() +   
":" + myDate.getMilliseconds());  
  
// Output:   
// 10:30:53:400  
```  
  
## <a name="converting-strings-to-dates"></a>Konvertieren von Zeichenfolgen in Datumsangaben  
 Sie können Zeichenfolgen zum Erstellen von `Date`-Objekten mit `Date(dateStr)` oder mit `Date.parse(dateStr)` angeben. JavaScript analysiert Datumszeichenfolgen anhand der folgenden Regeln:  
  
-   Zuerst wird versucht, eine Datumszeichenfolge mit dem [ISO-Datumsformat](#ISO) zu analysieren.  
  
    > [!NOTE]
    >  JavaScript verwendet eine vereinfachte Version des erweiterten Formats ISO 8601.  
  
-   Wenn die Datumszeichenfolge nicht im ISO-Format vorliegt, versucht JavaScript, das Datum unter Verwendung [anderer Datumsformate](#OtherDateFormats) zu analysieren.  
  
<a name="ISO"></a>   
## <a name="iso-date-format"></a>ISO-Datumsformat  
 Das ISO-Format ist eine Vereinfachung des erweiterten Formats ISO 8601. Es wird folgendes Format verwendet:  
  
 `YYYY-MM-DDTHH:mm:ss.sssZ`  
  
> [!IMPORTANT]
>  Das ISO-Datumsformat wird im Internet Explorer 8 (Standardmodus) und Quirksmodus nicht unterstützt.  
  
 In der folgenden Tabelle werden Teile dieses Formats beschrieben.  
  
|Symbol|Beschreibung|Werte|  
|------------|-----------------|------------|  
|`-`, `:`, `.`, `T`|Tatsächlich in der Zeichenfolge enthaltene Zeichen. `T` gibt den Anfang einer Uhrzeit an.||  
|`YYYY`|Jahr. Ein erweitertes Jahr kann statt einer vierstelligen Jahreszahl verwendet werden. Weitere Informationen finden Sie weiter unten in diesem Artikel unter [Erweiterte Jahresformate](../javascript/date-and-time-strings-javascript.md#bkmk_extend).||  
|`MM`|Monat|01 bis 12|  
|`DD`|Tag in einem Monat|01 bis 31|  
|`HH`|Stunden|00 bis 24|  
|`mm`|Besprechungsprotokoll|00 bis 59|  
|`ss`|Sekunden. Die Sekunden und die Millisekunden sind optional, wenn eine Uhrzeit angegeben wird.|00 bis 59|  
|`sss`|Milliseconds|00 bis 999|  
|`Z`|An dieser Position ist einer der folgenden Werte zulässig. Wird der Wert nicht angegeben, wird die UTC-Uhrzeit verwendet.<br /><br /> -   `Z` gibt die UTC-Zeit an.<br />-   `+hh:mm` gibt an, dass die Eingabezeit der angegebene Offset nach der UTC-Zeit ist.<br />-   `-hh:mm` gibt an, dass die Eingabezeit der absolute Wert des angegebenen Offsets vor der UTC-Zeit ist.||  
  
 Die Zeichenfolge kann nur das Datum in den folgenden Formaten enthalten: `YYYY`, `YYYY-MM`, `YYYY-MM-DD`.  
  
 Das ISO-Format unterstützt keine Zeitzonennamen. Sie können die Position `Z` verwenden, um einen Offset gegenüber der UTC-Zeit anzugeben. Wenn Sie keinen Wert in der `Z` Position angeben, wird die UTC-Zeit verwendet.  
  
 Für Mitternacht kann die Uhrzeit 00:00 für den aktuellen Tag oder 24:00 für den Vortag angegeben werden. Mit den folgenden beiden Zeichenfolgen wird die gleiche Uhrzeit angegeben: 2010-05-25T00:00 und 2010-05-24T24:00.  
  
 Um ein Datum im ISO-Format zurückzugeben, sollten Sie die [toISOString-Methode (Date)](../javascript/reference/toisostring-method-date-javascript.md) verwenden.  
  
<a name="bkmk_extend"></a>   
### <a name="extended-years"></a>Erweiterte Jahre  
 Ein *erweitertes Jahr* verfügt über 6 Ziffern statt 4 Ziffern und ein vorangestelltes Plus- oder Minuszeichen. Ein Beispiel für ein erweitertes Jahr ist `+002010`, das `2010` entspricht. Sie können ein erweitertes Jahr verwenden, um Jahre vor dem Jahr 0 oder nach 9999 darzustellen.  
  
 Wenn Sie das sechsstellige Format verwenden, müssen Sie ein Plus- oder Minuszeichen angeben. Wenn Sie das vierstellige Format verwenden, darf kein Vorzeichen vorhanden sein. Daher werden `0000` und `+000000` akzeptiert, `000000` und `-0001` verursachen jedoch einen Fehler. Das erweiterte Jahr 0 wird als positiver Wert betrachtet und daher mit einem vorangestellten Pluszeichen versehen.  
  
 Die [toISOString-Methode (Date)](../javascript/reference/toisostring-method-date-javascript.md) verwendet immer das erweiterte Jahr für die Jahre, die vor 0 und nach 9999 liegen.  
  
> [!NOTE]
>  [!INCLUDE[jsv9](../javascript/includes/jsv9-md.md)]  
  
<a name="OtherDateFormats"></a>   
## <a name="other-date-formats"></a>Andere Datumsformate  
 Wenn eine Datumszeichenfolge nicht im ISO-Format vorliegt, wird sie in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unter Verwendung der folgenden Regeln analysiert.  
  
 Kurze Datumangaben  
  
-   Das Format muss der Reihenfolge Monat/Tag/Jahr entsprechen, beispielsweise "06/08/2010".  
  
-   Als Trennzeichen können "/" oder "-" verwendet werden.  
  
 Lange Datumsangaben  
  
-   Jahr, Monat und Tag können in beliebiger Reihenfolge angegeben werden. "8. Juni 2010" und "2010 Juni 8" sind beide gültig.  
  
-   Das Jahr kann zwei oder vier Ziffern haben. Wenn die Jahresangabe nur zwei Ziffern hat, muss sie größer oder gleich 70 sein.  
  
-   Monats- und Tagesnamen müssen mindestens zwei Zeichen lang sein. Namen mit zwei Zeichen, die nicht eindeutig sind, werden dem letzten übereinstimmenden Namen zugeordnet. Beispielsweise "Ju" gibt Juli, nicht Juni an.  
  
-   Ein Wochentag wird ignoriert, wenn er mit dem Rest des angegebenen Datums inkonsistent ist. Beispielsweise wird "Dienstag, 9. November 1996" in "Freitag, 9. November 1996" aufgelöst, weil Freitag der richtige Wochentag für dieses Datum ist.  
  
 Uhrzeiten  
  
-   Stunden, Minuten und Sekunden werden durch Doppelpunkte getrennt. Einige Teile können jedoch weggelassen werden. Die folgenden Werte sind gültig: "10:", "10:11" und "10:11:12".  
  
-   Wenn PM angegeben wird und die angegebene Stunde größer oder gleich 13 ist, wird NaN zurückgegeben. Beispielsweise wird für "23:15 PM" NaN zurückgegeben.  
  
 Allgemein  
  
-   Für eine Zeichenfolge, die ein ungültiges Datum enthält, wird NaN zurückgegeben. Beispielsweise wird für eine Zeichenfolge, die zwei Jahre oder zwei Monate enthält, NaN zurückgegeben.  
  
-   [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] unterstützt alle Standardzeitzonen sowie koordinierte Weltzeit (UTC) und GMT (Greenwich Mean Time). (Das ISO-Format unterstützt keine Zeitzonen.)  
  
-   Text, der in Klammern eingeschlossen ist, wird als Kommentar behandelt. Klammern können geschachtelt werden.  
  
-   Kommas und Leerzeichen werden als Begrenzungszeichen behandelt. Mehrfache Begrenzungszeichen sind erlaubt.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt die Ergebnisse der Analyse von verschiedenen Datums- und Uhrzeitzeichenfolgen.  
  
```  
document.writeln((new Date("2010")).toUTCString());   
  
document.writeln((new Date("2010-06")).toUTCString());  
  
document.writeln((new Date("2010-06-09")).toUTCString());  
  
 // Specifies Z, which indicates UTC time.  
document.writeln((new Date("2010-06-09T15:20:00Z")).toUTCString());  
  
 // Specifies -07:00 offset, which is equivalent to Pacific Daylight time.  
document.writeln((new Date("2010-06-09T15:20:00-07:00")).toGMTString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("June 9, 2010")).toUTCString());  
  
// Specifies a non-ISO Long date.  
document.writeln((new Date("2010 June 9")).toUTCString());  
  
// Specifies a non-ISO Short date and time.  
document.writeln((new Date("6/9/2010 3:20 pm")).toUTCString());  
  
// Output:  
// Fri, 1 Jan 2010 00:00:00 UTC  
// Tue, 1 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 00:00:00 UTC  
// Wed, 9 Jun 2010 15:20:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 07:00:00 UTC  
// Wed, 9 Jun 2010 22:20:00 UTC  
```  
  
 Wenn Ortszeiten angegeben werden, ist das Ergebnis von der Zeitzone abhängig.  
  
> [!IMPORTANT]
>  Das ISO-Datumsformat wird im Internet Explorer 8 (Standardmodus) und Quirksmodus nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Date-Objekt](../javascript/reference/date-object-javascript.md)   
 [Date.parse-Funktion](../javascript/reference/date-parse-function-javascript.md)