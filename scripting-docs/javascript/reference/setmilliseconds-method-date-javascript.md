---
title: SetMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="setmilliseconds-method-date-javascript"></a>setMilliseconds-Methode (Datum) (JavaScript)
Legt den Millisekundenwert fest, dem `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 `numMilli`  
 Erforderlich. Ein numerischer Wert, der den Millisekundenwert gleich ist.  
  
## <a name="remarks"></a>Hinweise  
 Um den Millisekundenwert unter Verwendung der koordinierten Weltzeit (UTC) festzulegen, verwenden Sie die `setUTCMilliseconds` Methode.  
  
 Wenn der Wert des `numMilli` ist größer als 999 oder eine negative Zahl, die gespeicherten Anzahl der Sekunden (und Minuten, Stunden usw. bei Bedarf) wird inkrementiert einer entsprechenden Menge.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setMilliseconds`-Methode veranschaulicht.  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMilliseconds-Methode (Datum)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [GetUTCMilliseconds-Methode (Datum)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds-Methode (Datum)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)