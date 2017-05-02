---
title: "ScriptEngineMinorVersion-Funktion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion-Funktion"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMinorVersion-Funktion (JavaScript)
Ruft die Nebenversionsnummer des verwendeten Skriptmoduls ab.  
  
## Syntax  
  
```  
ScriptEngineMinorVersion()  
```  
  
## Hinweise  
 Der Rückgabewert entspricht direkt den Versionsinformationen in der Dynamic Link Library \(DLL\) für die verwendete Skriptsprache.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `ScriptEngineMinorVersion`\-Funktion.  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Siehe auch  
 [ScriptEngine\-Funktion](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion\-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMajorVersion\-Funktion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)