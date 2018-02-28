---
title: Push-Methode (Array) (JavaScript) | Microsoft Docs
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
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="push-method-array-javascript"></a>push-Methode (Array) (JavaScript)
Fügt neue Elemente an ein Array an und gibt die neue Länge des Arrays zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
 `item, item2,. . ., itemN`  
 Dies ist optional. Neue Elemente, die von der `Array`.  
  
## <a name="remarks"></a>Hinweise  
 Die `push` und `pop` Methoden ermöglichen es Ihnen, eine letzte in, out Stapel zuerst zu simulieren.  
  
 Die `push` Methode fügt Elemente in der Reihenfolge, in der sie angezeigt werden. Wenn eines der Argumente ein Array ist, wird es als ein einzelnes Element hinzugefügt. Verwenden der `concat` Methode, um die Elemente von zwei oder mehr Arrays zu verknüpfen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `push`-Methode veranschaulicht.  
  
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
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Concat-Methode (Array)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop-Methode (Array)](../../javascript/reference/pop-method-array-javascript.md)