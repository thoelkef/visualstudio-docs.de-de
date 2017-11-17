---
title: GetSeconds-Methode (Datum) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="getseconds-method-date-javascript"></a>getSeconds-Methode (Datum) (JavaScript)
Ruft die Sekunden des ein `Date` -Objekt unter Verwendung der Ortszeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine ganze Zahl zwischen 0 und 59 zurück. 0 (null) wird zurückgegeben, wenn die Zeit weniger als einer Sekunde in die aktuelle Minute ist. Wenn ein `Date` Objekt wurde erstellt, ohne dabei den Zeitpunkt, der Sekundenwert beträgt standardmäßig 0.  
  
## <a name="remarks"></a>Hinweise  
 Um die Sekunden Wert unter Verwendung der koordinierten Weltzeit (UTC) abzurufen, verwenden die `getUTCSeconds` Methode.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `getSeconds`-Methode gezeigt.  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetUTCSeconds-Methode (Datum)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [SetSeconds-Methode (Datum)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds-Methode (Datum)](../../javascript/reference/setutcseconds-method-date-javascript.md)