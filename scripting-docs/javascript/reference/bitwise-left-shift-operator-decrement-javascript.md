---
title: "Bitweiser Linksschiebeoperator&#160;(&lt;&lt;) (JavaScript) | Microsoft Docs"
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
  - "<<"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "<<-Operator"
  - "<<-Operator, Informationen über den <<-Operator"
  - "Bitweise Operatoren, Linksschiebeoperator"
  - "left shift-Operatoren"
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Bitweiser Linksschiebeoperator&#160;(&lt;&lt;) (JavaScript)
Verschiebt die Bits eines Ausdrucks nach links.  
  
## Syntax  
  
```  
  
result = expression1 << expression2  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Ein beliebiger Ausdruck.  
  
 *expression2*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der Operator **\<\<** verschiebt die Bits von *expression1* um die Anzahl der Bits, die in *expression2* angegeben sind, nach links.  Beispiel:  
  
```javascript  
var temp  
temp = 14 << 2  
```  
  
 Die *temp*\-Variable hat einen Wert von 56, da 14 \(binär 00001110\), um zwei Bits nach links verschoben, 56 ergibt \(binär 00111000\).  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Left Shift\-Zuweisungsoperator \(\<\<\=\)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bitweiser Rechtsschiebeoperator \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)