---
title: Slice-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>slice-Methode (Array) (JavaScript)
Gibt einen Abschnitt eines Arrays zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
 `start`  
 Erforderlich. Der Anfang des angegebenen Teils `arrayObj`.  
  
 `end`  
 Dies ist optional. Das Ende des angegebenen Teils `arrayObj`.  
  
## <a name="remarks"></a>Hinweise  
 Die `slice` Methode gibt ein `Array` Objekt, das den angegebenen Teil enthält `arrayObj`.  
  
 Die `slice` -Methode kopiert bis zur, aber nicht einschließlich, das vom angegebenen Element `end`. Wenn `start` ist negativ ist, wird dies als behandelt `length`  +  `start`, wobei `length` ist die Länge des Arrays. Wenn `end` ist negativ ist, wird dies als behandelt `length`  +  `end` , in denen `length` ist die Länge des Arrays. Wenn `end` ausgelassen wird, wird die Extraktion bis zum Ende von `arrayObj` fortgesetzt. Wenn `end` tritt ein, bevor `start`, keine Elemente in das neue Array kopiert werden.  
  
## <a name="example"></a>Beispiel  
 In den folgenden Beispielen wird die Verwendung der `slice`-Methode gezeigt. Im ersten Beispiel, alle bis auf das letzte Element des `myArray` in kopiert `newArray`. Im zweiten Beispiel nur die letzten beiden Elemente vom `myArray` in kopiert `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Slice-Methode (String)](../../javascript/reference/slice-method-string-javascript.md)   
 [String-Objekt](../../javascript/reference/string-object-javascript.md)