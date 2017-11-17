---
title: Array.of-Funktion (Array) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="arrayof-function-array-javascript"></a>Array.of-Funktion (Array) (JavaScript)
Gibt ein Array aus den übergebenen Argumenten zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>Parameter  
 `element0,...,elementN`  
 Dies ist optional. Die im Array zu platzierenden Elemente. Es wird ein Array mit n + 1 Elementen und einer Länge von n + 1 erstellt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ist vergleichbar mit einem Aufruf von `new Array(args)`, jedoch weist `Array.of` kein besonderes Verhalten auf, wenn ein Argument übergeben wird.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Array aus übergebenen Zahlen erstellt.  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt den Unterschied zwischen der Verwendung von `Array.of` und `new Array`.  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]