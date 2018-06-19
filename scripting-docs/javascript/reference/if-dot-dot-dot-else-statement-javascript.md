---
title: If... else-Anweisung (JavaScript) | Microsoft Docs
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
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637330"
---
# <a name="ifelse-statement-javascript"></a>if...else-Anweisung (JavaScript)
Führt bedingt eine Gruppe von Anweisungen aus, abhängig vom Wert eines Ausdrucks.  
  
## <a name="syntax"></a>Syntax  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Parameter  
 `condition1`  
 Erforderlich. Ein boolescher Ausdruck. Wenn `condition1` ist `null` oder `undefined`, `condition1` so behandelt, als `false`.  
  
 `statement1`  
 Dies ist optional. Die auszuführende Anweisung Wenn `condition1` ist **"true"**. Kann eine Verbundanweisung sein.  
  
 `condition2`  
 Die auszuwertende Bedingung.  
  
 `statement2`  
 Dies ist optional. Die auszuführende Anweisung Wenn `condition2` ist `true`. Kann eine Verbundanweisung sein.  
  
 `statement3`  
 Wenn beide `condition1` und `condition2` sind `false`, diese Anweisung ausgeführt wird.  
  
## <a name="example"></a>Beispiel  
 Der folgende Code zeigt, wie Sie `if`, `if else`, und `else`.  
  
 Es wird empfohlen, zum Einschließen von `statement1` und `statement2` in der geschweiften Klammern ({}) aus Gründen der Übersichtlichkeit und unbeabsichtigte Fehler zu vermeiden.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Bedingter (ternärer) Operator (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)