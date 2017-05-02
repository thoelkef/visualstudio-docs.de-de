---
title: "Anweisung mit Bezeichnung (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue-Anweisung"
  - "Bezeichner, Anweisungen"
  - "Anweisung mit Bezeichnung"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Anweisung mit Bezeichnung (JavaScript)
Stellt einen Bezeichner für eine Anweisung bereit.  
  
## Syntax  
  
```  
  
      label :  
   statements   
```  
  
## Parameter  
 *label*  
 Erforderlich.  Ein eindeutiger Bezeichner, der für Verweise auf die Anweisung mit Bezeichnung verwendet wird.  
  
 `statements`  
 Optional.  Eine oder mehrere mit *label* verknüpfte Anweisungen.  
  
## Hinweise  
 Bezeichnungen werden von den **break**\- und **continue**\-Anweisungen verwendet, um die Anweisung anzugeben, für die **break** und **continue** gilt.  
  
## Beispiel  
 Im folgenden Code verweist die **continue**\-Anweisung auf die **for**\-Schleife, der die `Inner:`\-Anweisung vorangestellt ist.  Wenn `j` gleich 24 ist, führt die **continue**\-Anweisung dazu, dass die **for**\-Schleife zur nächsten Iteration wechselt.  Die Zahlen 21 bis 23 und 25 bis 30 werden auf jeder Zeile ausgegeben.  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [break\-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [continue\-Anweisung](../../javascript/reference/continue-statement-javascript.md)