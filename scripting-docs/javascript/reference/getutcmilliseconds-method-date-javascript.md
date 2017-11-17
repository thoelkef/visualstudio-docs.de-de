---
title: GetUTCMilliseconds-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- UTC times, returning
- getUTCMilliseconds method
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fb7cf202c8511bec00c10dc5b8c23bd198d8700
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getutcmilliseconds-method-date-javascript"></a>getUTCMilliseconds-Methode (Datum) (JavaScript)
Ruft die Millisekunden von einem `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen Millisekundenwert, der kann im Bereich zwischen 0 und 999 zurück.  
  
## <a name="remarks"></a>Hinweise  
 Um die Anzahl der Millisekunden in lokale Zeit zu erhalten, verwenden Sie die `getMilliseconds` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCMilliseconds`-Methode veranschaulicht.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMilliseconds-Methode (Datum)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [SetMilliseconds-Methode (Datum)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds-Methode (Datum)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)