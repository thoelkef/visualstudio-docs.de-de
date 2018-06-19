---
title: GetUTCMinutes-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636810"
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes-Methode (Datum) (JavaScript)
Ruft die Minuten von einem `Date` -Objekt unter Verwendung der koordinierten Weltzeit (UTC).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück. 0 (null) wird zurückgegeben, dass die Zeit weniger als eine Minute nach der vollen Stunde ist. Wenn ein `Date` Objekt ohne Angabe der Uhrzeit erstellt wurde, wird standardmäßig die UTC Minutenwert ist 0. In anderen Zeitzonen können sie sich unterscheiden.  
  
## <a name="remarks"></a>Hinweise  
 Um die Anzahl von Minuten gespeichert, unter Verwendung der Ortszeit zu erhalten, verwenden die `getMinutes` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getUTCMinutes`-Methode veranschaulicht.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetMinutes-Methode (Datum)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [SetMinutes-Methode (Datum)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes-Methode (Datum)](../../javascript/reference/setutcminutes-method-date-javascript.md)