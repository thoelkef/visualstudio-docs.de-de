---
title: SetHours-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>setHours-Methode (Datum) (JavaScript)
Legt den Stundenwert in die `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numHours`  
 Erforderlich. Ein numerischer Wert, der gleich dem Stundenwert ist.  
  
 `numMin`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Minutenwert ist. Muss angegeben werden, wenn eines der folgenden Argumente verwendet wird.  
  
 `numSec`  
 Dies ist optional. Ein numerischer Wert gleich dem Sekundenwert. Muss angegeben werden, wenn das folgende Argument verwendet wird.  
  
 `numMilli`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Millisekundenwert ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie ein optionales Argument nicht angeben. Z. B. wenn die `numMinutes` Argument nicht angegeben wird, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem `getMinutes` Methode.  
  
 Um den Stundenwert unter Verwendung der koordinierten Weltzeit (UTC) festzulegen, verwenden Sie die `setUTCHours` Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Wenn das gespeicherte Datum z. B. "5. Januar 1996 00:00:00", und **setHours(30)** ist aufgerufen wird, wird das Datum in geändert "6. Jan 1996 06:00:00." Negative Zahlen haben ein ähnliches Verhalten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setHours`-Methode veranschaulicht.  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetHours-Methode (Datum)](../../javascript/reference/gethours-method-date-javascript.md)   
 [GetUTCHours-Methode (Datum)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours-Methode (Datum)](../../javascript/reference/setutchours-method-date-javascript.md)