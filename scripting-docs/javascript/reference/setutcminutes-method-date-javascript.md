---
title: SetUTCMinutes-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setutcminutes-method-date-javascript"></a>setUTCMinutes-Methode (Datum) (JavaScript)
Legt den Minutenwert fest, dem `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numMinutes`  
 Erforderlich. Ein numerischer Wert, der gleich dem Minutenwert ist. Muss angegeben werden, wenn eines der folgenden Argumente verwendet wird.  
  
 *numSeconds*  
 Dies ist optional. Ein numerischer Wert gleich dem Sekundenwert. Muss angegeben werden, wenn `numMilli` verwendet wird.  
  
 `numMilli`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Millisekundenwert ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie ein optionales Argument nicht angeben. Z. B. wenn die *NumSeconds* Argument nicht angegeben ist, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem `getUTCSeconds` Methode.  
  
 Um den Minutenwert unter Verwendung der Ortszeit zu ändern, verwenden Sie die `setMinutes` Methode.  
  
 Wenn der Wert eines Arguments größer als dessen Bereich ist bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Beispielsweise ist das gespeicherte Datum "5. Januar 1996 00:00:00.00", und **setUTCMinutes(70)** ist aufgerufen wird, wird das Datum in geändert "5. Januar 1996 01:10:00.00."  
  
 Die **SetUTCHours** Methode kann verwendet werden, um die Stunden, Minuten, Sekunden und Millisekunden festgelegt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `setUTCMinutes` Methode:  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMinutes-Methode (Datum)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [GetUTCMinutes-Methode (Datum)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes-Methode (Datum)](../../javascript/reference/setminutes-method-date-javascript.md)