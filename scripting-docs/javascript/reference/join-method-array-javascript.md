---
title: Join-Methode (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="join-method-array-javascript"></a>join-Methode (Array) (JavaScript)
Fügt alle Elemente eines Arrays, die durch das angegebene Trennzeichen getrennt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Parameter  
 `arrayObj`  
 Erforderlich. Ein `Array`-Objekt.  
  
 `separator`  
 Dies ist optional. Eine Zeichenfolge, mit der ein Element eines Arrays im resultierenden getrennt `String`. Wenn nicht angegeben, werden die Elemente des Arrays mit einem Komma getrennt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn jedes Element des Arrays ist **undefined** oder `null`, wird dies als eine leere Zeichenfolge behandelt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **Join** Methode.  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [String-Objekt](../../javascript/reference/string-object-javascript.md)