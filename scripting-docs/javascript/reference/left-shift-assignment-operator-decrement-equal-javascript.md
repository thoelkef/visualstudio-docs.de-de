---
title: "Left Shift-Zuweisungsoperator (&lt;&lt;=) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "<<="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<=-Operator [JavaScript]"
  - "Left Shift-Zuweisungsoperator (<<=) (JavaScript)"
  - "left shift-Operatoren [JavaScript]"
  - "Zuweisungsoperatoren, JavaScript"
ms.assetid: 9f30ff46-48cc-4931-b260-edef31ff0076
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Left Shift-Zuweisungsoperator (&lt;&lt;=) (JavaScript)
Verschiebt die angegebene Anzahl von Bits nach links und weist `result` das Ergebnis zu.  Die Bits, die durch den Vorgang freiwerden, werden mit 0 gefüllt.  
  
## Syntax  
  
```  
  
result <<= expression  
```  
  
## Parameter  
 `result`  
 Beliebige Variable.  
  
 `expression`  
 Die Anzahl von Bits, die verschoben werden sollen.  
  
## Hinweise  
 Die Verwendung des `<<=`\-Operators entspricht der Angabe von `result = result << expression`  
  
 Im folgenden Beispiel wird die Verwendung des `<<=`\-Operators gezeigt.  
  
```javascript  
// 14 is 00000000000000000000000000001110  
var temp = 14;  
temp <<= 2;   
document.write(temp);  
// 56 is 00000000000000000000000000111000  
Output: 56  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser Linksschiebeoperator \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)