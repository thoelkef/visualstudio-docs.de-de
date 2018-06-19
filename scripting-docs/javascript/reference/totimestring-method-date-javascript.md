---
title: ToTimeString-Methode (Datum) (JavaScript) | Microsoft Docs
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
- toTimeString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toTimeString method
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d9af1f688fee0c066158d8504e00f22af9b3a21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640070"
---
# <a name="totimestring-method-date-javascript"></a>toTimeString-Methode (Datum) (JavaScript)
Gibt eine Uhrzeit als Zeichenfolgenwert zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
objDate. toTimeString( )  
```  
  
## <a name="remarks"></a>Hinweise  
 Der erforderliche `objDate`-Verweis ist ein `Date`-Objekt.  
  
 Die `toTimeString` Methode gibt einen Zeichenfolgenwert, der die Uhrzeit in der aktuellen Zeitzone enthält.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel die Gültigkeitsdauer wird nach Mitternacht am 1. Januar 1970 UTC auf 2000 Millisekunden festgelegt, und klicken Sie dann diese geschrieben wird.  
  
```JavaScript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ToDateString-Methode (Datum)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString-Methode (Datum)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)