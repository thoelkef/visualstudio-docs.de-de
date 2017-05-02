---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
Benachrichtigt das Profilerobjekt, dass das Skriptmodul eine Funktion antraf, als, ein Skript kompilieren.  
  
## Syntax  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Parameter  
 `functionId`  
 \[in\] Die eindeutige ID der Funktion.  Diese ID wird durch das Skriptmodul zugewiesen.  
  
 `scriptId`  
 \[in\] Die eindeutige ID des Skripts, dass die Funktion gehört.  
  
 `pwszFunctionName`  
 \[in\] Der Name der Funktion oder NULL für eine anonyme Funktion.  
  
 `pwszFunctionNameHint`  
 \[in\] Der abgeleitete Name der Funktion oder NULL, wenn das Skriptmodul keinen Namen ableitet.  
  
 `pIDebugDocumentContext`  
 \[in\] Verfügbar, wenn der Zeiger auf eine `IUnknown`\-Schnittstelle, die der Profiler für einen [IDebugDocumentContext\-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger durchgeführt werden muss.  Andernfalls NULL.  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.  
  
## Hinweise  
 Das Skriptmodul kann den Dokumentenkontext bereitstellen, wenn dies vom Host unterstützt wird.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)