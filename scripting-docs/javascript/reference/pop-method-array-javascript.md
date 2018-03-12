---
title: POP-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="pop-method-array-javascript"></a>pop-Methode (Array) (JavaScript)
Entfernt das letzte Element aus einem Array und gibt dieses zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>Hinweise  
 Die [Push](../../javascript/reference/push-method-array-javascript.md) und `pop` Methoden ermöglichen es Ihnen, einen Stapel zu simulieren, die das Prinzip Last in, first out (LIFO) zum Speichern von Daten verwendet.  
  
 Die erforderliche `arrayObj` Verweis ist ein `Array` Objekt.  
  
 Wenn das Array leer ist, ist `undefined` wird zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `pop`-Methode veranschaulicht.  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [push-Methode (Array)](../../javascript/reference/push-method-array-javascript.md)