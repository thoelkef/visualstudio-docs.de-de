---
title: "substring-Methode (String) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Teilzeichenfolgen"
  - "substring-Methode"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# substring-Methode (String) (JavaScript)
Gibt eine untergeordnete Zeichenfolge an der angegebenen Position in einem `String`\-Objekt zurück.  
  
## Syntax  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## Parameter  
 `start`  
 Erforderlich.  Die nullbasierte Indexganzzahl, die den Beginn der untergeordneten Zeichenfolge angibt.  
  
 `end`  
 Optional.  Die nullbasierte Indexganzzahl, die das Ende der untergeordneten Zeichenfolge angibt.  Die untergeordnete Zeichenfolge enthält die Zeichen bis zum, aber nicht einschließlich des von `end` angegebenen Zeichens.  
  
 Wenn `end` weggelassen wird, werden die Zeichen von `start` bis zum Ende der ursprünglichen Zeichenfolge zurückgegeben.  
  
## Hinweise  
 Die `substring`\-Methode gibt eine Zeichenfolge zurück, die die untergeordnete Zeichenfolge von `start` bis, aber nicht einschließlich, `end` enthält.  
  
 Die **substring**\-Methode verwendet den niedrigeren Wert von `start` und `end` als Ausgangspunkt für die untergeordnete Zeichenfolge.  Beispielsweise wird durch strvar.substring\(0, 3**\)** und strvar.substring\(3, 0\) dieselbe Teilzeichenfolge zurückgegeben.  
  
 Wenn entweder `start` oder `end` den Wert `NaN` oder einen negativen Wert hat, wird der entsprechende Wert durch Null \(0\) ersetzt.  
  
 Die Länge der untergeordneten Zeichenfolge entspricht dem absoluten Wert der Differenz zwischen `start` und `end`.  Die untergeordnete Zeichenfolge, die z. B. in strvar.substring\(0, 3\) und strvar.substring\(3, 0\) zurückgegeben wird, hat eine Länge von drei Zeichen.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **substring**\-Methode.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [substr\-Methode \(String\)](../../javascript/reference/substr-method-string-javascript.md)