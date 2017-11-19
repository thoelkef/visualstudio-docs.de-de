---
title: GetTime-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetTime method
- time method
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a31e542445e89a0e2f3364d36ae44f8d2d4cf9bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="gettime-method-date-javascript"></a>getTime-Methode (Datum) (JavaScript)
Ruft den Zeitwert in Millisekunden an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getTime()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt die Anzahl der Millisekunden zwischen Mitternacht des 1. Januar 1970 und dem Time-Werten in der `Date` Objekt. Der Datumsbereich ist etwa 285.616 Jahre von beiden Seiten von Mitternacht, 1. Januar 1970 an. Negative Zahlen geben Datumsangaben vor 1970 an.  
  
## <a name="remarks"></a>Hinweise  
 Wenn mehrere Datum und Uhrzeit-Berechnungen durchführen zu können, empfiehlt es sich um Variablen, die gleich der Anzahl der Millisekunden in einem Tag, Stunde oder Minute zu definieren. Zum Beispiel:  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 Finden Sie unter [berechnen von Datums- und Uhrzeitangaben (JavaScript)](../../javascript/calculating-dates-and-times-javascript.md) für Weitere Informationen zum Verwenden der `getTime` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getTime`-Methode gezeigt.  
  
```JavaScript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [setTime-Methode (Datum)](../../javascript/reference/settime-method-date-javascript.md)