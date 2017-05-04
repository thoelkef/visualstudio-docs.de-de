---
title: "Vorzeichenloser Rechtsschiebeoperator&#160;(&gt;&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>>-Operator"
  - "Vorzeichenloser Rechtsschiebeoperator (>>>)"
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Vorzeichenloser Rechtsschiebeoperator&#160;(&gt;&gt;&gt;) (JavaScript)
Verschiebt die Bits eines Ausdrucks ohne Beibehaltung des Vorzeichens nach rechts.  
  
## Syntax  
  
```  
  
result = expression1 >>> expression2  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Ein beliebiger Ausdruck.  
  
 *expression2*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der Operator **\>\>\>** verschiebt die Bits von *expression1* um die Anzahl der Bits, die in *expression2* angegeben sind, nach rechts.  Von links wird mit Nullen aufgefüllt.  Nach rechts verschobene Stellen entfallen.  Beispiel:  
  
```javascript  
var temp  
temp = -14 >>> 2  
```  
  
 Die Variable *temp* besitzt den Anfangswert \-14 \(11111111 11111111 11111111 11110010 in binären Zweierkomplementen\).  Bei Verschiebung um zwei Bits nach rechts entspricht der Wert 1073741820 \(00111111 11111111 11111111 11111100 in binärer Schreibweise\).  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Vorzeichenloser Rightshiftzuweisungsoperator \(\>\>\>\=\)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bitweiser Linksschiebeoperator \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)