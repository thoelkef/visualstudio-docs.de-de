---
title: "IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionExitByName"
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerCallback2::OnFunctionExitByName
Benachrichtigt das Profilerobjekt, das das Skriptmodul darin, das einen beendet wird, Funktionsaufruf des Dokumentobjektmodells \(Document Object Model\).  
  
## Syntax  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### Parameter  
 `pwszFunctionName`  
 \[in\] beendet wurde der Name der dieser Funktion das Skriptmodul ausgeführt werden.  
  
 `scriptType`  
 \[in\] Der Typ der Funktion.  Beschreibungen von gültigen Werten, finden Sie unter [PROFILER\_SCRIPT\_TYPE\-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.  
  
## Hinweise  
 Für das Skriptmodul DOM\-Aufrufe ruft diese Methode auf, statt, [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md) aufzurufen.  Dies ist aufgrund der großen Anzahl eindeutiger Methoden und Eigenschaften im DOM.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)