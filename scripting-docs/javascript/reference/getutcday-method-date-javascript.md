---
title: GetUTCDay-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getUTCDay
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDay method
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ee9953a7abf548ef15cc124e09b914af360ca23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getutcday-method-date-javascript"></a>getUTCDay-Methode (Datum) (JavaScript)
Ruft den Tag der Woche mit Universal Coordinated Time (UTC) ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 (Sonntag) und 6 (Samstag), die den Tag der Woche darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie zum Abrufen der Tag der Woche unter Verwendung der Ortszeit die `getDate` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCDay`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [getDay-Methode (Datum)](../../javascript/reference/getday-method-date-javascript.md)