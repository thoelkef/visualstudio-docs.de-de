---
title: SetUTCMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- dates, UTC
- UTC times, setting
- setUTCMilliseconds method
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 279d00b256b3b0763e2f15f549fdc6ee81c20254
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640080"
---
# <a name="setutcmilliseconds-method-date-javascript"></a>setUTCMilliseconds-Methode (Datum) (JavaScript)
Legt den Millisekundenwert fest, dem `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numMilli`  
 Erforderlich. Ein numerischer Wert, der den Millisekundenwert gleich ist.  
  
## <a name="remarks"></a>Hinweise  
 Um den Millisekundenwert unter Verwendung der Ortszeit festzulegen, verwenden Sie die `setMilliseconds` Methode.  
  
 Wenn der Wert des `numMilli` ist größer als 999 oder eine negative Zahl, die gespeicherten Anzahl der Sekunden (und Minuten, Stunden usw., falls erforderlich) wird inkrementiert einer entsprechenden Menge.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setUTCMilliseconds`-Methode veranschaulicht.  
  
```JavaScript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMilliseconds-Methode (Datum)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [GetUTCMilliseconds-Methode (Datum)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds-Methode (Datum)](../../javascript/reference/setmilliseconds-method-date-javascript.md)