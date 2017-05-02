---
title: "Vorzeichenloser Rightshiftzuweisungsoperator&#160;(&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>=-Operator"
  - "Zuweisungsoperatoren, JavaScript"
  - "Vorzeichenloser Rightshiftzuweisungsoperator (>>>=)"
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Vorzeichenloser Rightshiftzuweisungsoperator&#160;(&gt;&gt;&gt;=) (JavaScript)
Verschiebt den Wert einer Variablen um die Anzahl der Bits, die im Wert eines Ausdrucks angegeben sind, nach rechts, ohne das Vorzeichen beizubehalten, und weist das Ergebnis der Variablen zu.  
  
## Syntax  
  
```  
  
result >>>= expression  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Verwendung des Operators \>\>\>\= entspricht genau folgendem Ablauf:  
  
```javascript  
result = result >>> expression  
```  
  
 Der Operator **\>\>\>\=**verschiebt die Bit von *result* gemäß der in *expression* angegebenen Nummer nach rechts.  Von links wird mit Nullen aufgefüllt.  Nach rechts verschobene Stellen entfallen.  Beispiel:  
  
```javascript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 Die Variable *temp* besitzt den Anfangswert – 14 \(11111111 11111111 11111111 11110010 in binären Zweierkomplementen\).  Beim Verschieben um zwei Bit nach rechts entspricht der Wert 1073741820 \(00111111 11111111 11111111 11111100 in Binärdatei\).  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Vorzeichenloser Rechtsschiebeoperator \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Bitweiser Linksschiebeoperator \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)