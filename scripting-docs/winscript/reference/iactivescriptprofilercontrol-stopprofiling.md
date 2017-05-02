---
title: "IActiveScriptProfilerControl::StopProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StopProfiling
apilocation: scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerControl::StopProfiling
Beenden, die auf dem Skriptmodul ein Profil erstellen.  Dies gibt Methodenaufrufe [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) auf dem Profilerobjekt und anschließend frei.  
  
## Syntax  
  
```  
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### Parameter  
 `hrShutdownReason`  
 \[in\] Das HRESULT als Parameter, das an die [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)\-Methode des Profilerobjekts übergeben werden soll.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilerstellung ist nicht aktiviert.|  
  
## Siehe auch  
 [IActiveScriptProfilerControl\-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)