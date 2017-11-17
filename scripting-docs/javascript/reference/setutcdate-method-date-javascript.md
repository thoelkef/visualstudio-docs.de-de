---
title: SetUTCDate-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate-Methode (Datum) (JavaScript)
Legt den numerischen Tag des Monats in der `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 *numDate*  
 Erforderlich. Ein numerischer Wert, der den Tag des Monats gleich ist.  
  
## <a name="remarks"></a>Hinweise  
 Um den Tag des Monats unter Verwendung der Ortszeit festzulegen, verwenden die `setDate` Methode.  
  
 Wenn der Wert der *NumDate* ist größer als die Anzahl der Tage im Monat in gespeicherten der **Datum** Objekt oder eine negative Zahl ist, wird das Datum wird in ein Datum gleich festgelegt *NumDate* minus die Anzahl der Tage im Monat gespeicherte. Das gespeicherte Datum beispielsweise am 5. Januar 1996 und **setUTCDate(32)** aufgerufen wird, werden die Änderungen am 1. Februar 1996 Datum. Negative Zahlen haben ein ähnliches Verhalten.  
  
 Die **SetUTCFullYear** Methode kann verwendet werden, um das Jahr, Monat und Tag des Monats festgelegt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCDate`-Methode veranschaulicht.  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetDate-Methode (Datum)](../../javascript/reference/getdate-method-date-javascript.md)   
 [GetUTCDate-Methode (Datum)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate-Methode (Datum)](../../javascript/reference/setdate-method-date-javascript.md)