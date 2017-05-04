---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
Benachrichtigt das Profilerobjekt, dass das Skriptmodul ein Skript kompilierte.  Diese Methode wird für jedes Skript aufgerufen, das kompiliert wird.  
  
## Syntax  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Parameter  
 `scriptId`  
 \[in\] Die eindeutige ID des Skripts, das kompiliert wurde.  Diese ID wird durch das Skriptmodul zugewiesen.  
  
 `type`  
 \[in\] Der Typ des Skripts, das kompiliert wurde.  Die Werte werden in [PROFILER\_SCRIPT\_TYPE\-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md) definiert.  
  
 `pIDebugDocumentContext`  
 \[in\] Verfügbar, wenn ein Zeiger auf eine `IUnknown`\-Schnittstelle, die der Profiler für einen [IDebugDocumentContext\-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md) Zeiger durchgeführt werden muss.  Andernfalls ist dies NULL.  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.  
  
## Hinweise  
 Das Skriptmodul kann den Dokumentenkontext bereitstellen, wenn dies vom Host unterstützt wird.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)