---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
Benachrichtigt das Profilerobjekt, das das Skriptmodul darin, das einen Funktionsaufruf ausgeführt wird, beendet wird, der kein Aufruf des DOM\- \(Document Object Model\) ist.  
  
## Syntax  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### Parameter  
 `scriptId`  
 \[in\] Die eindeutige ID des Skripts, dass die Funktion gehört.  Diese ID wird durch das Skriptmodul zugewiesen.  
  
 `functionId`  
 \[in\] Die eindeutige ID der Funktion.  Diese ID wird durch das Skriptmodul zugewiesen.  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.  
  
## Hinweise  
 Für DOM\-Aufrufe ruft das Skriptmodul [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) anstelle `IActiveScriptProfilerCallback::OnFunctionExit` an.  Dies ist aufgrund der großen Anzahl eindeutiger Methoden und Eigenschaften im DOM.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)