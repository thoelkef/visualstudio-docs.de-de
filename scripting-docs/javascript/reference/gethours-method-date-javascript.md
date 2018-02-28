---
title: GetHours-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="gethours-method-date-javascript"></a>getHours-Methode (Datum) (JavaScript)
Ruft die Stunden in ein Datum unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine ganze Zahl zwischen 0 und 23, die Anzahl der seit Mitternacht vergangenen Stunden angibt. 0 (null) wird zurückgegeben, wenn die Uhrzeit früher als 1:00:00 Uhr ist. Wenn ein `Date` Objekt wurde erstellt, ohne dabei den Zeitpunkt, die Stunde ist standardmäßig 0.  
  
## <a name="remarks"></a>Hinweise  
 Um den Stundenwert unter Verwendung der koordinierten Weltzeit (UTC) zu erhalten, verwenden die `getUTCHours` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getHours`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetUTCHours-Methode (Datum)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [SetHours-Methode (Datum)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours-Methode (Datum)](../../javascript/reference/setutchours-method-date-javascript.md)