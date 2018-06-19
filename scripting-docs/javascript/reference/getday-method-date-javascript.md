---
title: GetDay-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getDay
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetDay method
- Date object
- dates, returning day of the week
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1749eca5aceee76947a0162f22700f32525fdec0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636680"
---
# <a name="getday-method-date-javascript"></a>getDay-Methode (Datum) (JavaScript)
Ruft den Tag der Woche unter Verwendung der Ortszeit ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj. getDay()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine ganze Zahl zwischen 0 und 6, den Tag der Woche (Sonntag ist 0, Samstag ist 6).  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie zum Abrufen des Tages Universal Coordinated Time (UTC) mit der `getUTCDay` Methode.  
  
 Im folgenden Beispiel wird die Verwendung der `getDay`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [getUTCDay-Methode (Datum)](../../javascript/reference/getutcday-method-date-javascript.md)