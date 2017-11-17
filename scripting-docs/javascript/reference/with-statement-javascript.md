---
title: with-Anweisung (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: with_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: With statement
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35d49b13261c66cde0ecd53517a99361f6aecb79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="with-statement-javascript"></a>with-Anweisung (JavaScript)
Legt das Standardobjekt für eine Anweisung fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
with (object) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parameter  
 `object`  
 Das Standardobjekt.  
  
 `statements`  
 Eine oder mehrere Anweisungen, für die `object` das Standardobjekt ist.  
  
## <a name="remarks"></a>Hinweise  
 Die `with`-Anweisung wird vielfach zur Verkürzung von Programmcode verwendet.  
  
> [!WARNING]
>  Die Verwendung von `with` ist im Strict-Modus nicht zugelassen. Durch die Verwendung von `with` kann Code schwieriger lesbar und zu debuggen sein und sollte im Allgemeinen vermieden werden.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das `Math`-Objekt wiederholt verwendet.  
  
```JavaScript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## <a name="example"></a>Beispiel  
 Wenn Sie das Beispiel ändern, um die `with`-Anweisung zu verwenden, wird der Code kürzer:  
  
```JavaScript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [this-Anweisung](../../javascript/reference/this-statement-javascript.md)