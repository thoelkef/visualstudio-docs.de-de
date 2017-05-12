---
title: "Bitweiser Rechtsschiebeoperator&#160;(&gt;&gt;) (JavaScript) | Microsoft Docs"
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
  - ">>"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>-Operator"
  - ">>-Operator, Informationen über den >>-Operator"
  - ">>-Operator, Bitsets"
  - "Bitweise Operatoren, Rechtsschiebeoperator"
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Bitweiser Rechtsschiebeoperator&#160;(&gt;&gt;) (JavaScript)
Verschiebt die Bits eines Ausdrucks unter Beibehaltung der Vorzeichen nach rechts.  
  
## Syntax  
  
```  
  
result = expression1 >> expression2  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Ein beliebiger Ausdruck.  
  
 *expression2*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der Operator \>\> verschiebt die Bits von *expression1* um die Anzahl der Bits, die in *expression2* angegeben sind, nach rechts.  Das Vorzeichenbit von *expression1* wird verwendet, um die Stellen von links aufzufüllen.  Nach rechts verschobene Stellen entfallen.  So hat *temp* nach der Auswertung des folgenden Codes beispielsweise den Wert \-4: \-14 \(11110010 in binären Zweierkomplementen\) ergibt um zwei Bits nach rechts verschoben \-4 \(11111100 in binären Zweierkomplementen\).  
  
```javascript  
var temp  
temp = -14 >> 2  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser Linksschiebeoperator \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Rightshiftzuweisungsoperator \(\>\>\=\)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)