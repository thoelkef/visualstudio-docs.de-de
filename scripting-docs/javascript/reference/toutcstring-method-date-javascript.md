---
title: ToUTCString-Methode (Datum) (JavaScript) | Microsoft Docs
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
- toUTCString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC dates, converting to strings
- toUTCString method
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bd5efc43152c1af2dd467b73dce235e8fe52f29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640740"
---
# <a name="toutcstring-method-date-javascript"></a>toUTCString-Methode (Datum) (JavaScript)
Gibt ein Datum in einer Zeichenfolge in Universal Coordinated Time (UTC) konvertiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.toUTCString()   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `dateObj` Verweis ist "any" `Date` Objekt.  
  
 Die `toUTCString` Methode gibt ein `String` Objekt, das Format UTC-Konvention in einem benutzerfreundlichen enthält, einfach Formular gelesen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toUTCString`-Methode veranschaulicht.  
  
```JavaScript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [toGMTString-Methode (Datum)](../../javascript/reference/togmtstring-method-date-javascript.md)