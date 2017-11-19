---
title: GetMonth-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>getMonth-Methode (Datum) (JavaScript)
Ruft den Monat, unter Verwendung der Ortszeit ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die `getMonth` -Methode gibt eine ganze Zahl zwischen 0 (Januar) und 11 (Dezember) zurück. Für eine `Date` erstellt, die mit "5. Januar 1996" `getMonth` gibt 0 zurück.  
  
## <a name="remarks"></a>Hinweise  
 Um den Monatswert unter Verwendung der koordinierten Weltzeit (UTC) zu erhalten, verwenden die `getUTCMonth` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getMonth`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetUTCMonth-Methode (Datum)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [SetMonth-Methode (Datum)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth-Methode (Datum)](../../javascript/reference/setutcmonth-method-date-javascript.md)