---
title: "IActiveScriptProfilerControl2::PrepareProfilerStop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerControl2::PrepareProfilerStop"
ms.assetid: e43a63bc-c44f-44a8-9db4-29062b9e6a16
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl2::PrepareProfilerStop
Benachrichtigt den Profiler, dass Sie auf allen, anwendbaren Skriptmodulen Profilerstellung beendet werden.  Mit dieser Methode wird, erhalten Sie die vollständige Aufrufliste, wenn [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ausgeführt wird, wenn Sie beenden ein Profil zu erstellen.  
  
## Syntax  
  
```  
HRESULT PrepareProfilerStop();  
```  
  
#### Parameter  
 Die Methode enthält keine Parameter.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Profilerstellung konnte nicht gestartet werden.|  
|`S_FALSE`|Profilerstellung beendet wurde, als ein Skript nicht ausgeführt wurde.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilerstellung ist nicht aktiviert.|  
  
## Hinweise  
 Das Aufrufen von `IActiveScriptProfilerControl2::PrepareProfilerStop` wird sichergestellt, dass Ereignisse für Funktionen in der Aufrufliste gesendet werden.  Diese Methode muss aufgerufen werden, bevor Sie beenden, auf jedem Skriptmodul ein Profil zu erstellen, das auf der aktuellen Registerkarte ist.  Die Methode kann für jedes Skriptmodul aufgerufen werden.  
  
## Siehe auch  
 [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)   
 [IActiveScriptProfilerControl2\-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)