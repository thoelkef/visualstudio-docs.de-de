---
title: SetSeconds-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640170"
---
# <a name="setseconds-method-date-javascript"></a>setSeconds-Methode (Datum) (JavaScript)
Legt den Sekundenwert fest der `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 *numSeconds*  
 Erforderlich. Ein numerischer Wert gleich dem Sekundenwert.  
  
 `numMilli`  
 Dies ist optional. Ein numerischer Wert, der gleich dem Millisekundenwert ist.  
  
## <a name="remarks"></a>Hinweise  
 Alle **festgelegt** Methoden, die optionale Argumente verwenden, den Rückgabewert aus entsprechenden **abrufen** Methoden, wenn Sie ein optionales Argument nicht angeben. Z. B. wenn die `numMilli` Argument nicht angegeben wird, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verwendet den Rückgabewert aus dem **GetMilliseconds** Methode.  
  
 Um den Sekundenwert unter Verwendung der Universal Coordinated Time (UTC) festzulegen, verwenden Sie die `setUTCSeconds` Methode.  
  
 Ist der Wert eines Arguments größer als dessen Bereich bzw. eine negative Zahl, werden andere gespeicherte Werte entsprechend geändert. Wenn das gespeicherte Datum z. B. "5. Januar 1996 00:00:00" und **setSeconds(150)** ist aufgerufen wird, wird das Datum in geändert "am 5. Januar 1996 00:02:30 Uhr fortgeführt."  
  
 Die `setHours` Methode kann verwendet werden, um die Stunden, Minuten, Sekunden und Millisekunden festgelegt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setSeconds`-Methode veranschaulicht.  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetSeconds-Methode (Datum)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [GetUTCSeconds-Methode (Datum)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds-Methode (Datum)](../../javascript/reference/setutcseconds-method-date-javascript.md)