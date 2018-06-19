---
title: Date.Parse-Funktion (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- parse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parse function [JavaScript]
- Date.parse function [JavaScript]
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a73fda66ef24df17a5213a182c04667fc4dfabf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636140"
---
# <a name="dateparse-function-javascript"></a>Date.parse-Funktion (JavaScript)
Analysiert eine Zeichenfolge mit einem Datum und gibt die Anzahl der Millisekunden zwischen diesem Datum und Mitternacht des 1. Januars 1970 zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Date.parse(dateVal)   
```  
  
## <a name="remarks"></a>Hinweise  
 Das erforderliche `dateVal`-Argument ist entweder eine Zeichenfolge, die ein Datum enthält, oder ein Wert, der aus einem ActiveX-Objekt oder einem anderen Objekt abgerufen wird. Für Informationen zu Datum, die Zeichenfolgen der `Date.parse` Funktion analysiert werden kann. finden Sie unter [Datum- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md).  
  
 Die `Date.parse`-Funktion gibt einen ganzzahligen Wert zurück, der der Anzahl der Millisekunden zwischen Mitternacht des 1. Januar 1970 und dem in `dateVal` angegebenen Datum entspricht.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `Date.parse`-Funktion.  
  
```JavaScript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Differenz zwischen dem angegebenen Datum und dem 1.1.1970 zurückgegeben.  
  
```JavaScript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [getDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)