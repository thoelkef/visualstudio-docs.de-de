---
title: Instanceof-Operator (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>instanceof-Operator (JavaScript)
Gibt einen booleschen Wert zurück, der angibt, ob ein Objekt eine Instanz einer bestimmten Klasse ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Parameter  
 `result`  
 Erforderlich. Beliebige Variable.  
  
 `object`  
 Erforderlich. Beliebiger Objektausdruck.  
  
 `class`  
 Erforderlich. Eine beliebige definierte Objektklasse.  
  
## <a name="remarks"></a>Hinweise  
 Der `instanceof`-Operator gibt `true` zurück, wenn `object` eine Instanz von `class` ist. Er gibt `true` zurück, wenn `true`, wenn `class` in der Prototypenkette des Objekts vorhanden ist. Er gibt `false` zurück, wenn `object` keine Instanz von `class` ist oder wenn `object` `null` ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung des `instanceof`-Operators gezeigt.  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)