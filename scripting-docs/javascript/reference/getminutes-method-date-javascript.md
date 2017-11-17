---
title: GetMinutes-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>getMinutes-Methode (Datum) (JavaScript)
Ruft die Minuten von einem `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück. 0 (null) wird zurückgegeben, dass die Zeit weniger als eine Minute nach der vollen Stunde ist. Wenn ein `Date` Objekt ohne Angabe der Uhrzeit erstellt wurde, wird standardmäßig der Minutenwert ist 0.  
  
## <a name="remarks"></a>Hinweise  
 Um den Minutenwert unter Verwendung der koordinierten Weltzeit (UTC) zu erhalten, verwenden die `getUTCMinutes` Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie die `getMinutes` Methode.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetUTCMinutes-Methode (Datum)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [SetMinutes-Methode (Datum)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes-Methode (Datum)](../../javascript/reference/setutcminutes-method-date-javascript.md)