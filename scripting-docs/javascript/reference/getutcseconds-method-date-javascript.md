---
title: GetUTCSeconds-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636830"
---
# <a name="getutcseconds-method-date-javascript"></a>getUTCSeconds-Methode (Datum) (JavaScript)
Ruft die Sekunden des ein `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück. 0 (null) wird zurückgegeben, wenn die Zeit weniger als einer Sekunde in die aktuelle Minute ist. Wenn ein `Date` Objekt ohne Angabe der Uhrzeit erstellt wurde, wird standardmäßig die UTC Sekundenwert ist 0.  
  
## <a name="remarks"></a>Hinweise  
 Um die Anzahl der Sekunden in lokale Zeit zu erhalten, verwenden Sie die `getSeconds` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCSeconds`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetSeconds-Methode (Datum)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [SetSeconds-Methode (Datum)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds-Methode (Datum)](../../javascript/reference/setutcseconds-method-date-javascript.md)