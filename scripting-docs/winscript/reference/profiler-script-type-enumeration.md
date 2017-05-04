---
title: "PROFILER_SCRIPT_TYPE-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# PROFILER_SCRIPT_TYPE-Enumeration
Gibt den Typ des Skripts an.  
  
## Syntax  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## Mitglieder  
  
|Member|Description|  
|------------|-----------------|  
|PROFILER\_SCRIPT\_TYPE\_USER|Gibt vom Benutzer erstellten Skriptcode an.|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|Gibt Skriptcode an, der dynamisch während der Ausführung generiert wird.|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|Gibt den Skripttyp für systemeigene Funktionen und Objekte, die durch das Skriptmodul definiert werden.|  
|PROFILER\_SCRIPT\_TYPE\_DOM|Gibt einen Aufruf in das Dokumentobjektmodell \(DOM\) von Internet Explorer beispielsweise ein Aufruf der Methode `document.getElementById` an.|  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für die Active Script\-Profilerstellung](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)