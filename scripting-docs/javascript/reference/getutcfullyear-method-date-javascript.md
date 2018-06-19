---
title: GetUTCFullYear-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getUTCFullYear method
- Date object
- UTCFullYear method
- dates, UTC
- UTC dates, returning
- Full Year method
- UTC dates, getting
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8268631a96eed1f61ef4ba908b78680c8522096
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636850"
---
# <a name="getutcfullyear-method-date-javascript"></a>getUTCFullYear-Methode (Datum) (JavaScript)
Ruft das Jahr mit Universal Coordinated Time (UTC) ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Jahr als vierstellige Zahl zurückgegeben. Jahre als zwei Ziffern im angegebenen der `Date` Konstruktor oder im `setFullYear` wird angenommen, dass in der 20. Jahrhunderts angenommen, "5/14/12" `getUTCFullYear` "1912" zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie zum Abrufen des Jahres unter Verwendung der Ortszeit die `getFullYear` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCFullYear`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetFullYear-Methode (Datum)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [SetFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear-Methode (Datum)](../../javascript/reference/setutcfullyear-method-date-javascript.md)