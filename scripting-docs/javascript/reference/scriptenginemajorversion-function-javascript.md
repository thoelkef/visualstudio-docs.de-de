---
title: "ScriptEngineMajorVersion-Funktion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMajorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMajorVersion-Funktion"
ms.assetid: 3e251bce-1e14-4cb5-b79f-53845d1920fd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ScriptEngineMajorVersion-Funktion (JavaScript)
Ruft die Hauptversionsnummer des verwendeten Skriptmoduls ab.  
  
## Syntax  
  
```  
ScriptEngineMajorVersion()  
```  
  
## Hinweise  
 Der Rückgabewert entspricht direkt den Versionsinformationen in der Dynamic Link Library \(DLL\) für die verwendete Skriptsprache.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `ScriptEngineMajorVersion`\-Funktion:  
  
```javascript  
if (window.ScriptEngineMajorVersion) {  
    console.log(window.ScriptEngine());   
}  
  
Output: <current major version>  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Siehe auch  
 [ScriptEngine\-Funktion](../../javascript/reference/scriptengine-function-javascript.md)   
 [ScriptEngineBuildVersion\-Funktion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [ScriptEngineMinorVersion\-Funktion](../../javascript/reference/scriptengineminorversion-function-javascript.md)