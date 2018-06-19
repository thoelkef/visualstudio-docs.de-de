---
title: foreach-Methode (Set) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636760"
---
# <a name="foreach-method-set-javascript"></a>forEach-Methode (Set) (JavaScript)
Führt die angegebene Aktion für jedes Element in einem Satz aus.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parameter  
 `setObj`  
 Erforderlich. Ein `Set`-Objekt.  
  
 `callbackfn`  
 Erforderlich. `callbackfn`bis zu drei Argumente akzeptiert. Die Funktion, die `forEach` einmal für jedes Element im Satz aufruft.  
  
 `thisArg`  
 Dies ist optional. Ein Objekt, auf das das `this`-Schlüsselwort in der `callbackfn`-Funktion verweisen kann. Wird `thisArg` nicht angegeben, wird `undefined` als `this`-Wert verwendet.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn es sich beim `callbackfn`-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`-Ausnahme ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, key, setObj)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis zu drei Parameter verwenden, wie in der folgenden Tabelle dargestellt.  
  
|Rückrufargument|Definition|  
|-----------------------|----------------|  
|`value`|Ein im Satz enthaltener Wert.|  
|`key`|Ein im Satz enthaltener Wert. Ein Satz hat keine Schlüssel, dieser Wert ist also der gleiche wie `value`.|  
|`setObj`|Das zu durchlaufende `Set`-Objekt.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung von `forEach`. Das `callbackfn`-Argument enthält den Code für die Rückruffunktion.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, dass Sie Member aus einem Satz auch abrufen können, indem Sie der Rückruffunktion nur einen Parameter übergeben.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]