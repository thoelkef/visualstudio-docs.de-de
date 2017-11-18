---
title: PROFILER_EVENT_MASK-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: PROFILER_EVENT_MASK
apilocation: scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68547fcb1fd2cd34b18a3d204baefd24d9da936b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="profilereventmask-enumeration"></a>PROFILER_EVENT_MASK-Enumeration
Gibt die Typen von Ereignissen an, für die ein Profil erstellt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Profile-Funktionen, die in der vom Benutzer erstellter Skripts und dynamischen Code definiert sind.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Profile systemeigener Funktionen, die vom Skriptmodul definiert sind.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Erstellt ein Profil alle benutzerdefinierten und scripting Datenbankmodul-Funktionen ohne Aufrufe in das Document Objekt Model (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Profile-Funktionen, die in das DOM aufrufen|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Alle Funktionen, darunter auch Aufrufe in das DOM-Profile|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script Profiler-Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)