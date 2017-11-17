---
title: Date-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Date
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, determining
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb5d53f3bddfeb3a3ed1ab36e2b4be822964eba5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="date-object-javascript"></a>Date-Objekt (JavaScript)
Ermöglicht grundlegendes Speichern und Abrufen von Datums- und Zeitangaben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Der Variablenname, dem das `Date`-Objekt zugewiesen wird.  
  
 `dateVal`  
 Erforderlich. Als numerischer Wert gibt `dateVal` die Anzahl der Millisekunden in UTC (Universal Time Coordinated) zwischen dem angegebenen Datum und Mitternacht des 1. Januar 1970 an. Wenn eine Zeichenfolge `dateVal` wird gemäß den Regeln in analysiert [Datum- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md). Das `dateVal`-Argument kann auch ein VT_DATE-Wert sein, der von einigen ActiveX-Objekten zurückgegeben wird.  
  
 `year`  
 Erforderlich. Das vollständige Jahr, z. B. 1976 (und nicht 76).  
  
 `month`  
 Erforderlich. Der Monat als ganze Zahl zwischen 0 und 11 (Januar bis Dezember).  
  
 `date`  
 Erforderlich. Das Datum als ganze Zahl zwischen 1 und 31.  
  
 `hours`  
 Dies ist optional. Muss angegeben werden, wenn auch `minutes` angegeben wird. Eine ganze Zahl zwischen 0 und 23 (Mitternacht bis 23 Uhr), die die Stunde angibt.  
  
 Minuten  
 Dies ist optional. Muss angegeben werden, wenn auch `seconds` angegeben wird. Eine ganze Zahl zwischen 0 und 59, die die Minuten angibt.  
  
 `seconds`  
 Dies ist optional. Muss angegeben werden, wenn auch `milliseconds` angegeben wird. Eine ganze Zahl zwischen 0 und 59, die die Sekunden angibt.  
  
 `ms`  
 Dies ist optional. Eine ganze Zahl zwischen 0 und 999, die die Millisekunden angibt.  
  
## <a name="remarks"></a>Hinweise  
 Ein `Date`-Objekt enthält eine Zahl, die einen bestimmten Zeitpunkt bis auf eine Millisekunde genau darstellt. Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Wenn Sie z. B. 150 Sekunden angeben, macht [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] daraus 2 Minuten und 30 Sekunden.  
  
 Ist die Zahl `NaN`, stellt das Objekt keinen bestimmten Zeitpunkt dar. Wenn Sie keine Parameter an das `Date`-Objekt übergeben, wird es mit der aktuellen Zeit (UTC) initialisiert. Dem Objekt muss ein Wert zugewiesen werden, bevor Sie es verwenden können.  
  
 Der Bereich, der in einem `Date`-Objekt dargestellt werden kann, beträgt etwa 285.616 Jahre vor und nach dem 1. Januar 1970.  
  
 Finden Sie unter [berechnen von Datums- und Uhrzeitangaben (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) für Weitere Informationen zum Verwenden der `Date` Objekt und die zugehörigen Methoden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung des `Date`-Objekts.  
  
```JavaScript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## <a name="requirements"></a>Anforderungen  
 Das `Date object` wurde in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] eingeführt. Einige Member der folgenden Listen wurden in höheren Versionen eingeführt. Weitere Informationen finden Sie unter [Versionsinformationen](../../javascript/reference/javascript-version-information.md) oder in der Dokumentation für die einzelnen Mitglieder.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle sind die Eigenschaften des `Date Object`s aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Constructor-Eigenschaft](../../javascript/reference/constructor-property-date.md)|Gibt die Funktion an, durch die ein Objekt erstellt wird.|  
|[Prototype-Eigenschaft](../../javascript/reference/prototype-property-date.md)|Gibt einen Verweis auf den Prototyp einer Objektklasse zurück.|  
  
## <a name="functions"></a>Funktionen  
 In der folgenden Tabelle sind die Funktionen des `Date Object`s aufgelistet.  
  
|Funktionen|Beschreibung|  
|---------------|-----------------|  
|[Date.now-Funktion](../../javascript/reference/date-now-function-javascript.md)|Gibt die Anzahl der Millisekunden zwischen dem 1. Januar 1970 und dem aktuellen Datum und der Uhrzeit zurück.|  
|[Date.parse-Funktion](../../javascript/reference/date-parse-function-javascript.md)|Analysiert eine Zeichenfolge mit einem Datum und gibt die Anzahl der Millisekunden zwischen diesem Datum und Mitternacht des 1. Januars 1970 zurück.|  
|[Date.UTC-Funktion](../../javascript/reference/date-utc-function-javascript.md)|Gibt die Anzahl der Millisekunden zwischen Mitternacht des 1. Januar 1970 UTC (Universal Coordinated Time) oder GMT und dem angegebenen Datum zurück.|  
  
<a name="js56jsobjdatemeth"></a>   
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden des `Date Object`s aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[getDate-Methode](../../javascript/reference/getdate-method-date-javascript.md)|Gibt den Wert für einen Tag des Monats unter Verwendung der Ortszeit zurück.|  
|[getDay-Methode](../../javascript/reference/getday-method-date-javascript.md)|Gibt den Wert für einen Tag der Woche unter Verwendung der Ortszeit zurück.|  
|[getFullYear-Methode](../../javascript/reference/getfullyear-method-date-javascript.md)|Gibt den Wert des Jahres unter Verwendung der Ortszeit zurück.|  
|[getHours-Methode](../../javascript/reference/gethours-method-date-javascript.md)|Gibt den Stundenwert unter Verwendung der Ortszeit zurück.|  
|[getMilliseconds-Methode](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Gibt den Millisekundenwert unter Verwendung der Ortszeit zurück.|  
|[getMinutes-Methode](../../javascript/reference/getminutes-method-date-javascript.md)|Gibt den Minutenwert unter Verwendung der Ortszeit zurück.|  
|[getMonth-Methode](../../javascript/reference/getmonth-method-date-javascript.md)|Gibt den Monatswert unter Verwendung der Ortszeit zurück.|  
|[getSeconds-Methode](../../javascript/reference/getseconds-method-date-javascript.md)|Gibt den Sekundenwert unter Verwendung der Ortszeit zurück.|  
|[getTime-Methode](../../javascript/reference/gettime-method-date-javascript.md)|Gibt den Zeitwert eines `Date`-Objekts als die Anzahl der Millisekunden zurück, die seit Mitternacht am 1. Januar 1970 verstrichen sind.|  
|[getTimezoneOffset-Methode](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Gibt den Unterschied zwischen der Zeit auf dem Hostcomputer und UTC (Universal Coordinated Time) in Minuten zurück.|  
|[getUTCDate-Methode](../../javascript/reference/getutcdate-method-date-javascript.md)|Gibt den Wert für einen Tag des Monats unter Verwendung der UTC zurück.|  
|[getUTCDay-Methode](../../javascript/reference/getutcday-method-date-javascript.md)|Gibt den Wert für einen Tag des Woche unter Verwendung der UTC zurück.|  
|[getUTCFullYear-Methode](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Gibt den Wert des Jahres unter Verwendung der UTC zurück.|  
|[getUTCHours-Methode](../../javascript/reference/getutchours-method-date-javascript.md)|Gibt den Stundenwert unter Verwendung der UTC zurück.|  
|[getUTCMilliseconds-Methode](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Gibt den Millisekundenwert unter Verwendung der UTC zurück.|  
|[getUTCMinutes-Methode](../../javascript/reference/getutcminutes-method-date-javascript.md)|Gibt den Minutenwert unter Verwendung der UTC zurück.|  
|[getUTCMonth-Methode](../../javascript/reference/getutcmonth-method-date-javascript.md)|Gibt den Monatswert unter Verwendung der UTC zurück.|  
|[getUTCSeconds-Methode](../../javascript/reference/getutcseconds-method-date-javascript.md)|Gibt den Sekundenwert unter Verwendung der UTC zurück.|  
|[getVarDate-Methode](../../javascript/reference/getvardate-method-date-javascript.md)|Gibt den `Date`-Wert in einem -Objekt zurück.|  
|[getYear-Methode](../../javascript/reference/getyear-method-date-javascript.md)|Gibt den Jahreswert zurück.|  
|[hasOwnProperty-Methode](../../javascript/reference/hasownproperty-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt über eine Eigenschaft mit dem angegebenen Namen verfügt.|  
|[IsPrototypeOf-Methode](../../javascript/reference/isprototypeof-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt in der Prototypenkette eines anderen Objekts vorhanden ist.|  
|[propertyIsEnumerable-Methode](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Gibt einen booleschen Wert zurück, der angibt, ob eine angegebene Eigenschaft Teil eines Objekts ist, und ob sie aufzählbar ist.|  
|[setDate-Methode](../../javascript/reference/setdate-method-date-javascript.md)|Legt den numerischen Tag des Monats anhand der Ortszeit fest.|  
|[setFullYear-Methode](../../javascript/reference/setfullyear-method-date-javascript.md)|Legt den Wert des Jahres anhand der Ortszeit fest.|  
|[setHours-Methode](../../javascript/reference/sethours-method-date-javascript.md)|Legt den Stundenwert anhand der Ortszeit fest.|  
|[setMilliseconds-Methode](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Legt den Millisekundenwert anhand der Ortszeit fest.|  
|[setMinutes-Methode](../../javascript/reference/setminutes-method-date-javascript.md)|Legt den Minutenwert anhand der Ortszeit fest.|  
|[setMonth-Methode](../../javascript/reference/setmonth-method-date-javascript.md)|Legt den Monatswert anhand der Ortszeit fest.|  
|[setSeconds-Methode](../../javascript/reference/setseconds-method-date-javascript.md)|Legt den Sekundenwert anhand der Ortszeit fest.|  
|[setTime-Methode](../../javascript/reference/settime-method-date-javascript.md)|Legt die Werte für Datum und Uhrzeit im `Date`-Objekt fest.|  
|[setUTCDate-Methode](../../javascript/reference/setutcdate-method-date-javascript.md)|Legt den numerischen Tag des Monats anhand der UTC fest.|  
|[setUTCFullYear-Methode](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Legt den Wert des Jahres anhand der UTC fest.|  
|[setUTCHours-Methode](../../javascript/reference/setutchours-method-date-javascript.md)|Legt den Stundenwert anhand der UTC fest.|  
|[setUTCMilliseconds-Methode](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Legt den Millisekundenwert anhand der UTC fest.|  
|[setUTCMinutes-Methode](../../javascript/reference/setutcminutes-method-date-javascript.md)|Legt den Minutenwert anhand der UTC fest.|  
|[setUTCMonth-Methode](../../javascript/reference/setutcmonth-method-date-javascript.md)|Legt den Monatswert anhand der UTC fest.|  
|[setUTCSeconds-Methode](../../javascript/reference/setutcseconds-method-date-javascript.md)|Legt den Sekundenwert anhand der UTC fest.|  
|[setYear-Methode](../../javascript/reference/setyear-method-date-javascript.md)|Legt den Wert des Jahres anhand der Ortszeit fest.|  
|[toDateString-Methode](../../javascript/reference/todatestring-method-date-javascript.md)|Gibt ein Datum als Zeichenfolgenwert zurück.|  
|[toGMTString-Methode](../../javascript/reference/togmtstring-method-date-javascript.md)|Gibt ein Datum zurück, das unter Verwendung der GMT (Greenwich Mean Time) in eine Zeichenfolge konvertiert wurde.|  
|[toISOString-Methode](../../javascript/reference/toisostring-method-date-javascript.md)|Gibt ein Datum als Zeichenfolgenwert im ISO-Format zurück.|  
|[toJSON-Methode](../../javascript/reference/tojson-method-date-javascript.md)|Wird verwendet, um Daten eines Objekttyps vor der JSON-Serialisierung zu transformieren.|  
|[toLocaleDateString-Methode](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Gibt unter Berücksichtigung des aktuellen Gebietsschemas der Hostumgebung ein Datum als Zeichenfolge zurück.|  
|[ToLocaleString-Methode](../../javascript/reference/tolocalestring-date.md)|Gibt ein Objekt zurück, das unter Verwendung des aktuellen Gebietsschemas in eine Zeichenfolge konvertiert wurde.|  
|[toLocaleTimeString-Methode](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Gibt eine Uhrzeit als Zeichenfolgenwert zurück, der dem aktuellen Gebietsschema der Hostumgebung entspricht.|  
|[ToString-Methode](../../javascript/reference/tostring-method-date.md)|Gibt eine Zeichenfolgendarstellung eines Objekts zurück.|  
|[toTimeString-Methode](../../javascript/reference/totimestring-method-date-javascript.md)|Gibt eine Uhrzeit als Zeichenfolgenwert zurück.|  
|[toUTCString-Methode](../../javascript/reference/toutcstring-method-date-javascript.md)|Gibt ein Datum zurück, das anhand der UTC in eine Zeichenfolge konvertiert wurde.|  
|[ValueOf-Methode](../../javascript/reference/valueof-method-date.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
## <a name="see-also"></a>Siehe auch  
 [Berechnen von Datums- und Uhrzeitangaben (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Datum- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md)