---
title: Split-Methode (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>split-Methode (String) (JavaScript)
Teilt mithilfe des angegebenen Trennzeichens eine Zeichenfolge in untergeordnete Zeichenfolgen und gibt sie als Array zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Parameter  
 `stringObj`  
 Erforderlich. Das aufzuteilende `String`-Objekt oder -Zeichenfolgenliteral. Dieses Objekt nicht geändert wird, indem die **teilen** Methode.  
  
 `separator`  
 Dies ist optional. Eine Zeichenfolge oder eine **reguläre** Objekt, das Zeichen oder Zeichen zur Unterteilung der Zeichenfolge identifiziert. Wenn das Trennzeichen ausgelassen wird, wird ein Array mit einem Element zurückgegeben, das die vollständige Zeichenfolge enthält.  
  
 `limit`  
 Dies ist optional. Ein Wert, der zur Begrenzung der Anzahl von Elementen verwendet wird, die im Array zurückgegeben werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Das Ergebnis der **teilen** Methode ist ein Array von Zeichenfolgen, die an jedem Punkt aufgeteilt, in denen `separator` tritt in `stringObj`. Das `separator`-Argument wird nicht als Bestandteil eines Arrayelements zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **teilen** Methode.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Gilt für**: [String-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Concat-Methode (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp-Objekt](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression-Objekt](../../javascript/reference/regular-expression-object-javascript.md)   
 [Syntax regulärer Ausdrücke (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Beispiel-app für Bildlauf, schwenken und Zoomen](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)