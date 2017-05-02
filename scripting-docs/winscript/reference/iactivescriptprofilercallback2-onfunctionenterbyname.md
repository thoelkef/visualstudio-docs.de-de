---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
Benachrichtigt das Profilerobjekt, dass das Skriptmodul einen Funktionsaufruf des Dokumentobjektmodells \(Document Object Model\) ausgeführt wird.  
  
## Syntax  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### Parameter  
 `pwszFunctionName`  
 \[in\] Der Name der Funktion, die das Skriptmodul ausgeführt wird.  
  
 `scriptType`  
 \[in\] Der Typ der Funktion.  Beschreibungen von gültigen Werten, finden Sie unter [PROFILER\_SCRIPT\_TYPE\-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.  
  
## Hinweise  
 Für das Skriptmodul DOM\-Aufrufe ruft diese Methode auf, statt, [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md) aufzurufen.  Dies ist aufgrund der großen Anzahl eindeutiger Methoden und Eigenschaften im DOM.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [IActiveScriptProfilerCallback2\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback2-interface.md)