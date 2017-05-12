---
title: "var-Anweisung (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Deklarieren von Variablen, Var-Anweisung"
  - "var-Anweisung"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# var-Anweisung (JavaScript)
Deklariert eine Variable.  
  
## Syntax  
  
```  
var variable1 = value1  
```  
  
## Parameter  
 `variable1`  
 Der Name der Variablen, die deklariert wird.  
  
 `value1`  
 Die Startwerte, die den Variablen zugewiesen sind.  
  
## Hinweise  
 Verwenden Sie die `var`\-Anweisung zum Deklarieren von Variablen.  Den Variablen können in der Deklaration oder später im Skript Werte zugewiesen werden.  
  
 Eine Variable wird deklariert, wenn sie zum ersten Mal im Skript angezeigt wird.  
  
 Sie können eine Variable deklarieren, ohne das `var`\-Schlüsselwort in der Deklaration zu verwenden und ihr einen Wert zuzuweisen.  Dies wird als *implizite Deklaration* bezeichnet und ist nicht empfehlenswert.  Eine implizite Deklaration resultiert im globalen Gültigkeitsbereich der Variablen.  Wenn eine Variable auf Prozedurebene deklariert wird, soll diese jedoch meist keinen globalen Gültigkeitsbereich haben.  Um zu verhindern, dass die Variable einen globalen Gültigkeitsbereich erhält, müssen Sie das `var`\-Schlüsselwort in der Variablendeklaration verwenden.  
  
 Wenn Sie die Variable in der `var`\-Anweisung nicht initialisieren, wird ihr automatisch der [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]\-Wert `undefined` zugewiesen.  
  
## Beispiel  
 Die folgenden Beispiele veranschaulichen die Verwendung der `var`\-Anweisung.  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Siehe auch  
 [function\-Anweisung](../../javascript/reference/function-statement-javascript.md)   
 [new\-Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array\-Objekt](../../javascript/reference/array-object-javascript.md)   
 [Variablen](../../javascript/variables-javascript.md)