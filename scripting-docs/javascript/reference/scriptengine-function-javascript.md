---
title: "ScriptEngine-Funktion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngine"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngine-Funktion"
ms.assetid: 65674b2b-d2c2-4493-99b3-f0d20fda8249
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# ScriptEngine-Funktion (JavaScript)
Ruft den Namen der verwendeten Skriptsprache ab.  
  
## Syntax  
  
```  
ScriptEngine()  
```  
  
## Hinweise  
 Die Funktion `ScriptEngine` gibt „JScript“ zurück, womit [!INCLUDE[javascript](../../includes/javascript-md.md)] als das aktuelle Skriptmodul angegeben wird.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `ScriptEngine`\-Funktion:  
  
```javascript  
if (window.ScriptEngine) {  
    console.log(window.ScriptEngine());  
}  
  
// Output: JScript  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../includes/jsv5-md.md)]  
  
## Siehe auch  
 [ScriptEngineBuildVersion\-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion\-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion\-Funktion](../../javascript/reference/scriptengineminorversion-function-javascript.md)