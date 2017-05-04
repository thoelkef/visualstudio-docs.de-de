---
title: "IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::CompleteProfilerStart"
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::CompleteProfilerStart
Benachrichtigt den Profiler, dass Sie die Profilerstellung auf alle gültigen Skriptmodulen gestartet haben.  Mit dieser Methode wird, erhalten Sie die vollständige Aufrufliste, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie die Profilerstellung starten.  
  
## Syntax  
  
```  
HRESULT CompleteProfilerStart();  
```  
  
#### Parameter  
 Die Methode enthält keine Parameter.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Profilerstellung kann nicht gestartet werden.|  
|`S_FALSE`|Profilerstellung gestartet wurde, als ein Skript nicht ausgeführt wurde.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilerstellung ist nicht aktiviert.  Kein Rückruf ist festgelegt.|  
|`E_OUTOFMEMORY`|Die Aufrufliste kann aufgrund eines Speicherdruck abgerufen werden.|  
  
## Hinweise  
 Das Aufrufen von `IActiveScriptProfilerControl2::CompleteProfilerStart` wird sichergestellt, dass Ereignisse für Funktionen bereits in der Aufrufliste gesendet werden.  Diese Methode muss aufgerufen werden, nachdem er beginnt auf jedem Skriptmodul ein Profil erstellt hat, das auf der aktuellen Registerkarte ist.  Die Methode kann für jedes Skriptmodul aufgerufen werden.  
  
## Siehe auch  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [IActiveScriptProfilerControl2\-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)