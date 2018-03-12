---
title: SetUTCHours-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>setUTCHours-Methode (Datum) (JavaScript)
Legt den Stundenwert der `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numHours`  
 Erforderlich. Ein numerischer Wert, der gleich dem Stundenwert ist.  
  
 `numMin`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Minutenwert ist. Muss angegeben werden, wenn entweder `numSec` oder `numMilli` verwendet werden.  
  
 `numSec`  
 Dies ist optional. Ein numerischer Wert gleich dem Sekundenwert. Muss angegeben werden, wenn `numMilli` Argument verwendet wird.  
  
 `numMilli`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Millisekundenwert ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie ein optionales Argument nicht angeben. Z. B. wenn die `numMin` Argument nicht angegeben wird, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem `getUTCMinutes` Methode.  
  
 Um den Stundenwert unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setHours` Methode.  
  
 Wenn der Wert eines Arguments größer als dessen Bereich ist bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Beispielsweise ist das gespeicherte Datum "5. Januar 1996 00:00:00.00", und **setUTCHours(30)** wird aufgerufen, um das Datum geändert wird "6. Jan 1996 06:00:00.00."  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCHours`-Methode veranschaulicht.  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetHours-Methode (Datum)](../../javascript/reference/gethours-method-date-javascript.md)   
 [GetUTCHours-Methode (Datum)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours-Methode (Datum)](../../javascript/reference/sethours-method-date-javascript.md)