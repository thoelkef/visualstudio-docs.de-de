---
title: "Rightshiftzuweisungsoperator (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
  - ">>="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - ">>=-Operator [JavaScript]"
  - "Zuweisungsoperatoren, JavaScript"
  - "right shift-Operatoren [JavaScript]"
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Rightshiftzuweisungsoperator (&gt;&gt;=) (JavaScript)
Verschiebt den Wert einer Variablen um die Anzahl der Bits, die im Wert eines Ausdrucks angegeben sind, unter Beibehaltung des Vorzeichens nach rechts und weist das Ergebnis der Variablen zu.  
  
## Syntax  
  
```  
  
result >>= expression  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Die Verwendung des Operators **\>\>\=** entspricht genau der folgenden Angabe:  
  
```javascript  
result = result >> expression  
```  
  
 Der Operator **\>\>\=**verschiebt die Bits von *result* gemäß der in *expression* angegebenen Zahl nach rechts.  Das Vorzeichenbit von *result* wird verwendet, um die Bits von links aufzufüllen.  Nach rechts verschobene Stellen entfallen.  So hat *temp* nach der Auswertung des folgenden Codes beispielsweise den Wert \-4: 14 \(binär 11110010\), der um zwei Bits nach rechts verschoben \-4 \(binär 11111100\) ergibt.  
  
```javascript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [Bitweiser Linksschiebeoperator \(\<\<\)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Bitweiser Rechtsschiebeoperator \(\>\>\)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Vorzeichenloser Rechtsschiebeoperator \(\>\>\>\)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)