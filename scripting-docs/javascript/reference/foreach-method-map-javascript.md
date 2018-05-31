---
title: foreach-Methode (Map) (JavaScript) | Microsoft Docs
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7d625fb4dfe88b2db69e6aa0ff66c7e90f66
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335800"
---
# <a name="foreach-method-map-javascript"></a>forEach-Methode (Map) (JavaScript)
Führt die angegebene Aktion für jedes Element in einer Zuordnung aus.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parameter  
 `mapObj`  
 Erforderlich. Ein `Map`-Objekt.  
  
 `callbackfn`  
 Erforderlich. Die Funktion, die `forEach` einmal für jedes Element in der Zuordnung aufruft. `callbackfn` bis zu drei Argumente akzeptiert. `forEach` ruft die `callbackfn`-Funktion für jedes Element in der Zuordnung einmal auf.  
  
 `thisArg`  
 Dies ist optional. Ein Objekt, auf das das `this`-Schlüsselwort in der `callbackfn`-Funktion verweisen kann. Wird `thisArg` nicht angegeben, wird `undefined` als `this`-Wert verwendet.  
  
## <a name="exceptions"></a>Ausnahmen  
 Wenn es sich beim `callbackfn`-Argument nicht um ein Funktionsobjekt handelt, wird eine `TypeError`-Ausnahme ausgelöst.  
  
## <a name="remarks"></a>Hinweise  
 Die Syntax der Rückruffunktion lautet wie folgt:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Sie können die Rückruffunktion deklarieren, indem Sie bis zu drei Parameter verwenden, wie in der folgenden Tabelle dargestellt.  
  
|Rückrufargument|Definition|  
|-----------------------|----------------|  
|`value`|Ein Wert in der Zuordnung.|  
|`key`|Ein Schlüssel in der Zuordnung.|  
|`mapObj`|Das zu durchlaufende `Map`-Objekt.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie ein Member einer `Map` mithilfe von `forEach` abrufen.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]
