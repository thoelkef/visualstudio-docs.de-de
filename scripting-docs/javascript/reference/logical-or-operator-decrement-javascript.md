---
title: "Logischer OR-Operator (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "||-Operator"
  - "Logischer OR-Operator"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Logischer OR-Operator (||) (JavaScript)
Führt eine logische Disjunktion zweier Ausdrücke durch.  
  
## Syntax  
  
```  
  
result = expression1 || expression2  
```  
  
## Parameter  
 *Ergebnis*  
 Beliebige Variable.  
  
 *expression1*  
 Ein beliebiger Ausdruck.  
  
 *expression2*  
 Ein beliebiger Ausdruck.  
  
## Hinweise  
 Der Wert für *result* ist **True**, wenn einer der Ausdrücke oder beide Ausdrücke **True** sind.  Die folgende Tabelle veranschaulicht, wie *result* berechnet wird:  
  
|Wenn `expression1` folgenden Wert hat|Und `expression2` gleich|Das Ergebnis `result` ist|  
|-------------------------------------------|------------------------------|-------------------------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../includes/javascript-md.md)] verwendet bei der Konvertierung nicht boolescher Werte in boolesche Werte die folgenden Regeln:  
  
-   Alle Objekte werden als "true" interpretiert.  
  
-   Zeichenfolgen gelten nur dann als false, wenn sie leer sind.  
  
-   `null` und "undefined" gelten als "false".  
  
-   Zahlen gelten nur dann als false, wenn sie 0 sind.  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)