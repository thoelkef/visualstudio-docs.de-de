---
title: PROFILER_SCRIPT_TYPE-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PROFILER_SCRIPT_TYPE
apilocation:
- scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca90a566db422d75fefc44267ffe10504bb872ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816784"
---
# <a name="profilerscripttype-enumeration"></a>PROFILER_SCRIPT_TYPE-Enumeration
Legt den Typ des Skripts fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|PROFILER_SCRIPT_TYPE_USER|Gibt die benutzerspezifischen Skriptcode an.|  
|PROFILER_SCRIPT_TYPE_DYNAMIC|Gibt die Skriptcode, der während der Ausführung dynamisch generiert wird.|  
|PROFILER_SCRIPT_TYPE_NATIVE|Gibt den Skripttyp für systemeigene Funktionen und Objekte, die von der Skript-Engine definiert sind.|  
|PROFILER_SCRIPT_TYPE_DOM|Gibt einen Aufruf in die (DOKUMENTOBJEKTMODELL) von Internet Explorer, z. B. einen Aufruf der `document.getElementById` Methode.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script Profiler Konstanten, Enumerationen und Strukturen](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)