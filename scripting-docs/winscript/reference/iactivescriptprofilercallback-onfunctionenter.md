---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
Benachrichtigt das Profilerobjekt, dass das Skriptmodul im Begriff ist, einen Funktionsaufruf auszuführen, der kein Aufruf des DOM\- \(Document Object Model\) ist.  
  
## Syntax  
  
```  
HRESULT OnFunctionEnter(  
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
 Für DOM\-Aufrufe ruft das Skriptmodul [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) anstelle `IActiveScriptProfilerCallback::OnFunctionEnter` an.  Dies ist aufgrund der großen Anzahl eindeutiger Methoden und Eigenschaften im DOM.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)