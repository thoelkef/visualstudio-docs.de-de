---
title: Date.UTC-Funktion (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC-Funktion (JavaScript)
Gibt die Anzahl der Millisekunden zwischen Mitternacht des 1. Januar 1970, koordinierte Weltzeit (UTC) (oder GMT) und dem angegebenen Datum.  
  
## <a name="syntax"></a>Syntax  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>Parameter  
 `year`  
 Erforderlich. Die vollständige Jahr Bezeichnung ist erforderlich für die übergreifende Jahrhunderts in Sachen Datum Genauigkeit. Wenn `year` liegt zwischen 0 und 99 verwendet wird, klicken Sie dann `year` wird davon ausgegangen, dass 1900 + `year`.  
  
 `month`  
 Erforderlich. Der Monat als ganze Zahl zwischen 0 und 11 (Januar bis Dezember).  
  
 `day`  
 Erforderlich. Das Datum als ganze Zahl zwischen 1 und 31.  
  
 `hours`  
 Dies ist optional. Muss angegeben werden, wenn auch `minutes` angegeben wird. Eine ganze Zahl zwischen 0 und 23 (Mitternacht bis 23 Uhr), die die Stunde angibt.  
  
 `minutes`  
 Dies ist optional. Muss angegeben werden, wenn auch `seconds` angegeben wird. Eine ganze Zahl zwischen 0 und 59, die die Minuten angibt.  
  
 `seconds`  
 Dies ist optional. Muss angegeben werden, wenn auch `milliseconds` angegeben wird. Eine ganze Zahl zwischen 0 und 59, die die Sekunden angibt.  
  
 `ms`  
 Dies ist optional. Eine ganze Zahl zwischen 0 und 999, die die Millisekunden angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die `Date.UTC` Funktion gibt die Anzahl der Millisekunden zwischen Mitternacht, 1. Januar 1970 UTC und dem angegebenen Datum zurück. Dieser Rückgabewert kann verwendet werden, der `setTime` Methode und in der `Date` Objektkonstruktor. Wenn der Wert eines Arguments größer als dessen Bereich ist bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Wenn Sie z. B. 150 Sekunden angeben, macht [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] daraus 2 Minuten und 30 Sekunden.  
  
 Der Unterschied zwischen der `Date.UTC` Funktion und die `Date` Objektkonstruktors, der ein Datum akzeptiert wird, die die `Date.UTC` Funktion davon ausgeht, UTC, und die `Date` Objektkonstruktor Ortszeit.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Date.UTC`-Funktion.  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [setTime-Methode (Datum)](../../javascript/reference/settime-method-date-javascript.md)