---
title: "substr-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr-Methode"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# substr-Methode (String) (JavaScript)
Ruft eine Teilzeichenfolge ab, die an der angegebenen Position beginnt und über die angegebene Länge verfügt.  
  
## Syntax  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## Parameter  
 `stringvar`  
 Erforderlich.  Ein Zeichenfolgenliteral oder ein `String`\-Objekt, aus dem die untergeordnete Zeichenfolge extrahiert wird.  
  
 `start`  
 Erforderlich.  Die Anfangsposition der gewünschten untergeordneten Zeichenfolge.  Der Index des ersten Zeichens der Zeichenfolge ist Null.  
  
 `length`  
 Optional.  Die Anzahl der Zeichen, die die zurückgegebene untergeordnete Zeichenfolge enthalten soll.  
  
## Hinweise  
 Falls `length` Null oder negativ ist, wird eine leere Zeichenfolge zurückgegeben.  Ohne diese Angabe wird die untergeordnete Zeichenfolge bis zum Ende von `stringvar` fortgesetzt.  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der `substr`\-Methode veranschaulicht.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [String\-Objekt](../../javascript/reference/string-object-javascript.md)  
  
## Siehe auch  
 [substring\-Methode \(String\)](../../javascript/reference/substring-method-string-javascript.md)