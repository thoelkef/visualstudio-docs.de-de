---
title: Berechnen von Datum und Uhrzeit (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- date and time arithmetic [JavaScript]
- JavaScript, date and time
- date comparison [JavaScript]
- date and time calculations [JavaScript]
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18b4ff307c8f2c48a37ed9ca50e7c5f1ff693ece
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569500"
---
# <a name="calculating-dates-and-times-javascript"></a>Berechnen von Datum und Uhrzeit (JavaScript)
Sie können das [Date-Objekt](../javascript/reference/date-object-javascript.md) zur Ausführung allgemeiner Kalender- und Uhrzeitaufgaben verwenden, z.B. das Vergleichen von Datumsangaben und das Berechnen der verstrichenen Zeit.  
  
## <a name="setting-a-date-to-the-current-date"></a>Festlegen eines Datums auf das aktuelle Datum  
 Wenn Sie eine Instanz des [Date-Objekts](../javascript/reference/date-object-javascript.md) erstellen, ohne ein Datum anzugeben, gibt es einen Wert zurück, der das aktuelle Datum und die Uhrzeit, einschließlich Jahr, Monat, Tag, Stunde, Minute, Sekunde und Millisekunde darstellt. Sie können diesen Datums- und Uhrzeitwert dann lesen oder ändern.  
  
 Im folgenden Beispiel wird gezeigt, wie ein Datum ohne Parameter instanziiert und im Format *mm-dd-yy* angezeigt wird.  
  
```JavaScript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## <a name="setting-a-specific-date"></a>Festlegen eines bestimmten Datums  
 Sie können ein bestimmtes Datum festlegen, indem Sie eine Datumszeichenfolge an den Konstruktor übergeben.  
  
```JavaScript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  Die Zeitzone, die in der Datumszeichenfolge angezeigt wird, entspricht der Zeitzone, die auf dem lokalen Computer festgelegt ist.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] ist flexibel bezüglich des Formats der Zeichenfolge, die Sie als Parameter verwenden. Beispielsweise können Sie "8-24-2009", "24. August 2009" oder "24. Aug 2009" angeben.  
  
 Sie können auch eine Zeit angeben. Im folgenden Beispiel wird eine Möglichkeit dargestellt, ein Datum und eine Uhrzeit in ISO-Format anzugeben. Das "Z" steht für UTC-Zeit.  
  
```JavaScript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Weitere Informationen über Datumsformate wie ISO finden Sie unter [Zeichenfolgen für Datum und Uhrzeit](../javascript/date-and-time-strings-javascript.md).  
  
 Im folgenden Beispiel werden andere Möglichkeiten dargestellt, eine Zeit anzugeben.  
  
```JavaScript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## <a name="adding-and-subtracting-days-months-and-years"></a>Addieren und Subtrahieren von Tagen, Monaten und Jahren  
 Sie können die getX- und setX-Methoden des `Date`-Objekts verwenden, um bestimmte Datumsangaben und Zeiten festzulegen.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie ein Datum auf das Datum des vorherigen Tags festlegen können. Beachten Sie, dass der Monatswert und der Jahreswert ebenfalls geändert werden muss.  
  
```JavaScript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 Im folgenden Beispiel wird das Datum des letzten Tags des Monats festgelegt, indem ein Tag vom ersten Tag des Folgemonats subtrahiert wird.  
  
> [!TIP]
>  Die Monate des Jahres sind von 0 (Januar) bis 11 (Dezember) nummeriert. Die Tage der Woche sind von 0 (Sonntag) bis 6 (Samstag) nummeriert.  
  
```JavaScript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## <a name="working-with-days-of-the-week"></a>Arbeiten mit Tagen der Woche  
 Die [getDay](../javascript/reference/getday-method-date-javascript.md)-Methode ruft den Wochentag als Ziffer zwischen 0 (Sonntag) und 6 (Samstag) ab. (Nicht zu verwechseln mit der [getDate](../javascript/reference/getdate-method-date-javascript.md)-Methode, die den Monatstag als Zahl zwischen 1 und 31 abruft).  
  
 Im folgenden Beispiel wird das Datum für den US-Feiertag "Thanksgiving" festgelegt, der als der vierte Donnerstag im November definiert ist. Im Skript wird nach dem 1. November des aktuellen Jahrs gesucht, dann nach dem ersten Donnerstag, und zuletzt werden drei Wochen hinzugefügt.  
  
```JavaScript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## <a name="calculating-elapsed-time"></a>Berechnen der verstrichenen Zeit  
 Die [getTime](../javascript/reference/gettime-method-date-javascript.md)-Methode gibt die Anzahl von Millisekunden zurück, die seit Mitternacht des 1. Januar 1970 verstrichen sind. Für jedes davor liegende Datum wird eine negative Zahl zurückgegeben.  
  
 Mithilfe der [getTime](../javascript/reference/gettime-method-date-javascript.md)-Methode können Sie eine Start- und Endzeit zum Berechnen eines verstrichenen Zeitraums festlegen. Sie können die Methode zum Messen von kleinen Einheiten, z. B. einige Sekunden, und zum Messen größerer Einheiten, z. B. Tage, verwenden.  
  
 Im folgenden Beispiel wird die verstrichene Zeit in Sekunden berechnet. Die [getTime](../javascript/reference/gettime-method-date-javascript.md)-Methode ruft die Anzahl von Millisekunden seit dem Nulldatum ab.  
  
```JavaScript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Um mit besser überschaubaren Einheiten arbeiten zu können, können Sie die von der [getTime](../javascript/reference/gettime-method-date-javascript.md)-Methode zurückgegebenen Millisekunden auch durch einen passenden Wert teilen. Wenn Sie Millisekunden beispielsweise in Tage umwandeln möchten, teilen Sie die Zahl durch 86.400.000 (1000 Millisekunden x 60 Sekunden x 60 Minuten x 24 Stunden).  
  
 Das folgende Beispiel zeigt, wie viel Zeit seit dem ersten Tag des angegebenen Jahrs verstrichen ist. Es wird eine Folge von Divisionsoperationen verwendet, um die verstrichene Zeit in Tagen, Stunden, Minuten und Sekunden zu berechnen. Dabei wird die Sommerzeit nicht berücksichtigt.  
  
```JavaScript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### <a name="determining-the-users-age"></a>Bestimmen des Alters von Benutzern  
 Im folgenden Beispiel wird aus dem Geburtstag des Benutzers dessen Alter in Jahren berechnet Das Geburtsjahr wird vom laufenden Jahr subtrahiert, und dann wird zusätzlich 1 subtrahiert, falls der Geburtstag im laufenden Jahr noch nicht eingetreten ist.  
  
```JavaScript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## <a name="comparing-dates"></a>Vergleichen von Datumsangaben  
 Wenn Sie Daten in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] vergleichen, sollten Sie beachten, dass der `==`-Operator nur dann `true` zurückgibt, wenn die Daten auf beiden Seiten des Operators auf das gleiche Objekt verweisen. Wenn Sie zwei verschiedene `Date`-Objekte auf dasselbe Datum festgelegt haben, gibt `date1 == date2``false` zurück. Außerdem wird ein `Date`-Objekt, für das lediglich das Datum, aber nicht die Uhrzeit festgelegt wird, so initialisiert, dass die Uhrzeit der Mitternacht des Datums entspricht. Wenn Sie daher ein `Date` ohne festgelegte Uhrzeit mit beispielsweise `Date.now` vergleichen, sollten Sie beachten, dass `Date` auf Mitternacht festgelegt ist und `Date.now` nicht.  
  
 Im folgenden Beispiel wird überprüft, ob das aktuelle Datum mit einem angegebenen Datum übereinstimmt, oder davor oder danach liegt. Um das aktuelle Datum in `todayAtMidn` festzulegen, erstellt das Skript ein `Date`-Objekt für das aktuelle Jahr, den Monat und den Tag.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 Wenn wir das vorige Beispiel ändern, können wir überprüfen, ob ein bereitgestelltes Datum innerhalb eines bestimmten Bereichs ist.  
  
```JavaScript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Date-Objekt](../javascript/reference/date-object-javascript.md)