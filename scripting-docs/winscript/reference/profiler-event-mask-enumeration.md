---
title: "PROFILER_EVENT_MASK-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# PROFILER_EVENT_MASK-Enumeration
Gibt die Typen von Ereignissen an, für die ein Profil erstellt werden soll.  
  
## Syntax  
  
```  
typedef enum {  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL = 0x00000001,  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL = 0x00000002,  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL    = 0x00000004,  
    PROFILER_EVENT_MASK_TRACE_ALL =  
    PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL |  
    PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL,  
    PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM = PROFILER_EVENT_MASK_TRACE_ALL |  
    PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL  
} PROFILER_EVENT_MASK;  
```  
  
## Mitglieder  
  
|Member|Description|  
|------------|-----------------|  
|PROFILER\_EVENT\_MASK\_TRACE\_SCRIPT\_FUNCTION\_CALL|Erstellt ein Profil Funktionen, die im vom Benutzer erstellte Skript und im dynamischen Code definiert sind.|  
|PROFILER\_EVENT\_MASK\_TRACE\_NATIVE\_FUNCTION\_CALL|Erstellt ein Profil systemeigene Funktionen, die durch das Skriptmodul definiert werden.|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL|Erstellt alle benutzerdefinierten und Skriptmodulfunktionen, ausschließlich der Aufrufe im Dokumentobjektmodell ein Profil \(DOM\).|  
|PROFILER\_EVENT\_MASK\_TRACE\_DOM\_FUNCTION\_CALL|Erstellt ein Profil Funktionen, die in das DOM aufrufen.|  
|PROFILER\_EVENT\_MASK\_TRACE\_ALL\_WITH\_DOM|Erstellt alle Funktionen, einschließlich Aufrufe in das DOM ein Profil.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für die Active Script\-Profilerstellung](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)