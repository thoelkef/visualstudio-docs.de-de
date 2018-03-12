---
title: SetDate-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>setDate-Methode (Datum) (JavaScript)
Legt den numerischen Tag des Monats-Wert, der die `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numDate`  
 Erforderlich. Ein numerischer Wert, der den Tag des Monats gleich ist.  
  
## <a name="remarks"></a>Hinweise  
 Um den Tag des Monats unter Verwendung der Universal Coordinated Time (UTC) festzulegen, verwenden Sie die `setUTCDate` Methode.  
  
 Wenn der Wert des `numDate` ist größer als die Anzahl der Tage im Monat, dem Datum führt ein Rollup über auf einen späteren Monat / Jahr. Das gespeicherte Datum beispielsweise am 5. Januar 1996 und `setDate(32)` aufgerufen wird, werden die Änderungen am 1. Februar 1996 Datum. Wenn `numDate` ist eine negative Zahl, die an einer früheren Monat und/oder Jahr erstellt ein Rollup der Datum. Das gespeicherte Datum beispielsweise am 5. Januar 1996 und `setDate(-32)` aufgerufen wird, werden die Änderungen am 29. November 1995 Datum.  
  
 Die [SetFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md) kann verwendet werden, um das Jahr, Monat und Tag des Monats festzulegen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setDate`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [SetFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [SetMonth-Methode (Datum)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate-Methode (Datum)](../../javascript/reference/setutcdate-method-date-javascript.md)