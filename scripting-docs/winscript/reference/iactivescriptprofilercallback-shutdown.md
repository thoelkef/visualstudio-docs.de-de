---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
Wird aufgerufen, um das Profilerobjekt, wenn die Profilerstellung zu informieren auf einem Skriptmodul beendet wird.  Auf diese Weise, das Profilerobjekt kann seine Bereinigungsroutinen aufrufen, nach Bedarf.  Diese Methode wird auch durch das Skriptmodul aufgerufen, wenn das Skriptmodul beendet wird oder wenn ein Aufruf [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) fehlschlägt.  
  
## Syntax  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### Parameter  
 `hrReason`  
 \[in\] Der Grund für das Herunterfahren.  Wenn das Skriptmodul beendet wird, wird `S_OK` übergeben.  Wenn der Aufruf [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ein Fehler\-HRESULT zurückgibt, wird das HRESULT übergeben.  Andernfalls wird dieser Wert von [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md) abgerufen.  
  
## Rückgabewert  
 Der Rückgabewert dieser Methode wird durch das Skriptmodul ignoriert.  
  
## Siehe auch  
 [IActiveScriptProfilerCallback\-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)