---
title: GetFullYear-Methode (Datum) (JavaScript) | Microsoft Docs
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
- getFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, returning year
- Date object
- getFullYear method
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 211d6c86435e39eb75b9b1ce3415738541ca07db
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636750"
---
# <a name="getfullyear-method-date-javascript"></a>getFullYear-Methode (Datum) (JavaScript)
Ruft das Jahr, unter Verwendung der Ortszeit ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.getFullYear()   
```  
  
#### <a name="parameters"></a>Parameter  
 Der erforderliche `dateObj` -Verweis ist ein `Date` -Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Jahr als vierstellige Zahl. Beispielsweise wird das Jahr 1976 als 1976 zurückgegeben. Jahre als zwei Ziffern im angegebenen der `Date` Konstruktor oder im `setFullYear` wird angenommen, dass in der 20. Jahrhunderts angenommen, "5/14/12" `getFullYear` "1912" zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Um das Jahr mit Universal Coordinated Time (UTC) zu erhalten, verwenden die `getUTCFullYear` Methode.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **GetFullYear** Methode.  
  
```JavaScript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetUTCFullYear-Methode (Datum)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [SetFullYear-Methode (Datum)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear-Methode (Datum)](../../javascript/reference/setutcfullyear-method-date-javascript.md)