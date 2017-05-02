---
title: "Debug.write-Funktion (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write-Methode [JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Debug.write-Funktion (JavaScript)
Sendet Zeichenfolgen an den Skriptdebugger.  
  
## Syntax  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Parameter  
 *str1, str2,... , strN*  
 Optional.  An den Skriptdebugger zu sendende Zeichenfolgen.  
  
## Hinweise  
 Die `Debug.write`\-Funktion sendet zur Laufzeit Zeichenfolgen zum Direktfenster eines Skriptdebuggers.  Wenn das Skript nicht debuggt wird, hat die `Debug.write`\-Funktion keine Auswirkungen.  
  
 Die `Debug.write`\-Funktion ist mit der `Debug.writeln`\-Funktion fast identisch.  Der einzige Unterschied ist, dass die `Debug.writeln`\-Funktion nach dem Übermitteln der Zeichenfolgen ein Zeilenumbruchzeichen sendet.  
  
## Beispiel  
 Im Beispiel ist zu sehen, wie mit der `Debug.write`\-Funktion der Wert der Variablen im Direktfenster des Skriptdebuggers gezeigt wird.  
  
> [!NOTE]
>  Um dieses Beispiel auszuführen, müssen Sie einen Skriptdebugger installiert haben, und das Skript muss im Debugmodus ausgeführt werden.  
>   
>  Internet Explorer 8 enthält den [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Debugger.  Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801) weitere Informationen.  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Debugobjekt](../../javascript/reference/debug-object-javascript.md)  
  
## Siehe auch  
 [Debug.writeln\-Funktion](../../javascript/reference/debug-writeln-function-javascript.md)