---
title: GetMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- getMilliseconds method
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33e5fc54dffbe06e47f0978e6cef94b1f650c90f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636610"
---
# <a name="getmilliseconds-method-date-javascript"></a>getMilliseconds-Methode (Datum) (JavaScript)
Ruft ab, der ein Datum unter Verwendung der Ortszeit in Millisekunden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt die Millisekunden des Datums zurück. Der Wert kann zwischen 0 und 999 liegen. Wenn ein Datum ohne die Millisekunden erstellt wurde, ist der zurückgegebene Wert 0.  
  
## <a name="remarks"></a>Hinweise  
 Um die Anzahl der Millisekunden in Universal Coordinated Time (UTC) abzurufen, verwenden die `getUTCMilliseconds` Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die **GetMilliseconds** Methode.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetUTCMilliseconds-Methode (Datum)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [SetMilliseconds-Methode (Datum)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds-Methode (Datum)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)