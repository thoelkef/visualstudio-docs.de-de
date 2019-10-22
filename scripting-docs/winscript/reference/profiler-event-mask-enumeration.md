---
title: PROFILER_EVENT_MASK-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_EVENT_MASK
apilocation:
- scrobj.dll
ms.assetid: c2168408-f4f6-4600-971d-f15b4edf4ca2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1e1e7f3b604832014cb23245b105756d1126c5b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572285"
---
# <a name="profiler_event_mask-enumeration"></a>PROFILER_EVENT_MASK-Enumeration
Gibt die Typen von Ereignissen an, für die ein Profil erstellt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
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
|PROFILER_EVENT_MASK_TRACE_SCRIPT_FUNCTION_CALL|Profil Funktionen, die im Benutzer geschriebenen Skript und im dynamischen Code definiert sind.|  
|PROFILER_EVENT_MASK_TRACE_NATIVE_FUNCTION_CALL|Profile Native Funktionen, die von der Skript-Engine definiert werden.|  
|PROFILER_EVENT_MASK_TRACE_ALL|Dient zum Erstellen von Profilen für alle benutzerdefinierten Funktionen und Skript-Engine-Funktionen ohne Aufrufe der Dokumentobjektmodell (DOM).|  
|PROFILER_EVENT_MASK_TRACE_DOM_FUNCTION_CALL|Profile Funktionen, die das DOM aufzurufen.|  
|PROFILER_EVENT_MASK_TRACE_ALL_WITH_DOM|Profile für alle Funktionen, einschließlich Aufrufe im Dom.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script Profiler-Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)    
 [Iactivescriptprofilercontrol:: setprofilereventmask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md) -   
 [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)