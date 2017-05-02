---
title: "ScriptEngineBuildVersion-Funktion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineBuildVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineBuildVersion-Funktion"
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# ScriptEngineBuildVersion-Funktion (JavaScript)
Ruft die Buildversionsnummer des verwendeten Skriptmoduls ab.  
  
## Syntax  
  
```  
ScriptEngineBuildVersion()  
```  
  
## Hinweise  
 Der Rückgabewert entspricht direkt den Versionsinformationen in der Dynamic Link Library \(DLL\) für die verwendete Skriptsprache.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `ScriptEngineBuildVersion`\-Funktion:  
  
```javascript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../includes/jsv5-md.md)]  
  
## Siehe auch  
 [ScriptEngine\-Funktion](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineMajorVersion\-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [ScriptEngineMinorVersion\-Funktion](../../javascript/reference/scriptengineminorversion-function-javascript.md)