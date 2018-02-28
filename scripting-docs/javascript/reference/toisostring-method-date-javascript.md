---
title: ToISOString-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toISOString method [JavaScript]
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31559e1bc44849573ec7dc903411ce98b0a4440d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="toisostring-method-date-javascript"></a>toISOString-Methode (Datum) (JavaScript)
Gibt ein Datum als Zeichenfolgenwert im ISO-Format zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
  
objDate.toISOString()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Zeichenfolgendarstellung des Datums in internationalen Organisation für Normung (ISO)-Format.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn `objDate` enthält kein gültiges Datum ist, eine `RangeError` Ausnahme wird ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Das ISO-Format ist eine Vereinfachung des ISO 8601-Format. Weitere Informationen finden Sie unter [Datum- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md).  
  
 Die Zeitzone ist immer UTC, durch das Suffix "Z" in der Ausgabe gekennzeichnet.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toISOString`-Methode veranschaulicht.  
  
```JavaScript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Date-Objekt](../../javascript/reference/date-object-javascript.md)   
 [Datum- und Uhrzeitzeichenfolgen](../../javascript/date-and-time-strings-javascript.md)