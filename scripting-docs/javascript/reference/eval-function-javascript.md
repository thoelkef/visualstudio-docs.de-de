---
title: "eval-Funktion (JavaScript) | Microsoft Docs"
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
  - "eval"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "eval-Funktion"
  - "analysieren, Code"
  - "Parser"
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# eval-Funktion (JavaScript)
Wertet [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Code aus und führt diesen aus.  
  
## Syntax  
  
```  
eval(codeString)   
```  
  
## Parameter  
 `codeString`  
 Erforderlich.  Ein `String`\-Wert, der gültigen [!INCLUDE[javascript](../../includes/javascript-md.md)] Code enthält.  
  
## Hinweise  
 Die `eval`\-Funktion ermöglicht die dynamische Ausführung von [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Quellcode.  
  
 Die `codeString` Zeichenfolge wird vom [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Parser analysiert und ausgeführt.  
  
 Der an die `eval`\-Funktion übergebene Code wird im selben Kontext wie der Aufruf der `eval`\-Funktion ausgeführt.  
  
 Wenn möglich, verwenden Sie die [JSON.parse\-Funktion](../../javascript/reference/json-parse-function-javascript.md) zum Deserialisieren von JSON\-Text \(Text in JavaScript\-Objektnotation\).  Die `JSON.parse`\-Funktion ist sicherer und wird schneller ausgeführt als die `eval`\-Funktion.  
  
## Beispiel  
 Im folgenden Code wird die Variable `myDate` mit einem Testdatum initialisiert.  
  
```javascript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## Anforderungen  
 [!INCLUDE[jsv1](../../includes/jsv1-md.md)]  
  
 **Gilt für**: [Global\-Objekt](../../javascript/reference/global-object-javascript.md)  
  
## Siehe auch  
 [String\-Objekt](../../javascript/reference/string-object-javascript.md)