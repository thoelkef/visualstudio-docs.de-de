---
title: While-Anweisung (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641250"
---
# <a name="while-statement-javascript"></a>while-Anweisung (JavaScript)
Führt eine Anweisung oder eine Reihe von Anweisungen aus, bis eine angegebene Bedingung ist `false`.  
  
## <a name="syntax"></a>Syntax  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parameter  
 `expression`  
 Erforderlich. Ein boolescher Ausdruck, der vor jeder Iteration der Schleife überprüft wird. Wenn `expression` ist `true`, die Schleife ausgeführt wird. Wenn `expression` ist `false`, wird die Schleife beendet.  
  
 `statements`  
 Dies ist optional. Eine oder mehrere Anweisungen ausgeführt werden, wenn `expression` ist `true`.  
  
## <a name="remarks"></a>Hinweise  
 Die `while` -Anweisung Schecks `expression` vor der ersten Ausführung eine Schleife. Wenn `expression` ist `false` zu diesem Zeitpunkt wird die Schleife nie durchlaufen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `while`-Anweisung.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [continue-Anweisung](../../javascript/reference/continue-statement-javascript.md)   
 [Do...While-Anweisung](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [für die Anweisung](../../javascript/reference/for-statement-javascript.md)   
 [for...in-Anweisung](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)