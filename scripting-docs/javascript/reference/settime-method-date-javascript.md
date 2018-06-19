---
title: SetTime-Methode (Datum) (JavaScript) | Microsoft Docs
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
- setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640820"
---
# <a name="settime-method-date-javascript"></a>setTime-Methode (Datum) (JavaScript)
Legt die Werte für Datum und Uhrzeit im `Date`-Objekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>Parameter  
 `dateObj`  
 Erforderlich. Ein `Date`-Objekt.  
  
 *Millisekunden*  
 Erforderlich. Ein numerischer Wert, der die Anzahl der verstrichenen Millisekunden seit Mitternacht des 1. Januar 1970 GMT darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn *Millisekunden* ist negativ ist, gibt ein Datum früher als 1970 liegt. Der Datumsbereich, der verfügbar ist, etwa 285.616 Jahre von beiden Seiten des 1970.  
  
 Festlegen von Datum und Uhrzeit mit der `setTime` Methode ist unabhängig von der Zeitzone.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `setTime`-Methode veranschaulicht.  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [getTime-Methode (Datum)](../../javascript/reference/gettime-method-date-javascript.md)