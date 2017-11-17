---
title: SetUTCMonth-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth-Methode (Datum) (JavaScript)
Legt den Monatswert fest, dem `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numMonth`  
 Erforderlich. Ein numerischer Wert, der den Monat gleich ist. Der Wert für Januar ist 0 und andere Monatswerte hintereinander folgen.  
  
 `dateVal`  
 Dies ist optional. Ein numerischer Wert, der den Tag des Monats darstellt. Wenn es nicht angegeben ist, den Wert von einem Aufruf der `getUTCDate` Methode wird verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Um den Monatswert unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setMonth` Methode.  
  
 Wenn der Wert des `numMonth` ist größer als 11 (Januar ist Monat 0), oder eine negative Zahl, gespeicherte Jahr wird entsprechend inkrementiert oder dekrementiert. Beispielsweise ist das gespeicherte Datum "5. Januar 1996 00:00:00.00", und **setUTCMonth(14)** wird aufgerufen, um das Datum geändert wird "5. März 1997 00:00:00.00."  
  
 Die **SetUTCFullYear** Methode kann verwendet werden, um das Jahr, Monat und Tag des Monats festgelegt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCMonth`-Methode veranschaulicht.  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMonth-Methode (Datum)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [GetUTCMonth-Methode (Datum)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth-Methode (Datum)](../../javascript/reference/setmonth-method-date-javascript.md)