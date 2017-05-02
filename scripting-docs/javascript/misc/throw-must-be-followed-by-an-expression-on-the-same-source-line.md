---
title: "Auf &#39;throw&#39; muss ein Ausdruck in derselben Quellzeile folgen | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Auf &#39;throw&#39; muss ein Ausdruck in derselben Quellzeile folgen
Sie haben das `throw`\-Schlüsselwort verwendet, ohne in derselben Codezeile einen Ausdruck anzugeben.  Eine `throw`\-Anweisung besteht aus zwei Teilen: dem `throw`\-Schlüsselwort, dem der auszulösende Ausdruck folgt.  Beispiel:  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Sie können diese beiden Komponenten nicht aufteilen.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass sich das `throw`\-Schlüsselwort und der Ausdruck in der gleichen Zeile befinden.  
  
## Siehe auch  
 [Error\-Objekt](../../javascript/reference/error-object-javascript.md)   
 [throw\-Anweisung](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally\-Anweisung](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)