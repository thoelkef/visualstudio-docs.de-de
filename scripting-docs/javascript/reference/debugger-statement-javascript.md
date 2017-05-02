---
title: "debugger-Anweisung (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger-Anweisung"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# debugger-Anweisung (JavaScript)
Unterbricht die Ausführung.  
  
## Syntax  
  
```  
debugger  
```  
  
## Hinweise  
 Sie können `debugger`\-Anweisungen an einer beliebigen Stelle in Prozeduren verwenden, um die Ausführung zu unterbrechen.  Die `debugger`\-Anweisung entspricht dem Festlegen eines Haltepunkts im Code.  
  
 Die `debugger`\-Anweisung unterbricht die Ausführung, sie schließt jedoch keine Dateien und löscht keine Variablen.  
  
> [!NOTE]
>  Die `debugger`\-Anweisung hat keine Auswirkungen, es sei denn, das Skript wird gedebuggt.  
  
## Beispiel  
 In diesem Beispiel wird die `debugger`\-Anweisung verwendet, um die Ausführung bei jeder Iteration der `for`\-Schleife zu unterbrechen.  
  
> [!NOTE]
>  Um dieses Beispiel auszuführen, müssen Sie einen Skriptdebugger installiert haben, und das Skript muss im Debugmodus ausgeführt werden.  
>   
>  Internet Explorer 8 enthält den [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Debugger.  Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801) weitere Informationen.  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
## Siehe auch  
 [JavaScript\-Anweisungen](../../javascript/reference/javascript-statements.md)   
 [Bedingte Kompilierung](../../javascript/advanced/conditional-compilation-javascript.md)