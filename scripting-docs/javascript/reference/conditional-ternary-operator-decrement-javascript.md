---
title: "Bedingter (tern&#228;rer) Operator&#160;(?:) (JavaScript) | Microsoft Docs"
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
  - "?:"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "bedingter (ternärer) Operator"
  - "Bedingte Operatoren"
  - "ternär"
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Bedingter (tern&#228;rer) Operator&#160;(?:) (JavaScript)
Gibt in Abhängigkeit von einer Bedingung einen der zwei Ausdrücke zurück.  
  
## Syntax  
  
```  
  
test ? expression1 : expression2  
```  
  
## Parameter  
 `test`  
 Beliebiger boolescher Ausdruck.  
  
 `expression1`  
 Ein zurückgegebener Ausdruck, wenn `test` den Wert `true` hat.  Kann ein Kommaausdruck sein.  
  
 `expression2`  
 Ein zurückgegebener Ausdruck, wenn `test` den Wert `false` hat.  Durch einen Kommaausdruck können mehrere Ausdrücke verknüpft sein.  
  
## Hinweise  
 Der `?:`\-Operator kann als Kurzform für eine `if...else`\-Anweisung verwendet werden.  Er wird in der Regel als Teil eines umfangreicheren Ausdrucks verwendet, der durch eine `if...else`\-Anweisung noch komplexer werden würde.  Beispiel:  
  
```javascript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 Im Beispiel wird die Zeichenfolge "Good evening" erstellt, wenn es später als 18.00 Uhr ist.  Der entsprechende Code mit einer `if...else`\-Anweisung würde wie folgt aussehen:  
  
```javascript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
## Siehe auch  
 [if...else\-Anweisung](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Operatorrangfolge](../../javascript/operator-subtractprecedence-javascript.md)   
 [Zusammenfassung der Operatoren \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Beispiel\-App für ein Konfigurations\-Widget für Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)