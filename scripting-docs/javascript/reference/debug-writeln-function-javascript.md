---
title: "Debug.writeln-Funktion (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn-Methode"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Debug.writeln-Funktion (JavaScript)
Sendet Zeichenfolgen an den Skriptdebugger und fügt ein Zeilenumbruchzeichen hinzu.  
  
## Syntax  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Parameter  
 *str1, str2,... , strN*  
 Optional.  An den Skriptdebugger zu sendende Zeichenfolgen.  
  
## Hinweise  
 Die `Debug.writeln`\-Funktion sendet Zeichenfolgen gefolgt von einem Zeilenumbruchzeichen zur Laufzeit zum Direktfenster des Microsoft Skriptdebuggers.  Wenn das Skript nicht gedebuggt wird, hat die `Debug.writeln`\-Funktion keine Auswirkungen.  
  
 Die `Debug.writeln`\-Funktion ist nahezu identisch mit der `Debug.write`\-Funktion.  Der einzige Unterschied besteht darin, dass die `Debug.write`\-Funktion nach dem Senden der Zeichenfolgen kein Zeilenumbruchzeichen sendet.  
  
## Beispiel  
 In diesem Beispiel wird die `Debug.writeln`\-Funktion verwendet, um den Wert der Variablen im Direktfenster des Microsoft\-Skriptdebuggers anzuzeigen.  
  
> [!NOTE]
>  Um dieses Beispiel auszuführen, müssen Sie einen Skriptdebugger installiert haben, und das Skript muss im Debugmodus ausgeführt werden.  
>   
>  Internet Explorer 8 enthält den [!INCLUDE[javascript](../../includes/javascript-md.md)]\-Debugger.  Wenn Sie eine frühere Version von Internet Explorer verwenden, finden Sie unter [Gewusst wie: Aktivieren und Starten des Skriptdebuggings in Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801) weitere Informationen.  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## Anforderungen  
 [!INCLUDE[jsv3](../../includes/jsv3-md.md)]  
  
 **Gilt für**: [Debugobjekt](../../javascript/reference/debug-object-javascript.md)  
  
## Siehe auch  
 [Debug.write\-Funktion](../../javascript/reference/debug-write-function-javascript.md)